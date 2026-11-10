# Research Data Library

A catalog of public cyber incident sources and attribution benchmarks for reproducible research.

## Credit and terms of use

Credit belongs to the dataset creators, publishers, and maintainers identified below. The respective dataset owners and maintainers are responsible for the accuracy and availability of their data. Access to and use of each source are subject to its owner's applicable terms of use, license, and access conditions. Consult the original source before downloading, reusing, or redistributing data, and cite the specific release or record used.

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

Suggested citation for the Japan dataset release reviewed: Ketchum, M. (2026). *Japan Cybersecurity Tracker: Disclosed cyber incidents affecting organizations in Japan* [Data set, version of 2026-11-06]. MKUltraman. https://www.mkultraman.com/japan-cybersecurity-tracker/dataset/

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

## Static malware research datasets

| Source | Credit | Coverage and access | Research use and limitations |
| --- | --- | --- | --- |
| [EMBER 2018](https://github.com/elastic/ember) | Hyrum S. Anderson and Phil Roth. Hosted by Elastic | Version 2 static features extracted from 1 million Windows PE files scanned in or before 2018. Downloadable feature archive | Historical baseline for static malware detection. The feature archive supports feature-based experiments. Evaluating YARA rules directly requires separately obtained samples. |
| [EMBER2024](https://github.com/FutureComputing4AI/EMBER2024) | Robert J. Joyce, Gideon Miller, Phil Roth, Richard Zak, Elliott Zaresky-Williams, Hyrum Anderson, Edward Raff, and James Holt | Downloadable features and labels for approximately 3.2 million benign and malicious files across Win32, Win64, .NET, APK, ELF, and PDF | Supports detection, family classification, and behavior prediction. Restrict to Windows PE for PE-only comparisons and align feature definitions across releases. |
| [MOTIF](https://github.com/boozallen/MOTIF) | Robert J. Joyce and coauthors. Hosted by Booz Allen Hamilton | 3,095 disarmed Windows PE malware samples from 454 families. Downloadable samples, JSONL metadata, EMBER v2 features, and family aliases | Supports family classification and alias analysis using labels curated from threat intelligence. Account for modified PE header fields when extracting features from the disarmed samples. |
| [SOREL-20M](https://github.com/sophos/SOREL-20M) | Sophos AI and ReversingLabs | Approximately 20 million benign and malicious Windows PE records with EMBER v2 features, labels, and metadata. Downloadable data include disarmed malware binaries | Large-scale static detection and false-positive evaluation. Account for modified PE header fields when extracting features from disarmed binaries. |
| [BODMAS](https://whyisyoung.github.io/BODMAS/) | Limin Yang and the BODMAS project collaborators | 57,293 malicious and 77,142 benign PE samples, with 581 malware families and first-seen metadata. Features and metadata are downloadable. Access to malware binaries is by request | Family classification and temporal evaluation. Use first-seen dates to build chronological splits. |
| [MalDICT](https://github.com/rjjoyce/MalDICT) | Robert J. Joyce and the MalDICT paper coauthors | Malware datasets with behavior, platform, vulnerability exploitation, and packer tags. The project provides static features and disarmed PE downloads | Test whether static features reflect shared capabilities or packers. Check for hash overlap with VirusShare, which supplies the source samples. |
| [Microsoft BIG 2015](https://www.kaggle.com/competitions/malware-classification/data) | Microsoft, hosted by Kaggle | Nine malware families. Competition data include hexadecimal byte dumps with PE headers removed and assembly listings | Historical baseline for family classification using bytes or opcodes. Full PE header analysis and structure-dependent YARA evaluation require other samples. |

Maliciousness, malware family, and threat actor identity are separate labels. Use independent campaign evidence when evaluating actor attribution.

## Research notes

- Record the dataset version, retrieval date, terms of use, original record ID, and underlying source. Use the publisher's recommended citation where provided.
- Code the attribution basis separately from analyst confidence. Distinguish claims of responsibility, vendor assessments, official attribution, and researcher coding. Check whether multiple reports rely on the same underlying evidence.
- For service resilience research, code disruption onset, minimum service restoration, full recovery, and the next attack wave separately. Mark missing timestamps as unknown.

See [Source and Evidence Evaluation](../Frameworks/Source-and-Evidence-Evaluation.md) and [Static PE Evidence and Attribution Comparison](../Frameworks/Static-PE-Evidence-and-Attribution-Comparison.md).
