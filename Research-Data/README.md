# Research Data Library

A catalog of cyber research resources organized by data type, including incident records, actor-labeled samples, CTI reports, provenance data, SOC telemetry, emulation datasets, and attribution benchmarks.

## Credit and terms of use

Credit belongs to the dataset creators, publishers, and maintainers identified below. The respective dataset owners and maintainers are responsible for the accuracy and availability of their data. Access to and use of each source are subject to its owner's applicable terms of use, license, and access conditions. Consult the original source before downloading, reusing, or redistributing data, and cite the specific release or record used.

## Browse by data type

The categories distinguish research artifacts from knowledge bases, simulated activity, and derived copies. A source is listed once under its primary role; it can support more than one research task.

| Type | Section | Main research task |
| --- | --- | --- |
| Incident records | [Incident and campaign sources](#incident-and-campaign-sources) | Incident coding, public attribution, targeting, and campaign context |
| Impact records | [Critical infrastructure and service disruption](#critical-infrastructure-and-service-disruption) | Operational impact, disruption, and recovery |
| CTI text benchmarks | [Attribution and CTI benchmarks](#attribution-and-cti-benchmarks) | Attribution from descriptions and entity extraction |
| Actor-labeled samples | [Actor- and campaign-labeled malware datasets](#actor--and-campaign-labeled-malware-datasets) | Sample association with reported groups or campaigns |
| Reports and knowledge bases | [CTI reports and attribution knowledge bases](#cti-reports-and-attribution-knowledge-bases) | Evidence retrieval, name reconciliation, and hypothesis comparison |
| Host provenance | [System provenance and attack investigation datasets](#system-provenance-and-attack-investigation-datasets) | Causal reconstruction, graph analysis, and attack investigation |
| Security telemetry | [SOC and multi-source security logs](#soc-and-multi-source-security-logs) | Cross-source investigation and detection analytics |
| Adversary emulation | [Actor-inspired emulation datasets](#actor-inspired-emulation-datasets) | Controlled evaluation against a specified emulated behavior |
| IoT telemetry | [IoT intrusion detection datasets](#iot-intrusion-detection-datasets) | Multi-source IoT detection and attack-stage analysis |
| Static malware data | [Static malware research datasets](#static-malware-research-datasets) | Detection, family classification, and static feature evaluation |
| Derived data and tooling | [Corrected datasets and research tooling](#corrected-datasets-and-research-tooling) | Data preparation and reproducible comparison |
| Availability watchlist | [Research resources requiring access verification](#research-resources-requiring-access-verification) | Candidate resources not yet verified as usable downloads |

**Attribution boundary:** Maliciousness, malware family, campaign membership, reported group association, code authorship, and state responsibility are different targets. Preserve the original label meaning. An emulation of a named group's behavior is not an observed operation by that group. An original dataset and its corrected or preprocessed copy are not independent evaluation sets.

Catalog additions reviewed: November 24, 2026. This date refers to documentation and repository checks, not to downloading or validating every underlying sample archive. Existing incident and static-malware entries retain their source-specific release information.

## Incident and campaign sources

| Source | Publisher or maintainer | Coverage and unit | Access | Research use and limitations |
| --- | --- | --- | --- | --- |
| [EuRepoC Global Dataset](https://eurepoc.eu/database/) | European Repository of Cyber Incidents (EuRepoC) | Global cyber incidents since 2000, with more systematic collection since 2023 | Downloadable releases and live table. [Version 1.3 and codebook](https://zenodo.org/records/14965395) | Compare incident, target, and attribution coding. Use incident IDs to avoid counting related rows as separate events. |
| [Cyber Events Database 2.0](https://gotech.umd.edu/cyber-events-database) | University of Maryland, GoTech and CISSM | Global cyber events since 2014 | CSV, JSON, and codebook | Compare sectors and observable effects. Event date and publication date represent different observations. |
| [Dyadic Cyber Incident Dataset v2.0](https://doi.org/10.7910/DVN/CQOMYV) | Brandon Valeriano and dataset collaborators | Historical incidents in interstate rivalries | Versioned download via Harvard Dataverse | Study rivalry and escalation. Check release coverage before using it for recent events. |
| [Cyber Operations Tracker](https://www.cfr.org/cyber-operations/) | Council on Foreign Relations | Publicly known state-sponsored incidents since 2005 | Web tracker | Examine suspected sponsorship and targeting. Record the source and confidence of the attribution. |
| [Significant Cyber Incidents](https://www.csis.org/programs/strategic-technologies-program/significant-cyber-incidents) | Center for Strategic and International Studies | Selected significant incidents since 2006 | Web timeline | Identify cases and timelines. The selection criteria limit incidence and recovery comparisons. |
| [VERIS Community Database](https://verisframework.org/vcdb.html) | VERIS Community Database contributors | Publicly reported security incidents, including data breaches | Open repository linked by VERIS | Compare coded incident characteristics. Public disclosure affects coverage. |
| [Cyber Attacks in Times of Conflict](https://cyberconflicts.protect.ngo/) | CyberPeace Institute | Incidents in the context of Russia's war against Ukraine | Public portal | Trace conflict-related activity and reported civilian harm. Distinguish claims from corroborated findings. |
| [Campaign escalation registry](https://scholar.dsu.edu/ccspapers/167/) | Salim Arfaoui, Patrick H. Engebretson, and Youssef Dr. Harrath | 54 documented campaigns from 2007 to 2025 | Research publication and registry description | Compare escalation coding. The curated sample supports method validation. |
| [Japan Cybersecurity Tracker](https://www.mkultraman.com/japan-cybersecurity-tracker/dataset/) | Matthew Ketchum, MKUltraman | Organization-level cyber incident disclosures in Japan; one row per organization's notice, with sector, disclosure date, reported attack type, affected records, vendor exposure, and source links | Public summary; CSV available on request. CC BY 4.0 with attribution to Matthew Ketchum, MKUltraman | Study supplier dependencies and downstream exposure. Vendor links may be named, inferred, or unidentified; they are not threat actor attribution labels. Disclosure dates are not attack dates; related notices and record totals can overlap. Coverage depends on published disclosures. |
| [AI Incident Database (AIID) - Database Snapshots](https://incidentdatabase.ai/research/snapshots/) | Responsible AI Collaborative | Reported incidents involving harms or near harms associated with deployed AI systems. Multiple reports can be linked to a single incident | Weekly full database snapshots in JSON, CSV, and MongoDB archive formats | Identify cases and trace their reporting history. Use incident IDs to deduplicate reports, record the snapshot date, and corroborate actor attribution independently. |

Suggested citation for the Japan dataset release reviewed: Ketchum, M. (2026). *Japan Cybersecurity Tracker: Disclosed cyber incidents affecting organizations in Japan* [Data set, version of 2026-11-06]. MKUltraman. https://www.mkultraman.com/japan-cybersecurity-tracker/dataset/

Suggested citation for AIID: McGregor, S. (2021). Preventing repeated real world AI failures by cataloging incidents: The AI Incident Database. *Proceedings of the AAAI Conference on Artificial Intelligence, 35*(17), 15458-15463. https://doi.org/10.1609/aaai.v35i17.17817

## Critical infrastructure and service disruption

| Source | Publisher or maintainer | Coverage and unit | Access | Research use and limitations |
| --- | --- | --- | --- | --- |
| [Critical Infrastructure Tracker](https://cit.eurepoc.eu/) | EuRepoC | Critical infrastructure incidents in EuRepoC | Public dashboard | Sector filtering. Records share provenance with the parent dataset. |
| [SMICI](https://smici.umd.edu/smici_database) | University of Maryland, START | Cyber-physical and cyber-operational incidents affecting critical infrastructure | Public subset. Full data by request | Find cases with physical or operational impact. |
| [Critical Infrastructure Ransomware Attacks](https://sites.temple.edu/care/cira/) | Temple University, CARE Lab | Ransomware incidents affecting critical infrastructure | Public project and dataset page | Build ransomware case samples and corroborate operational effects with original reporting. |
| [ROCCA](https://orionpolicy.org/records-of-critical-cyber-attacks-project/) | Orion Policy Institute | Critical incidents affecting governments, infrastructure, and industry | Public dashboard | Compare significant cases across sectors. Review source and attribution on each record. |
| [The Observatory](https://www.16sectors.org/) | The Observatory project | Cross-sector critical infrastructure incidents | Public web catalog | Track verification status when selecting records. |
| [Cyber Incident Tracer #HEALTH](https://cybilportal.org/publications/cyber-incident-tracer-health/) | CyberPeace Institute | Disruptive cyberattacks affecting healthcare | Public resource listing | Identify reported impacts on care and corroborate recovery milestones. |
| [Breach Portal](https://ocrportal.hhs.gov/ocr/breach/breach_frontpage.jsf) | U.S. HHS Office for Civil Rights | U.S. reports of breaches of protected health information | Public regulatory portal | Confirm disclosures and affected organizations. Patient counts measure breach scope. |
| [Electric Disturbance Events](https://www.eia.gov/electricity/data/disturbance/disturb_events_archive.html) and [Event-Correlated Outage Dataset](https://catalog.data.gov/dataset/event-correlated-outage-dataset-in-america) | U.S. Department of Energy and Energy Information Administration | U.S. electric disturbances and outages from multiple causes | Public archive and downloadable dataset | Corroborate outage scope and timing. Establish the cyber link independently. |
| [EDGAR](https://www.sec.gov/edgar/search/) | U.S. Securities and Exchange Commission | Public company filings, including Form 8-K Item 1.05 disclosures | Public search | Corroborate reported business and operational impact. Track incident, discovery, and filing dates separately. |

## Attribution and CTI benchmarks

| Source | Credit | Unit and access | Research use |
| --- | --- | --- | --- |
| [CTIBench - CTI-TAA](https://github.com/maveryn/cti-bench) | CTIBench authors and contributors | Downloadable threat actor attribution examples | Evaluate attribution from CTI descriptions against benchmark labels. |
| [AttackER](https://arxiv.org/abs/2408.05149) | AttackER paper authors and dataset contributors | Annotated CTI text for named entity recognition. See publication for dataset details | Evaluate entity extraction as an input to attribution analysis. |

## Actor- and campaign-labeled malware datasets

These sources explicitly associate samples with reported groups or campaigns. For a Windows PE study, validate file format before inclusion and exclude other file types from the PE-only experiment.

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [APTMalware](https://github.com/cyber-research/APTMalware) | Cyber Research contributors | 3,594 malware samples associated with 12 APT groups. Downloadable sample archives and a CSV mapping sample hashes to public threat intelligence reports | Supports sample-level attribution research. Filter to Windows PE and review the cited reports to distinguish observed group use from authorship or sponsorship. |
| [ADAPT](https://github.com/SecPriv/adapt) | Aakanksha Saha and the ADAPT project, SecPriv | The project reports 6,134 samples associated with 92 threat groups and a separate test set of 230 samples with campaign and group labels. Executables and documents are represented. Full samples and feature files require a research access request to the maintainers | Supports campaign-level and group-level association across file types. Confirm access, release identity, labeling provenance, and the usable PE subset before selecting it as an experimental dependency. |
| [Cyber Science Lab APT Malware Dataset](https://cybersciencelab.com/datasets/apt-malware/) | Cyber Science Lab. Research by H. Haddadpajouh, A. Azmoodeh, A. Dehghantanha, and R. M. Parizi | 1,200 malware samples associated with five APT groups. The project describes header, opcode, bytecode, and system-call views and links to its dataset repository | The static views support comparison with the [MVFCC study](https://doi.org/10.1109/ACCESS.2020.3012907). Confirm which views and files are available before reproducing the benchmark. |

Reported group use does not establish who wrote the code or who operated every copy. Shared malware, code reuse, collection bias, and historical attribution changes can affect these labels.

## CTI reports and attribution knowledge bases

These resources provide context and reported relationships. They are not interchangeable with sample-level ground truth.

| Source | Credit | Unit and access | Research use and limitations |
| --- | --- | --- | --- |
| [APTnotes](https://github.com/aptnotes/data) | APTnotes contributors | Public reports and blogs indexed by title, publisher, date, report hash, and link in CSV and JSON; report files are hosted externally | Supports evidence retrieval, CTI extraction, and source tracing. The index's SHA-1 identifies the report file, not a malware sample. Deduplicate reports and trace shared underlying sources. |
| [MITRE ATT&CK Groups](https://attack.mitre.org/groups/) | MITRE ATT&CK | Public mappings from activity groups to reported techniques, software, campaigns, and source references | Supports behavior-based hypothesis comparison. Associated group names can overlap only partially; do not merge all names automatically. Technique coverage reflects public reporting rather than complete actor behavior. |
| [MISP Galaxy](https://github.com/MISP/misp-galaxy) | MISP Project and contributors | Machine-readable clusters covering threat actors, tools, malware, and related concepts | Supports vocabulary alignment and enrichment. Distinguish actors, operations, campaigns, and activity clusters; retain source-specific names and provenance when resolving aliases. |
| [Malpedia](https://malpedia.caad.fkie.fraunhofer.de/) | Fraunhofer FKIE | Public malware family catalog with aliases and references, plus [mappings to actor groups](https://malpedia.caad.fkie.fraunhofer.de/actors). Sample access requires an invite-only account | Normalize family labels and corroborate reported group use. Check sample-level evidence before assigning an actor label. |
| [dAPTaset](https://github.com/GiuseppeLaurenza/dAPTaset) | Giuseppe Laurenza and Riccardo Lazzeretti | Research code associated with a semi-automatic method for collecting and mapping APT-related data from public sources | Supports dataset construction and relationship mapping. The repository description does not establish that a complete, current, ready-to-download sample corpus is available; verify data artifacts and dependencies separately. |

## System provenance and attack investigation datasets

These datasets record or represent relationships among system activities. Their principal role is detection and reconstruction, not independent confirmation of real-world actor identity.

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [DARPA Transparent Computing (TC)](https://github.com/darpa-i2o/Transparent-Computing) | DARPA and TC program performers | Engagement data, CDM schemas, tools, and red-team ground-truth documentation. The main README describes Engagement 5; bulk data are hosted externally | Supports process, file, and network relationship analysis and attack reconstruction. Record engagement, performer, schema, and subset. CADETS, THEIA, TRACE, and other performer streams belong to this program and should not be counted as unrelated corpora. Research-prototype data can be incomplete. |
| [DARPA OpTC](https://github.com/FiveDirections/OpTC-data) | DARPA, Boston Fusion, Five Directions, BAE, and Provatek | Windows 10 endpoint telemetry in eCAR, Bro network data, and red-team documentation. The release covers about 500 collected hosts from a 1,000-host test environment; the README reports about 1 TB of compressed JSON-compatible data. Bulk data are hosted externally | Supports enterprise-scale and cross-host investigation. Preserve host, time, and entity identifiers; review the project's errata. Red-team documentation is not equivalent to a complete event-by-event actor label. |
| [ATLAS](https://github.com/purseclab/ATLAS) | Abdulellah Alsaheel and coauthors, PurSec Lab | Audit logs, processed experiment inputs, graph and sequence generation code, and attack-investigation experiments | Supports attack-entity identification and reconstruction. The documented evaluation includes manual cleaning and result editing; define and report those decisions when reproducing or automating it. This project is distinct from MITRE ATLAS. |
| [StreamSpot](https://github.com/sbustreamspot/sbustreamspot-data) | StreamSpot researchers; raw data credited to the University of Illinois Chicago team | The ALL dataset contains edges from 600 graphs covering five benign scenario types and one drive-by-download attack scenario type | Supports graph anomaly detection. The published preprocessing removes timestamps, encodes entity and edge types, and collapses some repeated edges. It is less suitable for detailed temporal or text-based forensic reconstruction. |

## SOC and multi-source security logs

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [OTRF Security Datasets](https://github.com/OTRF/Security-Datasets) | Roberto Rodriguez, Jose Luis Rodriguez, and OTRF contributors | Collections of benign and malicious security events from multiple platforms, with project documentation and dataset links | Supports detection analytics and analyst or agent investigation. Choose a specific package and inspect its scenario, background activity, collection method, and labels; the repository is not one uniform provenance dataset. |
| [LANL Comprehensive, Multi-Source Cybersecurity Events](https://csr.lanl.gov/data/cyber1/) | Alexander D. Kent, Los Alamos National Laboratory | 58 consecutive days of de-identified authentication, process, DNS, network-flow, and red-team event data. Approximately 1.65 billion events and 12 GB compressed, according to the publisher | Supports lateral-movement and cross-source analysis. The red-team file labels selected authentication compromise events, not all malicious events or actor identities. De-identification limits semantic interpretation. |
| [Splunk BOTS v3](https://github.com/splunk/botsv3) | Splunk BOTS authors and contributors | SOC investigation data spanning endpoint, network, cloud, and service sources; distributed as a pre-indexed Splunk package | Supports multi-source investigation and query-based agent evaluation. Installation depends on Splunk and documented add-ons; check version compatibility. It is not a neutral raw-log archive or a sample-to-actor attribution benchmark. |

## Actor-inspired emulation datasets

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [APT Simulation Datasets](https://github.com/skrghosh/apt-dataset) | Sutanu Kumar Ghosh and project collaborators | Controlled Windows 10 simulations using CALDERA and adversary-emulation guidance, including FIN6, APT29, menuPass, OilRig, and Wizard Spider scenarios; additional malware scenarios and ground-truth documentation are provided | Supports reconstruction and matching observed activity to an emulated behavior profile. A scenario name is an emulation target, not evidence that the real group generated the logs. Hold out complete scenarios or independent runs and avoid learning environment artifacts. |

## IoT intrusion detection datasets

| Source | Publisher or maintainer | Coverage and unit | Access | Research use and limitations |
| --- | --- | --- | --- | --- |
| [BCCC-IoT-APT-ZWave-2026](https://www.yorku.ca/research/bccc/ucs-technical/cybersecurity-datasets-cds/multi-source-iot-apt-detection-dataset-bccc-iot-apt-zwave-2026/) | Behaviour-Centric Cybersecurity Center (BCCC), York University | 11 labeled, multi-stage APT scenarios in a Z-Wave smart-home testbed (April-May 2025). Five data sources: IP network traffic, Z-Wave communications, MQTT traffic, device telemetry, and application/service logs. | Available by request through the dataset page. | Evaluate multi-source intrusion detection and attack-stage analysis. Hold out entire episodes to reduce leakage across data sources. The testbed labels describe simulated activity and provide no ground truth for real-world actor attribution. |

Suggested citation: Behaviour-Centric Cybersecurity Center. (2026). *Multi-source IoT APT detection dataset (BCCC-IoT-APT-ZWave-2026)* [Data set]. York University. https://www.yorku.ca/research/bccc/ucs-technical/cybersecurity-datasets-cds/multi-source-iot-apt-detection-dataset-bccc-iot-apt-zwave-2026/

## Static malware research datasets

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [EMBER 2018](https://github.com/elastic/ember) | Hyrum S. Anderson and Phil Roth. Hosted by Elastic | Version 2 static features extracted from 1 million Windows PE files scanned in or before 2018. Downloadable feature archive | Historical baseline for static malware detection. The feature archive supports feature-based experiments. Evaluating YARA rules directly requires separately obtained samples. |
| [EMBER2024](https://github.com/FutureComputing4AI/EMBER2024) | Robert J. Joyce, Gideon Miller, Phil Roth, Richard Zak, Elliott Zaresky-Williams, Hyrum Anderson, Edward Raff, and James Holt | Downloadable features and labels for approximately 3.2 million benign and malicious files across Win32, Win64, .NET, APK, ELF, and PDF | Supports detection, family classification, and behavior prediction. Restrict to Windows PE for PE-only comparisons and align feature definitions across releases. |
| [MOTIF](https://github.com/boozallen/MOTIF) | Robert J. Joyce and coauthors. Hosted by Booz Allen Hamilton | 3,095 disarmed Windows PE malware samples from 454 families. Downloadable samples, JSONL metadata, EMBER v2 features, and family aliases | Supports family classification and alias analysis using labels curated from threat intelligence. Account for modified PE header fields when extracting features from the disarmed samples. |
| [WinMalware2025](https://github.com/acsr-du/WinMalware2025) | ACSR contributors, University of Delhi | The [dataset paper](https://ieeexplore.ieee.org/abstract/document/11290447) reports 401,508 Windows malware samples across 160 families and 16 categories. The repository lists dataset and metadata directories and the CyberClassify curation tool | Supports large-scale family classification research. Verify binary availability and review the automated curation and labeling workflow before selecting a reproducible subset. |
| [RawMal-TF](https://github.com/CS-and-AI/RawMal-TF) | David Bálik, Martin Jureček, and Mark Stamp | Windows PE binaries grouped by type and family, plus precomputed features. The [dataset paper](https://arxiv.org/abs/2506.23909) reports 17 families and 14 types. The project links to an external download | Supports static feature extraction and YARA evaluation. Family labels were parsed from filenames. Check hash overlap with VirusShare and MalwareBazaar, both used as source collections. |
| [MalwareBazaar](https://bazaar.abuse.ch/) | abuse.ch and Spamhaus | Continuously updated malware samples and metadata. The [Community API](https://bazaar.abuse.ch/api/) requires an authentication key and supports queries by hash, signature, tag, and file type | Build a dated Windows PE sample set for temporal evaluation. Corroborate family labels and check hash overlap with other collections. |
| [SOREL-20M](https://github.com/sophos/SOREL-20M) | Sophos AI and ReversingLabs | Approximately 20 million benign and malicious Windows PE records with EMBER v2 features, labels, and metadata. Downloadable data include disarmed malware binaries | Large-scale static detection and false-positive evaluation. Account for modified PE header fields when extracting features from disarmed binaries. |
| [BODMAS](https://whyisyoung.github.io/BODMAS/) | Limin Yang and the BODMAS project collaborators | 57,293 malicious and 77,142 benign PE samples, with 581 malware families and first-seen metadata. Features and metadata are downloadable. Access to malware binaries is by request | Family classification and temporal evaluation. Use first-seen dates to build chronological splits. |
| [MalDICT](https://github.com/rjjoyce/MalDICT) | Robert J. Joyce and the MalDICT paper coauthors | Malware datasets with behavior, platform, vulnerability exploitation, and packer tags. The project provides static features and disarmed PE downloads | Test whether static features reflect shared capabilities or packers. Check for hash overlap with VirusShare, which supplies the source samples. |
| [Microsoft BIG 2015](https://www.kaggle.com/competitions/malware-classification/data) | Microsoft, hosted by Kaggle | Nine malware families. Competition data include hexadecimal byte dumps with PE headers removed and assembly listings | Historical baseline for family classification using bytes or opcodes. Full PE header analysis and structure-dependent YARA evaluation require other samples. |

Maliciousness, malware family, and threat actor identity are separate labels. Use independent campaign evidence when evaluating actor attribution.

## Corrected datasets and research tooling

| Resource | Credit | Type and access | Research use and limitations |
| --- | --- | --- | --- |
| [A New Hope for DARPA OpTC](https://correctedoptc.inria.fr/) | F. Majorczyk, B. Pilastre, and F. Dijoud; PIRAT team | Corrected OpTC data and host/network labeling, with links to data and correction scripts | Addresses identifier inconsistencies and labeling limitations reported by the authors. Record the correction release and labeling procedure. This is derived from OpTC and must not be used as an independent external test corpus against the original. |
| [PIDSMaker](https://github.com/ubc-provenance/PIDSMaker) | Tristan Bilot, Baoxiang Jiang, Thomas Pasquier, and collaborators | Research framework and preprocessed datasets, including DARPA TC, OpTC, ATLASv2, and CARBANAKv2 | Supports consistent experimental pipelines and baseline comparisons. Record code commit, source dataset, preprocessing, retained fields, and splits. Preprocessed subsets are not new independent observations. |

## Research resources requiring access verification

| Resource | Published description | Access finding and research implication |
| --- | --- | --- |
| [APT-ClaritySet paper](https://arxiv.org/abs/2512.15039) and [project repository](https://github.com/APT-ClaritySet/Dataset) | The paper reports 34,363 samples across 305 groups before deduplication, 25,923 samples across 303 groups after deduplication, and a function-reuse resource | On November 24, 2026, the GitHub repository returned an empty-repository response. The paper's description is not confirmation of accessible data. Treat it as a candidate requiring author contact or a verified alternative release before planning an experiment. |

## Selecting data for an attribution study

The following are research-design recommendations, not publisher guarantees.

| Study objective | Suggested starting resources | Required control |
| --- | --- | --- |
| Static Windows PE evidence and reported group association | APTMalware; ADAPT if access is obtained; Cyber Science Lab APT data after checking available views | Validate PE files, document label sources, and separate group association from family recognition and authorship. |
| Campaign or actor hypothesis assessment from CTI | APTnotes, ATT&CK, MISP Galaxy, and CTIBench CTI-TAA | Separate retrieval evidence from answer labels; apply a time cutoff and prevent actor names or benchmark answers leaking into inputs. |
| Attack-chain reconstruction from telemetry | ATLAS, DARPA TC, or a defined OpTC subset | Score recovered entities, steps, and relationships against the scenario evidence; do not report reconstruction accuracy as actor-attribution accuracy. |
| SOC agent investigation | OTRF, BOTS v3, or LANL | Specify available tools, query budget, evidence required, and a held-out investigation set. |
| Controlled matching to actor-inspired behavior | APT Simulation Datasets | Evaluate scenario or behavior-profile identification and state the simulation boundary explicitly. |
| Open-set attribution with abstention | Actor-labeled samples plus held-out groups and appropriately sourced unrelated malware | Keep entire unknown groups out of training and validation; report false attribution, coverage, and calibration alongside classification metrics. |

## Experimental validity and reproducibility

- Preserve source-native labels, normalized labels, supporting report IDs, dates, uncertainty, and conflicts. Do not silently collapse partially overlapping actor names.
- Deduplicate by cryptographic hash and inspect near-duplicates, shared code, family overlap, and common source collections before splitting data.
- Separate training, validation, and testing by the unit the claim concerns. Use time-, campaign-, or family-separated tests where feasible; disclose missing timestamps and limits of the split.
- Keep report titles, actor-named paths, labels, and answer-bearing metadata out of model inputs unless the task explicitly evaluates retrieval of known attribution. For LLMs, discuss possible prior exposure to public reports and benchmarks.
- Compare actor classification against a family-recognition baseline to test whether the system mainly learns malware lineage. A shared tool or packer alone is not sufficient attribution evidence.
- Report class imbalance, per-group results, unknown-group behavior, false-attribution rates, and uncertainty. Define abstention thresholds on validation data rather than tuning them on the test set.
- Freeze data manifests, file hashes, preprocessing code, model versions, prompts, split membership, and random seeds. Corrected or repackaged copies must retain links to their original data.
- This catalog links to external resources and does not redistribute sample binaries. Each source retains its own terms and access requirements.

## References for added resources

Use the exact release citation supplied by a dataset's maintainers when conducting a study. The following references identify the catalog sources; repository titles use sentence case.

Alsaheel, A., Nan, Y., Ma, S., Yu, L., Walkup, G., Celik, Z. B., Zhang, X., & Xu, D. (2021). ATLAS: A sequence-based learning approach for attack investigation. In *30th USENIX Security Symposium (USENIX Security 21)* (pp. 3005-3022). USENIX Association. https://github.com/purseclab/ATLAS

APTnotes contributors. (n.d.). *APTnotes* [Report collection]. GitHub. Retrieved November 24, 2026, from https://github.com/aptnotes/data

Cyber Research contributors. (n.d.). *APT malware dataset* [Data set]. GitHub. https://github.com/cyber-research/APTMalware

Defense Advanced Research Projects Agency. (2020). *Transparent computing engagement 5 data release* [Data set documentation]. GitHub. https://github.com/darpa-i2o/Transparent-Computing

Five Directions. (n.d.). *Operationally transparent cyber (OpTC) data release* [Data set documentation]. GitHub. https://github.com/FiveDirections/OpTC-data

Ghosh, S. K., & contributors. (n.d.). *APT datasets* [Data set]. GitHub. https://github.com/skrghosh/apt-dataset

Kent, A. D. (2015). *Comprehensive, multi-source cybersecurity events* [Data set]. Los Alamos National Laboratory. https://doi.org/10.17021/1179829

Laurenza, G., & Lazzeretti, R. (2019). dAPTaset: A comprehensive mapping of APT-related data. In *Computer security* (pp. 217-225). Springer. https://github.com/GiuseppeLaurenza/dAPTaset

MISP Project. (n.d.). *MISP galaxy* [Knowledge base]. GitHub. Retrieved November 24, 2026, from https://github.com/MISP/misp-galaxy

MITRE. (n.d.). *Groups*. MITRE ATT&CK. Retrieved November 24, 2026, from https://attack.mitre.org/groups/

Open Threat Research Forge. (n.d.). *Security datasets* [Data set collection]. GitHub. https://github.com/OTRF/Security-Datasets

PIRAT team. (2025). *A new hope for DARPA OpTC: Correction and labeling of the dataset DARPA OpTC* [Project website]. https://correctedoptc.inria.fr/

SecPriv. (n.d.). *ADAPT: Automating APT campaign and group attribution* [Software and data documentation]. GitHub. https://github.com/SecPriv/adapt

Splunk. (2018). *Boss of the SOC (BOTS) dataset version 3* [Data set]. GitHub. https://github.com/splunk/botsv3

StreamSpot contributors. (n.d.). *StreamSpot data* [Data set]. GitHub. https://github.com/sbustreamspot/sbustreamspot-data

UBC Provenance. (n.d.). *PIDSMaker* [Software and data documentation]. GitHub. https://github.com/ubc-provenance/PIDSMaker

Yin, Z., Yan, H., Lu, H., Xiong, J., Li, X., Mei, R., & Zang, T. (2025). *APT-ClaritySet: A large-scale, high-fidelity labeled dataset for APT malware with alias normalization and graph-based deduplication* [Preprint]. arXiv. https://doi.org/10.48550/arXiv.2512.15039

## Research notes

- Record the dataset version, retrieval date, terms of use, original record ID, and underlying source. Use the publisher's recommended citation where provided.
- Code the attribution basis separately from analyst confidence. Distinguish claims of responsibility, vendor assessments, official attribution, and researcher coding. Check whether multiple reports rely on the same underlying evidence.
- For service resilience research, code disruption onset, minimum service restoration, full recovery, and the next attack wave separately. Mark missing timestamps as unknown.

See [Source and Evidence Evaluation](../Frameworks/Source-and-Evidence-Evaluation.md) and [Static PE Evidence and Attribution Comparison](../Frameworks/Static-PE-Evidence-and-Attribution-Comparison.md).
