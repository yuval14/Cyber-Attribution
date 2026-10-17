# Static PE Evidence and Attribution Comparison

## Purpose and research boundary

This comparison supports the research topic *Cyber Attribution in the AI Age*. It distinguishes what execution-free Windows PE analysis can measure from what requires additional incident, campaign, actor or legal evidence. A malware-family label is a technical classification, not an identification of the operator who deployed it.

The planned experiment uses VirusShare as the sole malware acquisition source. Benign controls come from authentic operating systems and official software distributions, including independently verified challenging benign tools. Mentioning another dataset in the literature does not make it part of the experimental corpus. No new real-malware performance results are reported here.

## Tasks and evidence requirements

| Task | Target and required labels | Role in the PE experiment | Inference boundary |
| --- | --- | --- | --- |
| Malicious-content detection | Independently established malicious or benign file status | Direct evaluation of recall, false-positive rate, precision and confusion counts | Does not identify a malware family or actor by itself |
| Malware-family classification | Independently supported family labels, aliases and confidence records | Direct Macro-F1 comparison on the same eligible malicious files | Does not establish campaign membership or common control |
| Campaign linkage | Independently supported links across incidents or artifacts | Possible downstream use of the evidence record; not a confirmatory endpoint | Requires context beyond static file similarity |
| Actor attribution | Independently supported links to an operator or group | Outside the present experiment | Shared or copied malware is insufficient |
| State responsibility | Legally relevant relationships and an applicable legal assessment | Outside the present experiment | Classifier outputs do not establish legal responsibility |

## Relevant comparators

| Work or tool | Source type | Established overlap | Appropriate comparison and limitation |
| --- | --- | --- | --- |
| Steffens, Attribution of Advanced Persistent Threats | Academic book | Organizes malware within a broader attribution process | Conceptual evidence organization; not a matched PE classifier baseline |
| Unit 42 Attribution Framework | Practitioner framework | Evidentiary objects, reliability and credibility grading, clusters and review before naming | Compare the evidence handoff and contextual review; publication is not independent proof of accuracy |
| TrendAI Attribution Framework | Practitioner framework | Adapted Diamond Model, baseline artifact scoring and ACH | Compare analytical organization; distinguish its fixed scores from Unit 42's contextual adjustments |
| FIRST Source Evaluation | Professional guidance | Separates source reliability from information credibility | Supports terminology; does not calibrate classifier probabilities |
| HexAttribution | Peer-reviewed academic article | Multidimensional attribution and a reliability proof of concept | Compare assumptions and evidence categories; do not assume calibrated actor probabilities |
| Beg et al., evidence-driven few-shot meta-learning | Peer-reviewed academic article | Evidence graphs, learning, uncertainty and executable forensic signatures | Close conceptual overlap; includes execution-related traces and a different learning task |
| Synthetic APTs | Author preprint | AI emulation and convergent behaviors in cyber ranges | Relevant to imitation risks; limited study, not a universal demonstration that TTP attribution fails |
| YARA | Official technical documentation | String, byte and Boolean matching | Defines rule semantics; a match does not establish actor identity |
| capa | Official software documentation | Executable-capability identification and supporting match locations | Compare representation and evidence localization; capability is not proof of execution |
| MOTIF and AVClass2 | Academic dataset and labeling research | Family-label quality and AV-tag normalization | Inform label curation; multiple vendors are not automatically independent witnesses |
| BenchMFC, TESSERACT and Transcend | Academic evaluation research | Family drift, evaluation bias and changing distributions | Motivate explicit temporal and population limits; task and platform differences matter |
| Real-Time Source Attribution of Cyberattacks via AI-Driven Threat Intelligence | IEEE conference publication record verified | Candidate AI-attribution comparator | Full-method and result assessment pending; unavailable details must not be treated as absent capabilities |
| Making Analytic Confidence Visible | Publisher record verified | Candidate analytic-confidence comparator | Full-text verification pending in this update; no empirical efficacy claim is made |

## Provisional contribution to test

Rules, machine learning, static features, capability descriptions and auditable outputs are established ideas. The proposed contribution is the incremental utility of a pre-specified rule-acceptance protocol and a nonduplicate evidence representation under a frozen, leakage-controlled static PE experiment.

The primary comparisons must distinguish:

1. Rules-only decisions from supervised adjudication on identical samples.
2. Conventional static family features from the same features plus the evidence representation, using the same eligible families, classifier family and tuning budget.
3. Acceptance gates from an appropriately controlled comparison without those gates.
4. Predictive utility from evidence completeness and exact pipeline reconstruction.

A correct replay can reproduce an incorrect prediction. An explainable score is not necessarily calibrated, and a high family-classification score is not analytical confidence in actor identity. Multiple rules derived from one library or string should not be counted as independent attribution evidence.

## Verification and source handling

The repository is a discovery map and an author-maintained research resource. Cite the original publication for claims about prior work. Cite this repository when discussing its original synthesis or implementation, not as independent validation of the author's own proposed contribution.

The supplementary review was conducted on 18 October 2026. It used repository files, publisher and conference records, official documentation, and selected accessible text. This is a targeted review, not a completed exhaustive PRISMA systematic review. No quantitative literature-flow counts are asserted. Full-method comparisons remain necessary before any priority claim.

## References

Balassone, F., Mayoral-Vilches, V., Sanz-Gómez, M., Zabalegui-Landa, P., Rass, S., Quarta, D., Sanchez-Prieto, D., Oteiza-Álvarez, M., Graziano, A., Kim, L. M., & Choi, M. (2026). *Synthetic APTs: The collapse of TTP-based attribution* [Preprint]. arXiv. https://doi.org/10.48550/arXiv.2606.07158

Beg, R., Nigam, N., Sharma, Y. K., Patel, A., Solanki, S., Sharma, S., & Kumar, L. (2026). Design of an integrated evidence-driven few-shot meta-learning for zero-day malware detection and forensic attributions. *Scientific Reports, 16*, Article 20974. https://doi.org/10.1038/s41598-026-43745-9

Forum of Incident Response and Security Teams. (n.d.). *Source evaluation and information reliability*. https://www.first.org/global/sigs/cti/curriculum/source-evaluation

Hilt, S. (2026, February 12). *Threat attribution framework: How TrendAI applies structure over speculation*. TrendAI. https://www.trendaisecurity.com/en-us/resources-insights/deep-research/threat-attribution-framework-how-trendai-applies-structure-over-speculation

Jiang, Y., Li, G., Li, S., & Guo, Y. (2024). BenchMFC: A benchmark dataset for trustworthy malware family classification under concept drift. *Computers & Security, 139*, 103706. https://doi.org/10.1016/j.cose.2024.103706

Jordaney, R., Sharad, K., Dash, S. K., Wang, Z., Papini, D., Nouretdinov, I., & Cavallaro, L. (2017). Transcend: Detecting concept drift in malware classification models. In *26th USENIX Security Symposium* (pp. 625-642). USENIX Association. https://www.usenix.org/conference/usenixsecurity17/technical-sessions/presentation/jordaney

Joyce, R. J., Amlani, D., Nicholas, C., & Raff, E. (2023). MOTIF: A malware reference dataset with ground truth family labels. *Computers & Security, 124*, 102921. https://doi.org/10.1016/j.cose.2022.102921

Mandiant. (n.d.). *capa* [Computer software]. GitHub. https://github.com/mandiant/capa

Mangaiyarkarasi, V., et al. (2025). Real-time source attribution of cyberattacks via AI-driven threat intelligence. In *2025 International Conference on Innovations and Emerging Technologies in AI & Communication Systems*. IEEE. https://doi.org/10.1109/IETACS68750.2025.11385633

Pendlebury, F., Pierazzi, F., Jordaney, R., Kinder, J., & Cavallaro, L. (2019). TESSERACT: Eliminating experimental bias in malware classification across space and time. In *28th USENIX Security Symposium* (pp. 729-746). USENIX Association. https://www.usenix.org/conference/usenixsecurity19/presentation/pendlebury

Rid, T., & Buchanan, B. (2015). Attributing cyber attacks. *Journal of Strategic Studies, 38*(1-2), 4-37. https://doi.org/10.1080/01402390.2014.977382

Sebastián, S., & Caballero, J. (2020). AVClass2: Massive malware tag extraction from AV labels. In *Annual Computer Security Applications Conference* (pp. 42-53). ACM. https://doi.org/10.1145/3427228.3427261

Steffens, T. (2020). *Attribution of advanced persistent threats: How to identify the actors behind cyber-espionage*. Springer Vieweg. https://doi.org/10.1007/978-3-662-61313-9

Szulcsányi, V., & Magyar, S. (2026). A comparative analysis of threat models in the context of cyber threat attribution. *International Journal of Information Security, 25*, Article 105. https://doi.org/10.1007/s10207-026-01272-8

Szewczyk, Z. (2026). Making analytic confidence visible: An operational rubric for cyber analysis. *The Cyber Defense Review, 11*(3). https://doi.org/10.55682/cdr/rm2g-74cw

Unit 42. (2025, July 31). *Introducing Unit 42's attribution framework*. Palo Alto Networks. https://unit42.paloaltonetworks.com/unit-42-attribution-framework/

VirusTotal. (n.d.). *YARA: The pattern matching swiss knife for malware researchers*. https://virustotal.github.io/yara/
