# Source, Evidence, and Corroboration Evaluation in Cyber Attribution

This comparative table distinguishes source reliability, information credibility, evidentiary strength, independence of corroboration, analytic confidence, and estimative probability. These methods serve different purposes and should not be treated as interchangeable attribution algorithms.

Research applications and limitations below are comparative interpretations for this repository, not claims that the cited organizations have validated a common scoring model.

## Comparative Table

| Method or framework | Type | What is evaluated? | Main output | Practical application in cyber attribution and AI-assisted analysis | Limitation or overlap | Reference |
|---|---|---|---|---|---|---|
| Admiralty Code / NATO System | Source and information grading system | Source authenticity, competence, and reporting history separately from the credibility of a specific report | Source rating A-F and information rating 1-6, with rationale | Grade external reports and individual evidence items before integrating them into an attribution assessment | A source rating does not establish actor identity, evidence independence, or resistance to deception. F and 6 mean insufficient basis to judge, not necessarily poor quality | [FIRST source evaluation](https://www.first.org/global/sigs/cti/curriculum/source-evaluation) |
| FIRST Source Evaluation and Information Reliability | Professional implementation guidance | Reliability of the source and the information it supplies in CTI | Documented source and information ratings | Apply consistent grading to vendor reports, feeds, OSINT, and other external reporting | FIRST recommends the NID A-F / 1-6 model. This is substantially the same grading family as Admiralty, not a separate independent method | [FIRST source evaluation](https://www.first.org/global/sigs/cti/curriculum/source-evaluation) |
| Quality of Information Check | Structured analytic technique | Completeness, accuracy, collection context, source strengths and weaknesses, processing errors, and corroboration of critical reporting | Information-quality review, evidence gaps, and revised caveats | Periodically review the evidence base; check original collection and processing before relying on vendor or AI summaries | Multiple sources do not substitute for sound information. This review does not by itself establish actor identity or calibrate a probability | [CIA tradecraft primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf) |
| Independent Corroboration | Evidence evaluation principle | Whether supporting observations or reports originate from genuinely independent collection or evidence streams | Independent support, dependencies, and unresolved corroboration gaps | Check whether multiple vendors or AI outputs rely on different underlying evidence before increasing confidence | Different publishers, model names, or output wording do not by themselves prove independence; hidden upstream dependencies may remain unknown | [FIRST source evaluation](https://www.first.org/global/sigs/cti/curriculum/source-evaluation); [Investigation techniques](Investigation-Techniques.md); [False flag analysis](False-Flag-Cyber-Attribution.md) |
| Provenance and Circular Reporting Review | Evidence tracing procedure | Original source, collection context, transformations, citations, and reporting dependencies | Source lineage map and dependency register | Trace a claim through vendor reporting, enrichment tools, retrieval systems, and AI summaries; identify repeated versions of one original claim | Provenance can be incomplete. A traceable chain does not itself establish that the original claim is true | [False flag analysis](False-Flag-Cyber-Attribution.md) |
| Spoofability Assessment | Adversarial evidence review | How easily an artifact can be forged, planted, copied, or consistently imitated | Artifact-specific deception assessment and mitigation requirements | Review language markers, timestamps, malware reuse, infrastructure overlap, and AI-assisted TTP imitation | The repository's 1-5 scale is a practical heuristic, not an established validated measurement instrument. Difficult to spoof does not mean sufficient for attribution | [False flag analysis](False-Flag-Cyber-Attribution.md); [Skopik and Pahi](https://doi.org/10.1186/s42400-020-00048-4) |
| Key Assumptions Check (KAC) | Structured analytic technique | Assumptions required for the assessment, their support, criticality, and potential falsifiers | Assumption register and collection priorities | Test assumptions about infrastructure control, tool exclusivity, actor continuity, and independence of AI-derived outputs | Exposes weak assumptions but does not replace collection or establish source credibility | [CIA tradecraft primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf); [Investigation techniques](Investigation-Techniques.md); [PwC](https://www.pwc.com/gx/en/issues/cybersecurity/cyber-threat-intelligence/threat-intelligence-comparative-attribution.html) |
| Analysis of Competing Hypotheses (ACH) | Structured analytic technique | Consistency and inconsistency of evidence across plausible competing explanations; diagnostic value of evidence | Evidence-hypothesis matrix, surviving explanations, and evidence gaps | Compare known actor, shared tooling, proxy, compromised infrastructure, false flag, and AI-assisted imitation hypotheses | Results depend on hypothesis coverage and evidence quality. A tally of supporting items is not a calibrated probability | [CIA tradecraft primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf); [Investigation techniques](Investigation-Techniques.md) |
| Sensitivity Analysis | Robustness test; also a component of ACH | Whether conclusions change when critical evidence, assumptions, or weights are removed, weakened, or reinterpreted | Stability assessment and identification of decisive dependencies | Remove a vendor claim or a whole family of AI outputs derived from the same source and reassess attribution | Robustness is conditional on the tested changes; stability does not prove correctness. Can be applied independently or within ACH; do not double-count the same sensitivity exercise as two separate validation activities | [Szewczyk](https://doi.org/10.55682/cdr/rm2g-74cw); [HexAttribution](https://doi.org/10.1007/s10207-026-01272-8); [Investigation techniques](Investigation-Techniques.md) |
| Devil's Advocacy | Structured challenge technique | Strongest counterargument to the leading assessment, including weak sources and alternative explanations | Challenge memo, evidence gaps, and revised confidence wording | Assign a reviewer to challenge actor identity, control, sponsorship, and unjustified confidence | Effectiveness depends on reviewer independence, expertise, and access to evidence | [CIA tradecraft primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf); [Investigation techniques](Investigation-Techniques.md) |
| Pre-Mortem Analysis | Prospective failure analysis | How an attribution assessment might later prove wrong | Failure scenarios and preventive actions | Consider circular reporting, AI hallucination, false flags, shared contractors, or incorrect activity clustering before release | Generates possible failure explanations; does not establish their likelihood or verify evidence | [Klein (2007)](https://hbr.org/2007/09/performing-a-project-premortem); [Investigation techniques](Investigation-Techniques.md) |
| Clustering and Link-Strength Review | Analytical organization method | Shared features, relationship strength, outliers, and alternative explanations for overlap | Activity clusters and documented links | Group malware, infrastructure, certificates, behavior, and victimology while documenting why each link is accepted | Similarity can reflect shared tools, hosting, automation, or imitation. A cluster is not automatically a named actor or sponsor | [Investigation techniques](Investigation-Techniques.md); [Diamond Model](https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf) |
| Levels of Confidence in Assessment (LCA) | Confidence communication framework | Confidence in a judgment given evidence quality, reliability, corroboration, and ambiguity | High, moderate, or low confidence with explanation | Communicate confidence after evaluating evidence and alternatives; identify reasons confidence is limited | Confidence is distinct from probability. LCA labels are not a numerical evidence aggregation algorithm | [FIRST uncertainty reporting](https://www.first.org/global/sigs/cti/curriculum/cti-reporting) |
| Words of Estimative Probability (WEP) | Estimative language framework | Likelihood of an event, outcome, or analytic judgment | Standardized probability wording | State how likely an attribution hypothesis is separately from confidence in the assessment | WEP does not grade source quality. Verbal probability ranges vary across adopted standards and should be declared | [FIRST uncertainty reporting](https://www.first.org/global/sigs/cti/curriculum/cti-reporting) |
| ICD 203 Analytic Standards | Intelligence analytic quality standard | Source and methodology quality, uncertainty, assumptions, alternatives, reasoning, relevance, and other analytic tradecraft requirements | Quality review of an analytic product | Use as a basis for an explicit assessment checklist or research rubric, with operational definitions and validation | Not a source-rating algorithm or a cyber attribution model. A locally derived rubric should not be presented as an official ICD 203 scoring instrument | [ODNI ICD 203](https://www.dni.gov/files/documents/ICD/ICD-203.pdf) |
| PwC Framework for Comparative Attribution | Cross-assessment comparison framework | Evidence, direct and indirect sources, visibility gaps, methodologies, assumptions, and conditions for change across assessments | Documented comparison and questions for reassessment | Compare conflicting vendor assessments and identify differences in evidence access, actor boundaries, and analytic reasoning | Agreement between assessments does not establish independent corroboration; undisclosed collection limits verification | [PwC comparative attribution](https://www.pwc.com/gx/en/issues/cybersecurity/cyber-threat-intelligence/threat-intelligence-comparative-attribution.html) |
| Unit 42 Attribution Framework | Integrated industry attribution framework | Evidentiary objects organized with the Diamond Model and Admiralty reliability and credibility scores, alongside promotion standards | Activity clusters, temporary threat groups, and named threat actors, supported by evidence review | Compare evidence grading, cluster development, analyst adjustments, and review-board decisions | Default scores may be adjusted with justification. Promotion to a named group does not automatically establish legal state responsibility | [Unit 42](https://unit42.paloaltonetworks.com/unit-42-attribution-framework/) |
| TrendAI Threat Attribution Framework | Integrated industry attribution framework | Evidence scores, relationships across an adapted Diamond Model, persistent behavior, and competing explanations using ACH | Structured clusters and defensible attribution judgments | Compare an approach that combines Diamond relationships, Admiralty-derived scoring, and alternative-hypothesis testing | The published description uses fixed baseline artifact scores and builds confidence through correlation. Its attribution-value interpretation should be distinguished from information truthfulness in traditional source grading | [TrendAI](https://www.trendaisecurity.com/en-us/resources-insights/deep-research/threat-attribution-framework-how-trendai-applies-structure-over-speculation) |
| Operational Analytic Confidence Rubric | Qualitative operational rubric for SOC analytic sufficiency | Depth of ICD 203 application and observable rigor behaviors: hypothesis exploration, search, validation, source stance, sensitivity testing, specialist collaboration, synthesis, and explanation critique | Low, moderate, and high ordinal confidence anchors with documented analytic work, gaps, and review depth | Compare a proposed attribution rubric against a process-oriented framework; preserve sources, tool outputs, assumptions, and revisions in AI-assisted workflows | A professional commentary and practitioner synthesis, not an empirically validated scoring model. No calibrated numeric thresholds or demonstrated decision-quality improvements; the malware example is hypothetical | [Repository bibliographic entry](Cyber-Attribution-Frameworks.md); [Article DOI](https://doi.org/10.55682/cdr/rm2g-74cw) |
| InCA (Intelligent Cyber Attribution) | Formal argumentation and probabilistic reasoning framework | Conflicting or uncertain evidence and arguments supporting or challenging attribution conclusions | Explained attribution conclusions within a formal reasoning model | Compare explicit reasoning over uncertain evidence with a proposed operational evidence-review procedure | Formal representation and probabilistic assumptions require justification; the publication does not establish a general-purpose operational source-grading scale | [Shakarian et al. (2014)](https://arxiv.org/abs/1404.6699) |
| HexAttribution | Multidimensional attribution and reliability framework | Five substantive evidence domains with a derived reliability layer based on domain scores, structural strengths, and scenario weights | Structured attribution assessment and transparent reliability calculation | Compare the proposed procedure with an existing model that explicitly incorporates reliability and sensitivity analysis | Parameters rely on expert judgment; overlapping evidence requires conservative treatment. The authors describe a proof of concept, not full external empirical validation; scores should not be assumed to be calibrated probabilities | [Szulcsányi and Magyar (2026)](https://doi.org/10.1007/s10207-026-01272-8) |
| MICTIC | Attribution-process organization framework | Attribution evidence categories, detail of APT group definitions, and analysis results | Structured attribution analysis | Include as a comparator for organizing evidence, rather than as an interchangeable source-confidence scale | Verification here is limited to the publisher's chapter abstract and bibliographic record; the complete chapter was not reviewed, so detailed scoring or validation claims are not made | [Steffens (2020), The Attribution Process](https://link.springer.com/chapter/10.1007/978-3-662-61313-9_2) |

## Operational Analytic Confidence Rubric: Detailed Review

Szewczyk (2026) combines ICD 203 product standards with the observable rigor attributes of Zelik, Patterson, and Woods (2007). The purpose is to document whether analysis is sufficient for the decision under the available time, evidence, and consequences of error.

| Rigor attribute | What the reviewer examines | Example record in a cyber attribution assessment |
|---|---|---|
| Hypothesis exploration | Whether plausible competing explanations were considered | Known actor, proxy, shared tooling, and false flag hypotheses |
| Information search | Breadth and depth of collection relative to the question | Telemetry searched, time window, additional victims examined, and unavailable sources |
| Information validation | Corroboration and cross-checking of reports and tool outputs | Independent evidence supporting a claim and validation limitations |
| Stance analysis | Source perspective, expertise, biases, and tool or sensor limitations | Vendor visibility, collection scope, sensor blind spots, and automated verdict caveats |
| Sensitivity analysis | Fragility of assumptions and conclusions | Result after removing a critical report or changing an infrastructure-control assumption |
| Specialist collaboration | Relevant external expertise used | Malware specialist consultation and unresolved expert disagreements |
| Information synthesis | Integration of diverse evidence and interpretations | Explanation linking technical findings to campaign context without conflating evidence and inference |
| Explanation critique | Challenge of the main explanation and its reasoning | Peer-review findings, alternative interpretations, and resulting revisions |

The record examples are repository applications, not verbatim requirements from the paper.

| Confidence tier | Paraphrased interpretation |
|---|---|
| Low | Support is limited or weakly checked, with important time or visibility constraints |
| Moderate | Relevant evidence, partial corroboration, explicit assumptions, and proportionate review support a defensible assessment |
| High | Converging evidence, deeper validation, and stronger challenge of alternatives and assumptions support the judgment |

The tiers are qualitative ordinal anchors. They do not measure analyst competence, prescribe universal numerical cutoffs, or directly represent the probability that an attribution hypothesis is true.

The paper also distinguishes missing observations from missing observability. A lack of detected evidence may reflect sensor coverage or retention limitations rather than the absence of activity. Its proposed evaluation agenda includes inter-rater agreement, controlled exercises, comparison with subsequent ground truth, and decision testing through wargaming.

For AI-assisted analysis, the paper recommends retaining evidence of the process, including hypotheses, sources, prompts, tool calls, evidence trails, intermediate judgments, tool outputs, validation steps, and revisions. It explicitly leaves the effectiveness of these practices for evaluating analytic agents to future validation. Process documentation alone should therefore not be claimed as a novel contribution without comparison against this existing proposal; any new contribution requires a clearly specified additional mechanism and appropriate evaluation.


## Practical Integration

1. Preserve the evidence and document its collection context and provenance.
2. Grade source reliability and information credibility separately.
3. Identify shared origins and dependencies before counting corroboration.
4. Evaluate spoofability and distinguish direct observations from derived outputs and inference.
5. Document key assumptions and plausible competing explanations.
6. Apply ACH, sensitivity testing, challenge review, and pre-mortem analysis as appropriate.
7. State estimative probability and analytic confidence separately, with reasons and remaining gaps.
8. Review the finished assessment against explicit analytic quality criteria.

For AI-assisted work, preserve the underlying sources, input material, transformations, and verification record. Treat outputs as derived analysis unless they expose independently collected and verified evidence. Multiple outputs from one evidence base should not be counted as multiple independent observations.

These steps are a suggested synthesis for this repository, not a single validated composite method. Evaluation of a new research rubric should include clear construct definitions, scoring anchors, inter-rater agreement, and comparisons with relevant existing approaches.

## References

Central Intelligence Agency. (2009, March). *A tradecraft primer: Structured analytic techniques for improving intelligence analysis*. https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf


Caltagirone, S., Pendergast, A., & Betz, C. (2013). *The diamond model of intrusion analysis*. https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf

Forum of Incident Response and Security Teams. (n.d.). *Source evaluation and information reliability*. https://www.first.org/global/sigs/cti/curriculum/source-evaluation

Forum of Incident Response and Security Teams. (n.d.). *Communicating uncertainties in CTI reporting*. https://www.first.org/global/sigs/cti/curriculum/cti-reporting

Hilt, S. (2026, February 12). *Threat attribution framework: How TrendAI applies structure over speculation*. TrendAI. https://www.trendaisecurity.com/en-us/resources-insights/deep-research/threat-attribution-framework-how-trendai-applies-structure-over-speculation

Klein, G. (2007). Performing a project premortem. *Harvard Business Review, 85*(9), 18-19. https://hbr.org/2007/09/performing-a-project-premortem

Office of the Director of National Intelligence. (n.d.). *Intelligence Community Directive 203: Analytic standards*. https://www.dni.gov/files/documents/ICD/ICD-203.pdf

PricewaterhouseCoopers. (2025, June 20). *How we analyse, compare, and integrate multiple threat actor attribution assessments*. https://www.pwc.com/gx/en/issues/cybersecurity/cyber-threat-intelligence/threat-intelligence-comparative-attribution.html

Shakarian, P., Simari, G. I., Moores, G., Parsons, S., & Falappa, M. A. (2014). *An argumentation-based framework to address the attribution problem in cyber-warfare* [Preprint]. arXiv. https://arxiv.org/abs/1404.6699

Skopik, F., & Pahi, T. (2020). Under false flag: Using technical artifacts for cyber attack attribution. *Cybersecurity, 3*, Article 8. https://doi.org/10.1186/s42400-020-00048-4

Steffens, T. (2020). The attribution process. In *Attribution of advanced persistent threats: How to identify the actors behind cyber-espionage* (pp. 23-50). Springer. https://doi.org/10.1007/978-3-662-61313-9_2

Szulcsányi, V., & Magyar, S. (2026). A comparative analysis of threat models in the context of cyber threat attribution. *International Journal of Information Security, 25*, Article 105. https://doi.org/10.1007/s10207-026-01272-8

Szewczyk, Z. (2026). Making analytic confidence visible: An operational rubric for cyber analysis. *The Cyber Defense Review, 11*(3). https://doi.org/10.55682/cdr/rm2g-74cw

Unit 42. (2025, July 31). *Introducing Unit 42's attribution framework*. Palo Alto Networks. https://unit42.paloaltonetworks.com/unit-42-attribution-framework/

Zelik, D., Patterson, E. S., & Woods, D. D. (2007). Understanding rigor in information analysis. In K. L. Mosier & U. M. Fischer (Eds.), *Proceedings of the Eighth International Conference on Naturalistic Decision Making*. https://csel.eng.ohio-state.edu/productions/intelligence/1_Patterns/Rigorous_Process/ZelikEtAl2007_UnderstandingRigorInInformationAnalysis.pdf

The Szewczyk article was reviewed from the supplied publisher PDF, marked in press, volume 11, issue 3 (2026), 12 pages. It was accepted on September 24, 2026. The summary above paraphrases its framework rather than reproducing its tables.

## Verification Scope

Primary-source support is distinguished from evidence of empirical effectiveness. A published proposal, professional practice description, or hypothetical demonstration does not by itself establish calibrated scoring, inter-rater reliability, or improved attribution accuracy. The MICTIC entry is explicitly limited to publisher-abstract verification. Zelik et al. (2007) is cited as the foundational work identified in Szewczyk's paper; its full text was not independently reviewed for this update.

The paper *Cyber-Security Threats Origins and their Analysis* by Čergeť and Hudec (2023) was reviewed from the journal PDF. It describes public-data fusion and IP geolocation analysis; it does not substantiate the label Evidence-Based Attribution Model (EBAM). That attribution is therefore excluded here. [Original paper](https://acta.uni-obuda.hu/Cerget_Hudec_138.pdf)

FACT is not included in the verified comparison because its original framework document was unavailable during this review. This access limitation does not establish that the framework is invalid or unpublished.

## Related Documents

- [Investigation Techniques](Investigation-Techniques.md)
- [False Flag Cyber Attribution](False-Flag-Cyber-Attribution.md)
- [Cyber Attribution Frameworks](Cyber-Attribution-Frameworks.md)
- [AI-Based Cyber Attribution](AI-Based-Cyber-Attribution.md)
