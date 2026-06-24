# Threat Hunting Machine Learning Algorithms

This page provides a practical reference for using machine learning algorithms in threat hunting. It focuses on hunting use cases, algorithm selection, telemetry requirements, analyst review, limitations, and official implementation references.

Machine learning can support threat hunting by ranking unusual activity, discovering peer-group outliers, clustering related events, detecting changes in behavior, enriching investigations, and reducing search space. It should not replace analyst judgment, detection engineering, incident response, or cyber attribution discipline.

## Purpose

Machine learning assisted threat hunting should help analysts answer questions such as:

1. Which users, hosts, identities, applications, or cloud resources behave differently from their peer group?
2. Which process, command-line, DNS, authentication, proxy, or API activity is rare but security-relevant?
3. Which events form unusual clusters that may indicate tooling, staging, lateral movement, persistence, command and control, or exfiltration?
4. Which alert or hunt results should be reviewed first?
5. Which historical activity should be retro-hunted after new intelligence appears?

## Core Principle

Machine learning output is an investigative lead, not a finding by itself. A model score, anomaly flag, cluster assignment, or prediction should be validated with raw telemetry, context, false-positive analysis, MITRE ATT&CK mapping, and alternative explanations.

## Algorithm Selection Table

| Algorithm or family | Learning type | Description | Hunting use case | Typical telemetry and features | Main risk | Official reference |
| --- | --- | --- | --- | --- | --- | --- |
| Isolation Forest | Unsupervised anomaly detection | Randomly partitions data and isolates unusual observations more quickly than normal observations | Rare user behavior, unusual cloud API use, abnormal DNS volume, unusual process execution | Counts, rates, unique destinations, entropy, time-of-day, peer-group features | Sensitive to feature design and contamination assumptions | scikit-learn IsolationForest documentation: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html |
| One-Class SVM | Novelty detection and outlier detection | Learns a boundary around expected behavior and flags observations outside that boundary | Detect activity outside a known clean baseline, such as unusual admin behavior or rare service account behavior | Normal baseline features, user or host profiles, normalized event vectors | Sensitive to scaling, kernel choice, and outliers in training data | scikit-learn OneClassSVM documentation: https://scikit-learn.org/stable/modules/generated/sklearn.svm.OneClassSVM.html |
| Local Outlier Factor | Density-based outlier detection | Compares local density of an observation with the density of nearby observations | Detect peer-group outliers such as a workstation acting like a server or a user authenticating unlike similar users | Peer-group features, neighborhood-based behavior, volume and diversity metrics | Less suitable for direct prediction on new data unless configured for novelty use | scikit-learn LocalOutlierFactor documentation: https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.LocalOutlierFactor.html |
| DBSCAN | Density-based clustering | Groups dense regions and marks sparse points as noise | Find unusual clusters of network connections, login sources, process trees, or command-line families | Numeric or embedded vectors, distance metrics, session features | Parameter selection can strongly affect clusters and noise | scikit-learn DBSCAN documentation: https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html |
| OPTICS | Density-based clustering | Similar to DBSCAN but better for variable-density data | Hunt uneven clusters in DNS, proxy, endpoint, or identity telemetry | Distance-based feature vectors and embeddings | Interpretation requires care and analyst review | scikit-learn clustering documentation: https://scikit-learn.org/stable/modules/clustering.html |
| K-Means and MiniBatchKMeans | Clustering | Partitions observations into a selected number of clusters | Build peer groups, cluster command lines, group endpoints, find rare clusters | Scaled numeric features, embeddings, categorical encodings | Requires choosing number of clusters and can hide rare activity inside large clusters | scikit-learn clustering documentation: https://scikit-learn.org/stable/modules/clustering.html |
| Gaussian Mixture Models | Probabilistic clustering and anomaly scoring | Represents data as a mixture of probability distributions | Rank observations with low likelihood under expected behavior | Continuous features, normalized behavior vectors | Assumes data can be reasonably represented by mixture distributions | scikit-learn Gaussian mixture documentation: https://scikit-learn.org/stable/modules/mixture.html |
| PCA and TruncatedSVD | Dimensionality reduction | Projects high-dimensional data into lower-dimensional components | Detect reconstruction error, compress sparse events, visualize behavior, reduce noisy features | Process vectors, command-line vectors, DNS features, sparse matrices | Components may be difficult to explain operationally | scikit-learn decomposition documentation: https://scikit-learn.org/stable/modules/decomposition.html |
| Random Forest | Supervised classification or ranking | Ensemble of decision trees trained on labeled examples | Rank alerts, classify suspicious events, triage known malicious versus benign patterns | Labeled alerts, case outcomes, enriched features, ATT&CK tags | Requires reliable labels and may learn past analyst bias | scikit-learn RandomForestClassifier documentation: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html |
| Gradient Boosting | Supervised classification or ranking | Sequentially builds models to correct earlier errors | Alert prioritization, malware triage, phishing triage, suspicious authentication scoring | Labeled examples, engineered features, entity context | Can overfit and may be hard to explain without model inspection | scikit-learn GradientBoostingClassifier documentation: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html |
| Logistic Regression | Supervised baseline classifier | Linear model useful for interpretable classification | Explainable triage model for known hunt hypotheses | Labeled events, normalized numeric features, sparse vectors | Linear decision boundary may miss complex behavior | scikit-learn LogisticRegression documentation: https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html |
| TF-IDF and text vectorization | Feature extraction | Converts text into numeric vectors based on token frequency and rarity | Cluster command lines, URLs, registry paths, script blocks, email subjects, or user agents | Command lines, PowerShell, URLs, DNS labels, file paths, script text | Tokenization and normalization mistakes can dominate results | scikit-learn text feature extraction documentation: https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction |
| Cosine similarity and nearest neighbors | Similarity search | Measures similarity between vectors | Find commands, scripts, URLs, domains, or alerts similar to a known malicious seed | Text vectors, embeddings, normalized event vectors | Similarity does not prove maliciousness or common actor identity | scikit-learn nearest neighbors documentation: https://scikit-learn.org/stable/modules/neighbors.html |
| Graph algorithms | Graph analytics and network science | Models relationships among users, hosts, IPs, processes, domains, files, and cloud resources | Find unusual paths, central nodes, communities, lateral movement paths, infrastructure clusters | Entity graphs, authentication graphs, process trees, DNS graphs, cloud access graphs | Graph structure can reflect logging coverage rather than adversary behavior | NetworkX algorithms documentation: https://networkx.org/documentation/stable/reference/algorithms/index.html |

## Threat Hunting Use Cases

| Use case | Recommended algorithm families | Example hunting question | Analyst validation |
| --- | --- | --- | --- |
| Rare authentication behavior | Isolation Forest, One-Class SVM, LOF, peer grouping | Which user logged in from a rare ASN, country, device, or hour compared with their baseline? | Review MFA result, device trust, VPN, travel, role, and business context |
| Service account misuse | Isolation Forest, One-Class SVM, time-window baselines | Did a service account access unusual systems, APIs, or data classes? | Validate approved automation, owner, credential rotation, source host, and token use |
| Suspicious process execution | TF-IDF, clustering, Random Forest, Gradient Boosting | Which command lines are rare or similar to known malicious commands? | Review parent-child process chain, signer, hash, user, host role, script content, and ATT&CK mapping |
| DNS or proxy anomaly | Isolation Forest, DBSCAN, K-Means, entropy features | Which domains show rare volume, high entropy, rare TLDs, beaconing, or unusual user-agent behavior? | Check passive DNS, threat intel, proxy logs, TLS metadata, domain age, and destination reputation |
| Lateral movement hunting | Graph algorithms, clustering, LOF | Which user-host relationships or remote login paths are unusual? | Review admin activity, remote service use, session timing, source host risk, and ticket context |
| Cloud control-plane abuse | Isolation Forest, One-Class SVM, supervised ranking | Which identity called unusual APIs, changed permissions, or accessed rare regions? | Review IAM policy change, role assumption, MFA context, source IP, session tags, and resource sensitivity |
| Exfiltration staging | Isolation Forest, time-window features, clustering | Which host compressed, staged, or transferred unusual data volume? | Review file paths, process tree, network destination, business workflow, and DLP context |
| AI workflow compromise | IoPC features, anomaly detection, graph analysis | Which prompt, retrieved context, tool call, or connector action deviates from normal workflow? | Review prompt logs, tool authorization, retrieved document, output, user approval, and data access |
| Alert triage ranking | Random Forest, Gradient Boosting, Logistic Regression | Which alerts should analysts review first? | Calibrate model with case outcomes, tune thresholds, and review explainability |
| Retro-hunting after new intelligence | Similarity search, YARA/feature matching, clustering | Did this behavior or artifact appear before the current incident? | Define lookback, retention, data coverage, false positives, and first-seen time |

## Feature Engineering for Threat Hunting

| Feature category | Examples | Hunting value |
| --- | --- | --- |
| Frequency and volume | Login count, DNS query count, API call count, process count | Detect unusual bursts, rare usage, and deviation from baseline |
| Diversity | Unique destinations, unique commands, unique countries, unique resources | Find expansion, discovery, broad access, and abnormal reach |
| Rarity | Rare parent process, rare domain, rare command token, rare cloud action | Surface low-frequency but meaningful behavior |
| Time behavior | Hour of day, day of week, time since last seen, session duration | Identify off-hours activity and behavior drift |
| Peer-group deviation | Compare user to department, host to role, identity to application | Distinguish unusual activity from role-specific behavior |
| Sequence and order | Process chain, authentication sequence, API call sequence | Support TTP-oriented hunting and ATT&CK mapping |
| Text tokens | Command-line tokens, URL path tokens, script functions, user-agent strings | Support clustering, similarity search, and rare token detection |
| Graph structure | Degree, centrality, community, path length, new edges | Support lateral movement, infrastructure clustering, and identity relationship hunting |
| Risk enrichment | Asset criticality, vulnerability exposure, privilege, external exposure | Prioritize results by impact and business context |

## Operational Workflow

| Step | Activity | Output |
| ---: | --- | --- |
| 1 | Define the hunt hypothesis | Example: service accounts should not perform interactive logins from unmanaged hosts |
| 2 | Select telemetry sources | Endpoint, identity, DNS, proxy, cloud, email, AI workflow, EDR, SIEM, data lake |
| 3 | Engineer features | Entity windows, peer groups, rarity, sequence, text, graph, enrichment |
| 4 | Select algorithm | Match algorithm to data shape, label availability, and hunting question |
| 5 | Train or fit model | Use clean baseline where possible, avoid known incident periods unless supervised labels are intended |
| 6 | Score and rank | Produce anomaly scores, cluster IDs, predicted classes, or similarity rankings |
| 7 | Review with analyst context | Validate raw events, false positives, business logic, and ATT&CK mapping |
| 8 | Convert useful results into detection logic | Sigma, SIEM query, YARA-L, EDR rule, cloud detection, case playbook, or retro-hunt query |
| 9 | Monitor quality | Precision, recall where labeled, analyst acceptance, false-positive rate, drift, and coverage |
| 10 | Govern model lifecycle | Owner, version, features, training window, test results, review date, retirement criteria |

## Algorithm Selection Guidance

1. Use **Isolation Forest** when labels are limited and the goal is to rank unusual behavior across many numeric features.
2. Use **One-Class SVM** when a relatively clean baseline exists and the goal is novelty detection against that baseline.
3. Use **Local Outlier Factor** when peer-neighborhood behavior matters, such as user-to-peer or host-to-role comparison.
4. Use **DBSCAN, OPTICS, or K-Means** when the goal is grouping similar behavior and reviewing rare or noisy clusters.
5. Use **PCA or TruncatedSVD** when the data is high-dimensional and sparse, such as command-line, URL, DNS, or event-token vectors.
6. Use **Random Forest, Gradient Boosting, or Logistic Regression** when there are reliable labels from confirmed cases, analyst decisions, or validated detection outcomes.
7. Use **TF-IDF, cosine similarity, and nearest neighbors** for command-line, URL, file path, email, script, and user-agent hunting.
8. Use **graph algorithms** when relationships are the core evidence, such as user-to-host, process-to-child-process, domain-to-IP, or identity-to-cloud-resource graphs.

## Mapping to MITRE ATT&CK

Machine learning hunting outputs should be mapped to ATT&CK only after analyst validation. A cluster, score, or anomaly does not automatically equal an ATT&CK technique. Use ATT&CK mapping to document the behavior being investigated, not to claim attribution.

| Hunting pattern | Possible ATT&CK-aligned behavior to investigate |
| --- | --- |
| Rare process parent-child chain | Execution, defense evasion, persistence |
| Unusual remote login graph edge | Lateral movement, credential access |
| Rare cloud API action by identity | Privilege escalation, defense evasion, discovery |
| High-entropy DNS or beaconing pattern | Command and control |
| Unusual archive or compression behavior | Collection or exfiltration preparation |
| Prompt or tool-call anomaly | AI workflow compromise, unauthorized tool use, context manipulation |

Official ATT&CK reference: https://attack.mitre.org/

## Validation Metrics and Analyst Measures

| Measure | Use | Caveat |
| --- | --- | --- |
| Precision | How many reviewed results were useful or suspicious | Requires analyst labels or confirmed outcomes |
| Recall | How many known malicious events were found | Requires ground truth, often unavailable in hunting |
| False positive rate | How much benign activity is surfaced | Depends on thresholds and entity context |
| Time to triage | Analyst effort per result | Can improve even when model accuracy is imperfect |
| First-seen time | Earliest historical appearance of behavior | Limited by retention and telemetry coverage |
| Peer-group explainability | Whether analysts understand why an entity is unusual | Poor features reduce trust |
| Drift monitoring | Whether baseline behavior changed | Business changes can look like attacks |

## Common Failure Modes

| Failure mode | Why it matters | Mitigation |
| --- | --- | --- |
| Weak feature engineering | Good algorithms cannot rescue poor telemetry representation | Build features around entities, time windows, peer groups, and security semantics |
| Training on compromised data | The model may learn malicious behavior as normal | Exclude known incident windows and high-risk periods where possible |
| Alert-label bias | Supervised models may learn analyst habits rather than malicious behavior | Use confirmed outcomes, multiple reviewers, and periodic relabeling |
| Ignoring base rates | Rare does not always mean malicious | Add business context, asset role, and allow-list review |
| Poor thresholding | Too many or too few results | Tune thresholds by analyst capacity and hunt objective |
| No explainability | Analysts may not trust the model or may miss the reason for the score | Store top contributing features, nearest neighbors, and raw event links |
| Overclaiming attribution | ML clusters may be treated as actor identity | Separate cluster, campaign, tool, TTP, and attribution claims |
| Model drift | Behavior changes over time | Monitor drift, retrain, and compare to previous baselines |
| Privacy and governance gaps | ML hunting may process sensitive user behavior | Apply minimization, access control, retention rules, and audit logging |

## Recommended Page Template for a Machine Learning Hunt

| Field | Description |
| --- | --- |
| Hunt name | Short descriptive name |
| Hypothesis | What suspicious behavior is being tested |
| ATT&CK mapping | Technique or tactic being investigated, if validated |
| Data sources | SIEM tables, EDR logs, identity logs, DNS, proxy, cloud, AI workflow logs |
| Entity | User, host, process, identity, domain, IP, resource, prompt, or tool call |
| Time window | Training period, scoring period, lookback period |
| Features | List of engineered features used |
| Algorithm | Model family and implementation reference |
| Threshold or ranking method | Top N, score threshold, peer-group threshold, cluster rarity |
| Analyst review steps | Raw events, context, false-positive checks, escalation logic |
| Output | Case, detection rule, retro-hunt query, dashboard, or risk score |
| Caveats | Data gaps, assumptions, known blind spots |
| Owner and review date | Governance and lifecycle management |

## References

MITRE. (n.d.). *MITRE ATT&CK*. Retrieved June 25, 2026, from https://attack.mitre.org/

NetworkX Developers. (n.d.). *Algorithms*. NetworkX documentation. Retrieved June 25, 2026, from https://networkx.org/documentation/stable/reference/algorithms/index.html

Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., & Duchesnay, E. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research, 12*, 2825-2830. https://jmlr.org/papers/v12/pedregosa11a.html

scikit-learn developers. (n.d.). *Clustering*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/clustering.html

scikit-learn developers. (n.d.). *Decomposing signals in components*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/decomposition.html

scikit-learn developers. (n.d.). *Feature extraction: Text feature extraction*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction

scikit-learn developers. (n.d.). *Gaussian mixture models*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/mixture.html

scikit-learn developers. (n.d.). *IsolationForest*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html

scikit-learn developers. (n.d.). *LocalOutlierFactor*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.LocalOutlierFactor.html

scikit-learn developers. (n.d.). *Nearest Neighbors*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/neighbors.html

scikit-learn developers. (n.d.). *Novelty and outlier detection*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/outlier_detection.html

scikit-learn developers. (n.d.). *OneClassSVM*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/generated/sklearn.svm.OneClassSVM.html

scikit-learn developers. (n.d.). *RandomForestClassifier*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html

scikit-learn developers. (n.d.). *GradientBoostingClassifier*. scikit-learn documentation. Retrieved June 25, 2026, from https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html
