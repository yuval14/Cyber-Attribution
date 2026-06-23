# Intro to Cyber Threat Intelligence

This page introduces Cyber Threat Intelligence (CTI) for organisations, enterprises, sectoral communities, SOC teams, incident responders, risk owners, executives, and analysts. It adapts ideas from the UK Home Office guide *Cyber Threat Intelligence: A Guide for Decision Makers and Analysts* into a general, non-government-focused operating model.

The purpose of CTI is to help defenders understand who may target the organisation, why they may do so, what capabilities and methods they may use, and what action the organisation should take as a result.

CTI is not simply a feed of indicators. It is a disciplined process that turns information about adversaries, campaigns, vulnerabilities, infrastructure, malware, tactics, techniques, and procedures into actionable intelligence for decision making, detection, prevention, response, and attribution.

## Why CTI Matters

| Need | CTI contribution |
| --- | --- |
| Better prioritisation | Helps security teams focus on threats that are relevant to the organisation, its sector, geography, assets, and business model |
| Stronger detection | Converts adversary behaviours, infrastructure, malware, and TTPs into detection logic and hunting hypotheses |
| Faster incident response | Gives responders context about likely actor goals, known tools, expected lateral movement, and containment priorities |
| Improved vulnerability management | Connects CVEs, exploited vulnerabilities, threat actor interest, sector targeting, and business exposure |
| Risk informed decisions | Translates technical threat activity into business risk, executive briefings, investment decisions, and board-level choices |
| Attribution support | Helps distinguish actor clusters, campaigns, infrastructure reuse, tool reuse, sponsorship, intent, and confidence |

## Working Definition

Cyber Threat Intelligence is the process of collecting, processing, analysing, and disseminating information about adversaries in cyberspace in order to produce actionable intelligence. Effective CTI explains adversary motivation, capability, intent, target selection, infrastructure, malware, TTPs, and likely courses of action.

A practical CTI mission statement:

> The CTI function provides actionable intelligence to the organisation's defenders and decision makers so they can prevent, detect, respond to, and learn from cyber threats.

CTI should support cyber defence. It should not replace protective monitoring, asset management, vulnerability management, incident response, or risk management.

## Core Principles

| Principle | Practical meaning |
| --- | --- |
| Threat led | Start with the organisation's threat profile, not with generic feeds |
| Actionable | Intelligence should support a decision, control change, detection, hunt, response, or risk discussion |
| Relevant | Prioritise threats that have capability, intent, and opportunity against the organisation |
| Timely | Deliver intelligence while it can still influence action |
| Accurate | Evaluate source reliability, corroboration, and confidence before dissemination |
| Audience specific | Tailor products for executives, SOC analysts, incident responders, risk owners, vulnerability teams, and engineers |
| Feedback driven | Measure whether CTI products changed decisions, controls, detections, hunts, or response actions |

## The CTI Lifecycle

The CTI lifecycle provides a repeatable model for turning raw information into intelligence products.

| Phase | Main question | Typical outputs |
| --- | --- | --- |
| Direction | What intelligence questions must be answered, and for whom? | Intelligence requirements, priority intelligence requirements, scope, collection plan |
| Collection | What data and reporting should be gathered? | Internal telemetry, incident reports, vulnerability data, OSINT, ISAC or community sharing, commercial reporting |
| Processing | How should collected material be normalized, enriched, deconflicted, scored, and prepared? | Enriched indicators, deduplicated events, source notes, relevance scoring, quality tags |
| Analysis | What does the information mean, and what should be done? | Threat assessments, actor profiles, campaign reports, detection guidance, hunt hypotheses, attribution assessments |
| Dissemination | Who needs the intelligence, in what format, and by when? | Executive briefs, SOC tickets, SIEM rules, threat alerts, vulnerability priorities, incident response briefs |
| Feedback and improvement | Did the intelligence create value? | Product metrics, stakeholder feedback, detection outcomes, lessons learned, revised requirements |

## Strategic, Operational, and Tactical CTI

| Level | Audience | Focus | Example products |
| --- | --- | --- | --- |
| Strategic CTI | Executives, board, risk committee, CISO, business owners | Business impact, sector threat landscape, adversary intent, geopolitical or market context, investment choices | Annual threat assessment, executive briefing, board risk note, sector risk update |
| Operational CTI | SOC leads, incident responders, threat hunters, security architects, vulnerability managers | Adversary campaigns, TTPs, intrusion patterns, target selection, likely attack paths | Threat actor profile, campaign report, threat hunting package, incident response context brief |
| Tactical CTI | SOC analysts, detection engineers, network defenders, endpoint teams | IOCs, malware artifacts, domains, IPs, hashes, signatures, YARA, Sigma, detection logic | Enriched IOC feed, SIEM rule, blocklist recommendation, malware note, detection update |

The levels overlap. A ransomware campaign may require an executive risk update, an operational playbook for responders, and tactical indicators for detection systems.

## CTI Use Cases

| Use case | Objective | Example intelligence needed |
| --- | --- | --- |
| Alert validation | Decide whether an event should be escalated | Indicator reputation, known campaign links, observed TTPs, asset criticality |
| Automated enrichment | Improve SIEM, SOAR, EDR, and ticket prioritisation | Indicator context, actor links, confidence, severity, sightings |
| Vulnerability prioritisation | Prioritise remediation based on exploitation and exposure | CVE exploitation evidence, KEV status, EPSS score, actor interest, affected assets |
| Threat hunting | Search proactively for hidden activity | TTPs, intrusion chains, detection hypotheses, malware behaviour, infrastructure patterns |
| Incident response support | Contain and remediate attacks with context | Actor objectives, known tools, persistence methods, exfiltration patterns, containment guidance |
| Anti-phishing and fraud defence | Improve detection and user protection | Sender infrastructure, lures, domains, kits, payloads, brand abuse patterns |
| Executive risk briefing | Inform business and investment decisions | Threat landscape, sector targeting, likely impact, control gaps, recommended decisions |
| Cyber attribution | Assess actor cluster, sponsorship, intent, and confidence | Malware lineage, infrastructure history, victimology, TTPs, geopolitical context, source evaluation |

## Building a CTI Capability

A CTI function should be built around organisational needs rather than vendor tools. A practical build sequence is:

1. Define the organisation's critical assets and business processes.
2. Identify priority threats by capability, intent, opportunity, and relevance.
3. Define intelligence requirements for each stakeholder group.
4. Start with reliable internal sources and trusted external sources.
5. Create repeatable collection, processing, analysis, and dissemination workflows.
6. Pilot open source or low friction tooling before major procurement.
7. Integrate CTI outputs into SOC, incident response, vulnerability management, threat hunting, risk, and executive reporting.
8. Measure value and revise requirements continuously.

## Collection Sources

| Source category | Examples | Notes |
| --- | --- | --- |
| Internal telemetry | SIEM, EDR, DNS, proxy, firewall, email security, cloud logs, identity logs | High relevance because it reflects actual exposure and activity in the organisation |
| Incident response reports | Internal incidents, near misses, forensic timelines, containment lessons | Strong source for recurring attacker patterns and control gaps |
| Vulnerability and asset data | CMDB, SBOM, scanner results, KEV, EPSS, exploit reporting, patch status | Supports threat-informed vulnerability management |
| OSINT | Research blogs, social media, WHOIS, passive DNS, code repositories, leak sites, public advisories | Useful but requires validation, context, and source evaluation |
| Sharing communities | ISACs, sector groups, trusted peer networks, CERT or CSIRT communities | Valuable when trust, handling rules, and feedback loops are clear |
| Commercial CTI | Vendor reports, threat feeds, managed intelligence services, malware sandboxes | Must be evaluated for relevance, quality, timeliness, and overlap with internal needs |
| Native analysis | Malware analysis, infrastructure analysis, threat hunting, clustering, adversary emulation | Creates organisation-specific intelligence and improves confidence |

## Processing and Evaluation

Collected data should be processed before analysts use it. Processing should answer four questions:

| Question | Example control |
| --- | --- |
| Is the source reliable? | Source reputation, history, access, collection method, known limitations |
| Is the information credible? | Corroboration, logic, consistency, recency, conflict with other reporting |
| Is it relevant? | Match to sector, geography, assets, technologies, threat profile, business processes |
| Is it actionable? | Clear defensive action, decision, detection, hunt, or response step |

Recommended processing fields:

| Field | Purpose |
| --- | --- |
| Source | Where the information came from |
| Date observed | When the activity or report was observed |
| Date received | When the organisation received it |
| Validity period | How long the intelligence is likely to remain useful |
| Confidence | Analyst confidence in the judgment |
| Source rating | Reliability and credibility rating when appropriate |
| Relevance | Why this matters to the organisation |
| Action | What the consumer should do |
| Owner | Team responsible for action |
| Review date | When the item should be refreshed or retired |

## Analysis

Analysis turns processed information into intelligence. Analysts should:

1. Separate observed facts from inferred judgments.
2. Use structured analytic techniques where uncertainty is high.
3. Compare multiple hypotheses before making attribution judgments.
4. Distinguish actor cluster, operator, sponsor, control, intent, and confidence.
5. Identify what evidence would strengthen or weaken the assessment.
6. Use clear confidence language and avoid overclaiming.
7. Tailor products to the decision the consumer must make.

Useful analytic methods include clustering, Key Assumptions Check, Analysis of Competing Hypotheses, Devil's Advocacy, Pre-Mortem Analysis, Diamond Model analysis, Cyber Kill Chain mapping, MITRE ATT&CK mapping, Attack Flow, and intrusion timeline reconstruction.

## Dissemination

CTI has value only when it reaches the right consumer in a usable format.

| Consumer | Preferred product | Design rule |
| --- | --- | --- |
| Executive leadership | Short risk brief or decision memo | Explain impact, likelihood, confidence, options, and recommended decisions |
| CISO and risk owners | Threat assessment, control gap analysis, roadmap input | Link threats to assets, controls, risks, and investment choices |
| SOC | Enriched IOC package, detection logic, triage note | Provide context, confidence, expiry, and false positive warnings |
| Incident response | Actor or campaign context, containment notes | Include expected behaviours, persistence, exfiltration, and likely next steps |
| Vulnerability team | Threat-informed remediation list | Link exploited vulnerabilities to assets, exposure, actors, and business impact |
| Threat hunting | Hunt package | Provide hypotheses, data sources, ATT&CK techniques, and expected telemetry |
| Legal and policy teams | Attribution and evidence summary | Separate evidence, inference, confidence, legal relevance, and uncertainty |

## CTI Product Catalogue

| Product | Level | Frequency | Purpose |
| --- | --- | --- | --- |
| Threat landscape report | Strategic | Quarterly, semiannual, or annual | Explain the threat environment relevant to the organisation |
| Executive threat brief | Strategic | As needed | Support leadership decisions during major threats or incidents |
| Sector threat update | Strategic or operational | Monthly or event driven | Summarise threats affecting the organisation's sector |
| Threat actor profile | Operational | As needed | Explain actor motivation, capability, infrastructure, TTPs, and target selection |
| Campaign report | Operational | Event driven | Describe an observed campaign and defensive implications |
| Threat hunting package | Operational | Regular or event driven | Turn CTI into searchable hypotheses |
| Incident support brief | Operational | During incident response | Provide adversary context and likely next actions |
| Enriched IOC package | Tactical | Continuous or event driven | Support detection, triage, blocking, and enrichment |
| Detection engineering note | Tactical | Event driven | Translate TTPs and indicators into durable detection logic |
| Vulnerability intelligence note | Strategic, operational, or tactical | Weekly or urgent | Prioritise patching based on exploitation, actor interest, and exposure |

## Relationship to Cyber Attribution

CTI supports attribution, but it should not collapse all evidence into a single actor label. A defensible attribution assessment should separate:

| Attribution layer | Question |
| --- | --- |
| Technical association | Which malware, infrastructure, TTPs, or tools are linked? |
| Activity cluster | Do the observations form a coherent activity set? |
| Campaign | Is the activity part of a known or emerging campaign? |
| Operator | Who likely conducted the operation? |
| Sponsor or beneficiary | Who likely directed, enabled, tolerated, or benefited from the activity? |
| Intent | What objective best explains the operation? |
| Confidence | How strong is the evidence, and what alternatives remain plausible? |

CTI products used for attribution should include evidence quality, source reliability, information credibility, assumptions, alternative hypotheses, and confidence language.

## Minimum CTI Operating Model

| Component | Minimum practice |
| --- | --- |
| Governance | Named CTI owner, defined stakeholders, approved priorities, and handling rules |
| Requirements | Documented intelligence requirements tied to business, SOC, IR, vulnerability, and risk needs |
| Collection | Approved internal and external sources with collection purpose and owner |
| Processing | Deduplication, enrichment, relevance scoring, confidence, source notes, expiry |
| Analysis | Structured methods, hypothesis testing, evidence registers, and peer review for high impact products |
| Dissemination | Product catalogue, distribution list, handling labels, action owner, feedback path |
| Tooling | Start simple; adopt TIP, MISP, STIX/TAXII, SIEM, SOAR, and automation only where requirements justify it |
| Metrics | Product usefulness, action taken, detection improved, incidents supported, vulnerabilities reprioritised |
| Improvement | Lessons learned, revised requirements, source quality review, collection gap tracking |

## CTI Starter Checklist

| Question | Yes or No |
| --- | --- |
| Have we identified our critical assets and business processes? |  |
| Do we know which threat actors or threat types are most relevant to us? |  |
| Have stakeholders defined what decisions they expect CTI to support? |  |
| Do we separate raw indicators from analysed intelligence? |  |
| Do we score source reliability, relevance, confidence, and timeliness? |  |
| Do our CTI products include recommended action and owner? |  |
| Are CTI outputs connected to SOC, IR, vulnerability management, risk, and executive reporting? |  |
| Do we review whether CTI products created measurable value? |  |
| Do we retire stale indicators and outdated assessments? |  |
| Do we document uncertainty and alternative explanations? |  |

## Common Mistakes

| Mistake | Better practice |
| --- | --- |
| Buying a threat intelligence platform before defining requirements | Define use cases, consumers, sources, workflows, and outputs first |
| Treating indicators as intelligence | Add context, relevance, confidence, source evaluation, and recommended action |
| Measuring volume instead of value | Measure decisions supported, detections improved, incidents accelerated, and risks reduced |
| Sharing the same product with every audience | Tailor strategic, operational, and tactical outputs |
| Ignoring internal telemetry | Combine external reporting with internal visibility and incident lessons |
| Over-attributing from weak signals | Separate technical similarity from operator, sponsor, intent, and confidence |
| Keeping stale indicators forever | Assign retention periods based on relevance, confidence, sightings, and operational value |
| Reporting without feedback | Maintain a feedback loop with every major consumer group |

## Recommended Metrics

| Metric | Value measured |
| --- | --- |
| Number of intelligence requirements answered | Alignment to stakeholder needs |
| Percentage of CTI products with recorded action taken | Operational usefulness |
| Detection rules created or improved from CTI | SOC value |
| Threat hunts initiated and findings generated | Proactive defence value |
| Vulnerabilities reprioritised due to threat intelligence | Vulnerability management value |
| Incidents where CTI reduced investigation time | Incident response value |
| Executive decisions informed by CTI | Strategic value |
| Source quality review outcomes | Collection quality |
| Indicator expiry compliance | Reduction of stale or noisy technical intelligence |
| Feedback score by product type | Product improvement |

## Example CTI Product Template

| Field | Content |
| --- | --- |
| Title | Clear description of the threat, actor, campaign, vulnerability, or incident |
| Audience | Executive, SOC, IR, vulnerability team, risk owner, legal, or policy |
| Key judgment | Main analytic conclusion in one or two sentences |
| Confidence | High, moderate, or low, with explanation |
| Why it matters | Relevance to the organisation |
| Evidence | Observations, sources, and corroboration |
| Assessment | Meaning, implications, and likely next developments |
| Recommended action | Concrete defensive or decision action |
| Owner | Team responsible for action |
| Expiry or review date | When to refresh, retire, or reassess |
| Alternatives and gaps | What remains uncertain or could change the assessment |

## References

Caltagirone, S., Pendergast, A., & Betz, C. (2013). *The diamond model of intrusion analysis*. ThreatConnect.

Home Office Cyber Security Programme. (2019). *Cyber threat intelligence: A guide for decision makers and analysts* (Version 2.0). UK Home Office. https://hodigital.blog.gov.uk/wp-content/uploads/sites/161/2020/03/Cyber-Threat-Intelligence-A-Guide-For-Decision-Makers-and-Analysts-v2.0.pdf

MITRE. (2024). *MITRE ATT&CK*. https://attack.mitre.org/

OASIS Open. (2021). *STIX Version 2.1*. https://docs.oasis-open.org/cti/stix/v2.1/stix-v2.1.html

OASIS Open. (2021). *TAXII Version 2.1*. https://docs.oasis-open.org/cti/taxii/v2.1/taxii-v2.1.html
