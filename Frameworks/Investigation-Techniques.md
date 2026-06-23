# Structured Analytic Techniques (SATs) for Cyber Attribution Investigation

This page provides a practical set of Structured Analytic Techniques (SATs) that can be used during cyber attribution investigations, including LLM assisted investigations. The goal is to improve reasoning discipline, expose uncertainty, test alternative explanations, and prevent premature attribution.

These techniques support analysis. They do not replace forensic validation, source reliability assessment, legal review, or intelligence oversight.

## Analytic Purpose

SATs are explicit, repeatable methods used to improve the quality, transparency, and auditability of analytic reasoning. In cyber attribution, they help analysts separate evidence from inference, identify hidden assumptions, compare competing explanations, challenge premature judgments, and calibrate confidence levels.

They are especially useful because technical indicators can be reused, infrastructure can be shared or compromised, contractor and proxy relationships may obscure control, and adversaries may deliberately plant deceptive artifacts. SATs therefore help analysts distinguish between actor cluster, operator, sponsor, control, intent, and confidence.

## Collection and Analysis Context

SATs are most effective when analysts understand their collection sources on a technical level and can determine which intelligence requirements each source can satisfy. A collection management framework (CMF) can help organize internal and external data sources, identify what each source contains, and document how the data is processed, enriched, and exploited.

Analysts should continuously look for human fingerprints that indicate adversary choices, such as naming habits, operational routines, language artifacts, build patterns, passwords, actor handles, certificate reuse, registration behavior, and infrastructure management practices.

### Collection Sources to Consider

| Source | Examples | Attribution value |
|---|---|---|
| Malware | Hashes, header metadata, PDB strings, mutexes, import hashes, compiler artifacts, embedded paths | May reveal developer habits, tool lineage, build environment, reused code, actor handles, passwords, or internal IDs |
| Network infrastructure | Actor registered domains, compromised sites, dynamic DNS use, IP address relationships, ASNs, passive DNS, domain age patterns, hosting changes | Helps map infrastructure continuity, reuse, staging behavior, operational security practices, and possible shared infrastructure |
| TLS certificates | Certificate hashes, issuer details, validity dates, certificate reuse across infrastructure, TLS fingerprints | Can link infrastructure clusters and reveal repeated operational patterns |
| Endpoint and host artifacts | Process creation, script execution, registry or filesystem changes, credential misuse, persistence mechanisms, EDR logged behaviors | Helps align observed activity with adversary TTPs and distinguishes hands on keyboard behavior from automated or commodity activity |

### Intelligence Life Cycle Placement

| Stage | Role in cyber attribution |
|---|---|
| Planning and direction | Define attribution questions, intelligence requirements, scope, confidence thresholds, and legal or policy constraints |
| Collection | Acquire relevant technical, contextual, operational, and external reporting sources |
| Processing and exploitation | Normalize, enrich, deconflict, evaluate, and prepare data for analysis |
| Analysis and production | Apply SATs, evaluate competing explanations, assess confidence, and produce findings |
| Dissemination | Deliver the assessment with confidence language, caveats, evidence gaps, and decision relevance |

## Confidence Language and Source Evaluation

Structured analysis should be paired with explicit confidence language and source evaluation. In cyber attribution, this prevents analysts from mixing four different questions: what the evidence says, how reliable the source is, how likely the analytic judgment is, and how much confidence analysts have in the assessment.

### FIRST/NATO Words of Estimative Probability (WEP)

Words of Estimative Probability (WEP) standardize likelihood language. They help reduce ambiguity in terms such as likely, possible, and almost certain. Use WEP for the likelihood of an event, outcome, or analytic judgment.

The FIRST CTI SIG recommends the NATO WEP terms below for CTI reporting.

| FIRST/NATO WEP term | Probability relationship | Use in cyber attribution |
|---|---:|---|
| Highly unlikely | Less than 10% | Strong evidence points away from the judgment |
| Unlikely | 10% to 40% | Evidence tends to contradict the judgment, but uncertainty remains |
| Even chance | 40% to 60% | Evidence does not clearly favor one hypothesis over another |
| Likely | 60% to 90% | Evidence supports the judgment more than alternatives |
| Highly likely | Greater than 90% | Evidence strongly supports the judgment and alternatives are weak |

The percentages express the relationship among terms rather than precise mathematical probability. For machine interpretation, FIRST notes that the upper boundary of unlikely can include 40%, and the lower boundary of likely can include 60%.

### FIRST Levels of Confidence in Assessment (LCA)

Levels of Confidence in Assessment (LCA) communicate how much confidence analysts have in a judgment, based on the quality, correlation, and reliability of the underlying evidence. LCA should be kept separate from WEP. WEP communicates likelihood. LCA communicates confidence in the assessment.

The FIRST CTI SIG recommends the NATO LCA terms below.

| FIRST/NATO LCA term | Meaning | Use in cyber attribution |
|---|---|---|
| High confidence | Good quality information, evidence from multiple collection capabilities, and a clear judgment can be made | Use when evidence is strong, corroborated, and alternatives have been tested |
| Moderate confidence | Evidence is open to several interpretations, or is credible and plausible but lacks correlation | Use when the judgment is supported but important gaps, ambiguity, or limited corroboration remain |
| Low confidence | Fragmentary information, or information from collection capabilities of dubious reliability | Use when the judgment is tentative and should not drive high consequence action without further collection |

#### FIRST Reporting Pattern

| Reporting option | When to use | Example wording |
|---|---|---|
| WEP and LCA | Use when both likelihood and confidence are important | It is likely that Actor X conducted the activity. We have moderate confidence in this conclusion. |
| WEP only | Use when probability is the main uncertainty to communicate | It is likely that Actor X conducted the activity. |
| LCA only | Use when the main issue is the quality of information and how sure the analyst is | We assess with moderate confidence that Actor X conducted the activity. |

Avoid placing WEP and LCA in the same sentence because it can confuse likelihood with confidence. A judgment can be likely but low confidence if the evidence is thin, poorly sourced, or not independently corroborated.

### Admiralty Code / NATO System

The Admiralty Code, also known as the NATO System, uses a two character rating to evaluate collected information. The letter grades source reliability. The number grades information credibility. For example, B2 means a usually reliable source reporting information that is probably true.

#### Source Reliability

| Code | Meaning | Practical interpretation |
|---|---|---|
| A | Completely reliable | No doubt about authenticity, trustworthiness, or competence |
| B | Usually reliable | Minor doubt, but a strong record of valid reporting |
| C | Fairly reliable | Some doubt, but has provided valid reporting in the past |
| D | Not usually reliable | Significant doubt, although some prior reporting may have been valid |
| E | Unreliable | Lacks authenticity, trustworthiness, or competence |
| F | Reliability cannot be judged | Insufficient basis to evaluate the source |

#### Information Credibility

| Code | Meaning | Practical interpretation |
|---|---|---|
| 1 | Confirmed | Confirmed by independent sources and consistent with other information |
| 2 | Probably true | Logical and consistent, but not independently confirmed |
| 3 | Possibly true | Reasonably logical and agrees with some other information |
| 4 | Doubtful | Possible, but not logical or not supported by other information |
| 5 | Improbable | Contradicted by other information or not logical |
| 6 | Truth cannot be judged | Insufficient basis to evaluate the information |

### How to Use WEP, LCA, and Admiralty/NATO Ratings

| Analytic need | Use WEP | Use FIRST/NATO LCA | Use Admiralty Code / NATO System |
|---|---|---|---|
| Source evaluation | No | No | Yes, to grade source reliability and information credibility |
| Evidence register | Optional | Optional, if the item affects overall confidence | Yes, especially for external reporting and human sourced claims |
| ACH matrix | Yes, for final hypothesis likelihood | Yes, for confidence in the surviving hypothesis | Yes, for evidence quality and diagnostic weight |
| Key Assumptions Check | Yes, for assumption likelihood | Yes, for confidence in each key assumption | Yes, for assumptions based on specific reports |
| Finished assessment | Yes, to communicate likelihood | Yes, to communicate confidence in the assessment | Yes, when documenting source and information quality |

### Example Evidence Register

| Evidence item | Source | Admiralty/NATO rating | Relevance | WEP impact | LCA impact |
|---|---|---:|---|---|---|
| Joint advisory links activity to an actor cluster | Government advisory | B2 | Supports actor cluster association | Increases likelihood of state linked activity | Supports moderate to high confidence if corroborated |
| Reused TLS certificate connects two domains | Passive DNS and certificate telemetry | A2 | Supports infrastructure clustering | Increases likelihood of shared operational infrastructure | Supports confidence in the cluster, not necessarily in sponsor identity |
| PDB string contains a language marker | Malware sample | A3 | Supports developer environment inference | Weakly increases likelihood, but does not prove nationality | Low confidence for nationality or sponsor inference |
| Vendor blog attributes campaign directly to a state service | External CTI report | C3 | Supports a hypothesis, but requires corroboration | Should not independently drive high likelihood | Should not independently drive high confidence |

## Summary

| No. | Technique or standard | Main question | Attribution value | Typical output |
|---:|---|---|---|---|
| 1 | Clustering | Which data points appear related, and why? | Groups related activity while separating signal from noise | Cluster map, feature list, and candidate activity groupings |
| 2 | Key Assumptions Check | What must be true for the current assessment to hold? | Surfaces hidden assumptions and fragile reasoning | Assumption register and collection gaps |
| 3 | Analysis of Competing Hypotheses (ACH) | Which hypothesis is least inconsistent with the evidence? | Tests multiple plausible explanations side by side | ACH matrix and surviving hypotheses |
| 4 | Devil's Advocacy | What is the strongest case against the current judgment? | Challenges confirmation bias and weak evidence | Challenge memo and evidence gap list |
| 5 | Pre-Mortem Analysis | How could this attribution judgment later prove wrong? | Identifies failure modes before publication or escalation | Failure scenarios and mitigation actions |
| 6 | WEP, LCA, and Admiralty/NATO ratings | How should likelihood, confidence, source reliability, and information credibility be expressed? | Prevents unclear confidence language and source laundering | Probability wording, confidence level, and evidence grading |

## Where the Techniques Fit in an Attribution Workflow

1. Define the incident, scope, victimology, and operational timeline.
2. Separate observations from inferences and externally sourced reporting.
3. Grade source reliability and information credibility using the Admiralty Code / NATO System where appropriate.
4. Organize collection sources through a CMF and identify which sources satisfy which intelligence requirements.
5. Use clustering to group related data points and identify candidate activity groupings.
6. Build candidate attribution hypotheses.
7. Run Key Assumptions Check, ACH, Devil's Advocacy, and Pre-Mortem as analysis or peer review gates.
8. Use WEP for likelihood and FIRST/NATO LCA for analytic confidence.
9. Document what is known, what is inferred, what remains uncertain, and why.

## 1. Clustering

### Purpose

Clustering groups related data points based on shared characteristics in order to reveal patterns that may not be visible when examining items individually. It is especially useful for large or fragmented datasets, where analysts need to identify activity groupings, distinguish noise from signal, and develop hypotheses.

### Inputs

| Input | Description |
|---|---|
| Technical indicators | Malware hashes, infrastructure, TLS certificates, domains, IPs, tools, scripts, and endpoint artifacts |
| Behavioral indicators | TTPs, timing, targeting logic, operational tempo, and hands on keyboard behavior |
| Contextual indicators | Victimology, geopolitical timing, known campaign history, and external reporting |
| Source notes | Source origin, reliability, freshness, and collection limitations |

### Method

1. Define the dataset and the purpose of clustering.
2. Select clustering features, such as infrastructure reuse, malware artifacts, timing, victimology, TLS reuse, or TTP overlap.
3. Separate high confidence links from weak or contextual similarities.
4. Identify clusters, outliers, and ambiguous data points.
5. Test whether the cluster represents one actor, one campaign, shared tooling, shared infrastructure, or coincidental overlap.
6. Convert unresolved links into collection requirements.

### Template

| Data point | Shared feature | Related to | Link strength | Alternative explanation | Follow up action |
|---|---|---|---|---|---|
| Domain A | Same TLS certificate as Domain B | Infrastructure cluster 1 | Medium | Certificate reuse by shared hosting provider | Validate hosting history and certificate issuance context |
| Malware sample X | Similar PDB path to sample Y | Tooling cluster 1 | High | Shared builder or leaked code | Compare compile times, code lineage, and operational context |

### Output

The output is a cluster map or feature table that explains why data points were grouped, how strong each link is, and which alternative explanations remain plausible.

## 2. Key Assumptions Check

### Purpose

A Key Assumptions Check identifies the assumptions that must be true for an attribution judgment to remain valid. It should be used when analysts are making critical judgments under uncertainty or complexity. It helps ensure the analysis is grounded, exposes potential bias, and tests whether assumptions remain valid as new information emerges.

### Inputs

| Input | Description |
|---|---|
| Initial judgment | The current attribution statement and confidence level |
| Evidence list | Technical indicators, TTPs, infrastructure, malware, timing, victimology, and reporting |
| Context | Geopolitical timing, campaign history, targeting logic, and known actor behavior |
| Source notes | Origin, reliability, corroboration, and limitations of each source |

### Method

1. State the current judgment in one sentence.
2. List every assumption required for that judgment to be true.
3. Mark each assumption as evidence supported, inferred, contextual, or uncertain.
4. Rate each assumption by criticality and confidence.
5. Identify assumptions that would materially change the attribution if proven false.
6. Convert weak assumptions into collection tasks.

### Template

| Assumption | Type | Criticality | Confidence | What could disprove it? | Follow up action |
|---|---|---|---|---|---|
| The observed infrastructure is controlled by the assessed actor | Inferred | High | Evidence that the infrastructure was reused, leased, compromised, or shared | Validate infrastructure history and ownership changes |
| Malware similarity reflects actor continuity rather than tool reuse | Inferred | High | Evidence that the tool is public, leaked, sold, or used by multiple actors | Compare code, build artifacts, and operational context |

### Output

The output is an assumption register that tells the analyst which parts of the assessment are solid, which are fragile, and which require additional collection.

## 3. Analysis of Competing Hypotheses (ACH)

### Purpose

ACH should be used when analysts need to evaluate multiple plausible explanations or outcomes for a complex problem where evidence may support or refute different possibilities. It is particularly useful for reducing cognitive bias, enforcing a systematic approach, and identifying which hypothesis is least inconsistent with the available evidence.

Diagnostic evidence should receive more weight than evidence that fits many hypotheses.

### Example Hypotheses

| Hypothesis | Description |
|---|---|
| H1 | A state intelligence service conducted the operation directly |
| H2 | A contractor or proxy conducted the operation on behalf of a state |
| H3 | A criminal actor reused tools, infrastructure, or tradecraft associated with the state actor |
| H4 | The operation was designed as a false flag or deception effort |

### Seven Steps of ACH

| Step | Action | Purpose |
|---:|---|---|
| 1 | Hypotheses | Define mutually distinguishable hypotheses |
| 2 | Evidence | List evidence and assumptions separately |
| 3 | Diagnostics | Assess whether each item is consistent, inconsistent, neutral, or unknown for each hypothesis |
| 4 | Refinement | Revise hypotheses and evidence items to remove ambiguity or overlap |
| 5 | Prioritization | Focus on the most diagnostic evidence and the most consequential inconsistencies |
| 6 | Sensitivity | Test whether the conclusion changes if key evidence is removed, downgraded, or reinterpreted |
| 7 | Conclusion and Evaluation | Identify rejected and surviving hypotheses, confidence level, evidence gaps, and collection priorities |

### ACH Matrix Template

Use simple marks consistently:

| Mark | Meaning |
|---|---|
| C | Consistent |
| I | Inconsistent |
| N | Neutral or not diagnostic |
| ? | Unknown or requires collection |

| Evidence item | H1 | H2 | H3 | H4 | Notes |
|---|---:|---:|---:|---:|---|
| Joint advisory links activity to a known actor cluster | C | C | N | ? | Supports cluster association, but not necessarily direct state control |
| Infrastructure previously used by multiple operators | I | C | C | C | Weakens direct control claim |
| Victimology matches strategic state interest | C | C | N | C | Supports motive, but is not independently decisive |

### Output

The output is a short finding that states which hypotheses were rejected, which remain plausible, and what evidence would distinguish between the surviving explanations.

## 4. Devil's Advocacy

### Purpose

Devil's Advocacy deliberately challenges the leading attribution judgment. It is useful before public attribution, legal escalation, sanctions, diplomatic action, or high impact defensive measures.

### Method

1. Assign an analyst or reviewer to argue against the current judgment.
2. Identify the strongest alternative explanation.
3. Challenge source reliability, evidence freshness, clustering logic, and confidence language.
4. Ask whether the evidence proves actor identity, actor control, operational sponsorship, or only technical similarity.
5. Produce a challenge memo with evidence gaps and suggested wording changes.

### Challenge Questions

| Area | Questions |
|---|---|
| Technical evidence | Could malware, infrastructure, tooling, or TTPs have been reused or copied? |
| Source reliability | Is the key evidence independently corroborated? |
| Actor control | Does the evidence show direct control, sponsorship, tolerance, or only association? |
| Deception | Could the operation include false flags, planted artifacts, or misleading infrastructure? |
| Confidence | Is the confidence level stronger than the evidence justifies? |

### Output

The output is a challenge memo that improves the assessment, even if the original judgment remains unchanged. The memo should identify what would make the judgment stronger, weaker, or more precise.

## 5. Pre-Mortem Analysis

### Purpose

A Pre-Mortem asks the team to imagine that the attribution judgment was later proven wrong and then explain why. This helps identify failure modes before the assessment is finalized.

### Method

1. Assume the assessment has failed six months after release.
2. List the most plausible reasons for failure.
3. Identify which failure modes are preventable through additional collection, wording changes, or peer review.
4. Add mitigations before the assessment is used for decision making.

### Failure Mode Template

| Failure mode | How it could happen | Impact on attribution | Mitigation |
|---|---|---|---|
| Shared contractor activity | A contractor served several state or non state clients | Direct state attribution becomes overstated | Distinguish actor cluster from sponsor and control |
| Tool reuse | A second actor reused malware, scripts, or infrastructure | Technical similarity becomes less diagnostic | Require corroborating evidence beyond tool overlap |
| False flag | The actor planted misleading artifacts | Attribution points toward the wrong sponsor | Test deception indicators and require independent corroboration |
| Vendor over clustering | Separate campaigns were merged into one actor cluster | Actor continuity is overstated | Review cluster criteria and confidence thresholds |

### Output

The output is a list of failure scenarios, mitigation actions, and recommended changes to confidence language.

## LLM Supported Use

LLMs can help structure analysis, generate alternative hypotheses, and stress test reasoning. They should not be treated as evidence sources unless their output is grounded in verifiable material supplied by the analyst.

### Example Prompts

| Technique | Prompt |
|---|---|
| Clustering | Group the following indicators by shared features. Explain link strength, alternative explanations, and which items should remain unclustered. |
| Key Assumptions Check | List the assumptions required for this attribution judgment to be true. Separate evidence supported assumptions from inferred assumptions. |
| ACH | Build an ACH matrix for the following hypotheses and evidence items. Identify which evidence is diagnostic and which hypotheses remain plausible. |
| Devil's Advocacy | Challenge this attribution assessment. Identify weak evidence, alternative explanations, and overconfident wording. |
| Pre-Mortem | Assume this attribution judgment is proven wrong in six months. List the most likely reasons and propose mitigations. |
| WEP, LCA, and Admiralty/NATO ratings | For each evidence item, separate source reliability, information credibility, WEP likelihood, and FIRST/NATO LCA confidence. |

### LLM Guardrails

| Risk | Control |
|---|---|
| Fabricated evidence | Use only analyst supplied evidence or cited sources |
| Overconfident wording | Require confidence language and uncertainty notes |
| Source laundering | Preserve source origin, date, and reliability notes |
| Hidden assumptions | Ask the model to list assumptions before conclusions |
| Confirmation bias | Require at least two plausible alternative hypotheses |
| Over clustering | Require alternative explanations for each link before accepting a cluster |
| Conflating likelihood with confidence | Require separate fields for WEP likelihood and FIRST/NATO LCA confidence |
| Conflating reliability with confidence | Require separate fields for source reliability, information credibility, likelihood, and analytic confidence |

## Example Confidence Adjustment

| Stage | Judgment |
|---|---|
| Before structured techniques | High confidence attribution to MSS based on a joint advisory |
| After structured techniques | Moderate confidence attribution to MSS based on the joint advisory and prior examples of contractors serving multiple clients |

The adjustment does not necessarily reject the original attribution. It makes the judgment more precise by distinguishing actor cluster, sponsorship, control, and confidence.

## Recommended Use in Repository Outputs

When writing cyber attribution assessments, include a short reasoning discipline section:

| Field | Example |
|---|---|
| Techniques used | Clustering, Key Assumptions Check, ACH, Devil's Advocacy, Pre-Mortem |
| Source grading | Admiralty Code / NATO System ratings for key evidence items |
| Estimative language | FIRST/NATO WEP term and probability range |
| Analytic confidence | FIRST/NATO LCA term: high, moderate, or low confidence |
| Main assumptions | Infrastructure control, tool exclusivity, actor continuity |
| Alternatives considered | State service, contractor or proxy, criminal reuse, false flag |
| Evidence gaps | Control evidence, independent corroboration, infrastructure reuse history |
| Confidence impact | Confidence reduced from high to moderate pending additional corroboration |

## References

Caltagirone, S., Pendergast, A., & Betz, C. (2013). *The diamond model of intrusion analysis*. ThreatConnect.

Forum of Incident Response and Security Teams. (n.d.). *Communicating uncertainties in CTI reporting*. Retrieved June 24, 2026, from https://www.first.org/global/sigs/cti/curriculum/cti-reporting

Heuer, R. J., Jr. (1999). *Psychology of intelligence analysis*. Center for the Study of Intelligence, Central Intelligence Agency.

Janis, I. L. (1972). *Victims of groupthink: A psychological study of foreign-policy decisions and fiascoes*. Houghton Mifflin.

Kent, S. (1964). Words of estimative probability. *Studies in Intelligence, 8*(4), 49-65.

Klein, G. (2007). Performing a project premortem. *Harvard Business Review, 85*(9), 18-19.

North Atlantic Treaty Organization. (2016). *AJP-2.1 allied joint doctrine for intelligence procedures*. NATO Standardization Office.

Office of the Director of National Intelligence. (2018). *A guide to cyber attribution*. Cyber Threat Intelligence Integration Center.

Pherson, R. H., & Heuer, R. J., Jr. (2021). *Structured analytic techniques for intelligence analysis* (3rd ed.). CQ Press.

Rid, T., & Buchanan, B. (2015). Attributing cyber attacks. *Journal of Strategic Studies, 38*(1-2), 4-37. https://doi.org/10.1080/01402390.2014.977382

U.S. Department of the Army. (2006). *Human intelligence collector operations* (FM 2-22.3). Department of the Army.
