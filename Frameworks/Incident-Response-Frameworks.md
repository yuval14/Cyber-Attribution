# Incident Response Frameworks

This page provides a practical reference for common incident response frameworks and guidance sources that can support cyber attribution work. Incident response and attribution are not the same activity. Incident response focuses on detection, containment, eradication, recovery, evidence preservation, and lessons learned. Attribution uses the evidence and context produced during response to assess actor identity, sponsorship, intent, control, and confidence.

Use this page as a map of frameworks. Do not treat it as a substitute for legal advice, regulatory reporting requirements, forensic procedure, or organization specific incident response plans.

## Why Incident Response Matters for Cyber Attribution

Incident response quality directly affects attribution quality. Poor logging, weak evidence handling, unmanaged containment, or undocumented remediation can destroy the evidentiary trail needed to distinguish between a state actor, contractor, proxy, criminal reuse, shared infrastructure, false flag, or opportunistic exploitation.

A good incident response process should therefore preserve the following attribution relevant outputs:

| Output | Attribution value |
|---|---|
| Timeline of activity | Supports campaign reconstruction, dwell time analysis, and operational tempo assessment |
| Initial access evidence | Helps distinguish phishing, vulnerability exploitation, credential misuse, supply chain compromise, and insider activity |
| Malware and tooling artifacts | Supports technical clustering, tool lineage analysis, and capability assessment |
| Infrastructure evidence | Supports domain, IP, TLS, ASN, hosting, passive DNS, and infrastructure reuse analysis |
| Endpoint and identity logs | Supports hands on keyboard analysis, lateral movement reconstruction, and operator behavior assessment |
| Containment and eradication notes | Helps determine what was observed before the adversary was displaced |
| Lessons learned | Converts incident findings into control validation, resilience improvement, and future collection requirements |

## Summary of Frameworks and Guidance

| No. | Framework or guidance | Main orientation | Typical phases or focus areas | Best use |
|---:|---|---|---|---|
| 1 | SANS Incident Response Framework / PICERL | Practitioner incident handling lifecycle | Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned | SOC and incident handler workflow |
| 2 | NIST SP 800-61 Rev. 3 | Risk managed incident response profile aligned to CSF 2.0 | Identify, Protect, Detect, Respond, Recover, and governance considerations | Enterprise IR program design and improvement |
| 3 | ISO/IEC 27035 | Information security incident management standard | Prepare, detect, report, assess, respond, and learn | ISMS aligned incident management process |
| 4 | ENISA CSIRT Maturity Framework | CSIRT capability maturity | Governance, mandate, services, people, processes, tools, cooperation, and continuous improvement | National, sectoral, and organizational CSIRT maturity assessment |
| 5 | CISA Federal Cybersecurity Incident and Vulnerability Response Playbooks | U.S. federal operational playbooks | Incident response and vulnerability response actions | Playbook driven response and vulnerability coordination |
| 6 | ENISA Good Practice Guide for Incident Management | CSIRT and incident handling good practice | Incident handling, reporting, coordination, and operational practices | CERT/CSIRT procedure development |
| 7 | CREST Cyber Security Incident Response Guide | Commercial and organizational incident management | Preparation, response capability, specialist support, and recovery considerations | Building or procuring professional IR capability |
| 8 | UK NCSC Incident Management Guidance | Practical organizational response capability | Plan, build, develop, and maintain incident response capability | Building IR capability across people, process, and technology |
| 9 | Canadian Centre for Cyber Security IR Plan Guidance | Practical incident response plan guidance | Preparation, detection and analysis, containment, eradication, recovery, post incident activity | Developing and testing an IR plan |

## 1. SANS Incident Response Framework / PICERL

### Purpose

The SANS model is a widely used practitioner lifecycle for incident handlers. It is often remembered as PICERL:

| Phase | Purpose | Attribution relevant output |
|---|---|---|
| Preparation | Establish policy, tooling, logging, roles, access, communication paths, and exercises | Known baseline, evidence sources, response authority, and collection readiness |
| Identification | Detect, validate, classify, and scope the incident | Initial timeline, affected assets, indicators, and incident category |
| Containment | Limit damage and prevent further adversary action | Scope boundaries, affected systems, preserved images, and adversary behavior before displacement |
| Eradication | Remove malicious artifacts and close root causes | Malware samples, persistence mechanisms, exploited vulnerabilities, and credential misuse evidence |
| Recovery | Restore systems and monitor for recurrence | Validation results, residual indicators, and evidence of re-entry attempts |
| Lessons Learned | Review root causes and improve controls | Control gaps, analytic lessons, and future collection requirements |

### When to Use

Use PICERL as the operational spine for SOC and incident handler activity. It is simple, memorable, and well suited for internal playbooks, tabletop exercises, and after action reviews.

## 2. NIST SP 800-61 Rev. 3

### Purpose

NIST SP 800-61 Rev. 3 reframes incident response as part of cybersecurity risk management and aligns incident response recommendations with the NIST Cybersecurity Framework 2.0. It supersedes Rev. 2 and is better suited for organizations that want incident response embedded across the full risk lifecycle, not only during active response.

### Practical Use

| CSF 2.0 function | Incident response meaning |
|---|---|
| Govern | Define authorities, risk appetite, policy, roles, reporting obligations, and oversight |
| Identify | Understand assets, dependencies, business impact, critical services, and threat exposure |
| Protect | Reduce incident likelihood and impact through controls, hardening, training, backup, and resilience |
| Detect | Maintain telemetry, alerting, triage, and analytic capability |
| Respond | Coordinate containment, communication, technical response, evidence handling, and decision support |
| Recover | Restore services, validate integrity, communicate status, and improve resilience |

### Attribution Note

NIST Rev. 3 is especially useful for ensuring that incident response evidence, risk decisions, business impact, and recovery actions are tied to governance and enterprise risk management.

## 3. ISO/IEC 27035: Information Security Incident Management

### Purpose

ISO/IEC 27035 provides a structured approach to information security incident management. It is useful for organizations operating an ISO/IEC 27001 aligned Information Security Management System (ISMS) or seeking a standard based process for preparing for, detecting, reporting, assessing, responding to, and learning from incidents.

### Practical Use

| Use case | Value |
|---|---|
| ISMS integration | Aligns incident management with policy, risk, audit, and continual improvement |
| Incident classification | Helps define what counts as an information security event or incident |
| Reporting and escalation | Supports consistent reporting, assessment, and escalation procedures |
| Lessons learned | Links incidents to corrective action and management review |

## 4. ENISA CSIRT Maturity Framework

### Purpose

The ENISA CSIRT Maturity Framework supports assessment and improvement of CSIRT capability. It is useful for national CSIRTs, sectoral CSIRTs, government teams, and mature enterprise teams that need to evaluate capability beyond a single incident lifecycle.

### Capability Areas

| Area | Example maturity questions |
|---|---|
| Mandate and governance | Is the CSIRT mandate clear, approved, resourced, and understood by stakeholders? |
| Services | Are incident handling, vulnerability coordination, alerts, advisories, malware analysis, and situational awareness services defined? |
| Processes | Are intake, triage, escalation, coordination, closure, and lessons learned repeatable? |
| People | Are roles, training, on call models, and surge capacity defined? |
| Tools and data | Are case management, telemetry, enrichment, evidence handling, and reporting tools sufficient? |
| Cooperation | Are trusted relationships, information sharing channels, and cross border coordination mechanisms in place? |
| Improvement | Are exercises, metrics, audits, and after action reviews used to improve capability? |

### Attribution Note

CSIRT maturity affects attribution because mature teams produce more consistent evidence, cleaner timelines, better source records, and more reliable coordination with external partners.

## 5. CISA Federal Cybersecurity Incident and Vulnerability Response Playbooks

### Purpose

The CISA federal playbooks provide standardized operational steps for incident response and vulnerability response. They were designed for U.S. federal civilian executive branch agencies, but the structure is useful for any organization that wants consistent playbook driven action.

### Practical Use

| Playbook area | Use |
|---|---|
| Incident response | Standardize preparation, detection, analysis, containment, eradication, recovery, coordination, and post incident activity |
| Vulnerability response | Standardize vulnerability identification, reporting, prioritization, remediation, validation, and communication |
| Stakeholder coordination | Clarify who must be notified, when, and with what information |
| Repeatability | Convert response expectations into checklists and repeatable action steps |

### Attribution Note

The vulnerability response playbook is especially important when attribution depends on whether an intrusion resulted from opportunistic exploitation, targeted exploitation, supply chain compromise, or reuse of a known exposed weakness.

## 6. ENISA Good Practice Guide for Incident Management

### Purpose

ENISA's Good Practice Guide for Incident Management supports CERT and CSIRT teams with practical incident management guidance, especially for network and information security incidents.

### Practical Use

| Use case | Value |
|---|---|
| CERT/CSIRT procedure development | Provides a practical baseline for incident handling processes |
| Reporting and coordination | Supports structured information exchange and coordination between teams |
| Operational discipline | Encourages repeatable handling, documentation, escalation, and closure |
| Training | Useful for building exercises and onboarding analysts |

## 7. CREST Cyber Security Incident Response Guide

### Purpose

CREST guidance is useful for organizations building, assessing, or procuring professional incident response capability. It is especially relevant where organizations depend on external incident response providers, legal counsel, forensic suppliers, communications advisors, or cyber insurance panels.

### Practical Use

| Area | Value |
|---|---|
| Readiness | Helps organizations prepare people, processes, retainers, evidence handling, and communication channels before an incident |
| Specialist support | Helps define when external forensic, legal, crisis communications, or malware analysis support is needed |
| Procurement | Helps buyers assess professional incident response services and capability requirements |
| Exercise design | Supports tabletop and simulation planning |

## 8. UK NCSC Incident Management Guidance

### Purpose

The UK NCSC incident management guidance focuses on building an effective cyber incident response capability. It organizes guidance around planning response processes, building a cyber security incident response team, developing technical capabilities, and maintaining the capability over time.

### Practical Use

| Area | Value |
|---|---|
| Plan | Define incident response processes, escalation, communications, and decision points |
| Build | Establish the incident response team, roles, responsibilities, and skill sets |
| Develop | Build technical response capability, including evidence, logs, tooling, and analysis |
| Maintain | Exercise, review, update, and improve the capability |

### Attribution Note

NCSC's people, process, and technology framing is useful because attribution failures often come from organizational gaps, not only technical gaps.

## 9. Canadian Centre for Cyber Security IR Plan Guidance

### Purpose

The Canadian Centre for Cyber Security guidance provides practical steps for developing an incident response plan. It emphasizes simple and flexible planning, annual testing and revision, defined roles, communications, and lifecycle based response.

### Practical Use

| Phase | Practical focus |
|---|---|
| Preparation | Management commitment, risk assessment, likely incident types, policies, backups, patching, team roles, communications, and exercises |
| Detection and analysis | Monitoring, reporting, analysis, prioritization, and activation of the IR plan |
| Containment | Reduce business impact and isolate affected systems or access paths where required |
| Eradication | Root cause analysis, removal of malicious content, hardening, patching, and closing residual attack vectors |
| Recovery | Restore and validate affected systems, monitor stability, and update training or procedures |
| Post incident activities | Review root cause, document lessons learned, and improve detection and prevention |

## Framework Selection Guide

| Organizational need | Recommended starting point |
|---|---|
| SOC needs a simple operational lifecycle | SANS PICERL |
| Enterprise wants IR embedded into risk management | NIST SP 800-61 Rev. 3 |
| Organization operates an ISO aligned ISMS | ISO/IEC 27035 |
| National or sectoral CSIRT wants capability maturity assessment | ENISA CSIRT Maturity Framework |
| Government agency needs repeatable incident and vulnerability playbooks | CISA Federal Playbooks |
| CERT/CSIRT needs practical incident handling guidance | ENISA Good Practice Guide |
| Organization needs to procure external IR services | CREST guidance |
| Large organization needs people, process, and technology capability guidance | UK NCSC Incident Management Guidance |
| Small or medium organization needs a practical IR plan | Canadian Centre for Cyber Security guidance |

## Unified Incident Response Lifecycle for Repository Use

For repository templates and incident notes, use the following simplified lifecycle unless a specific framework is required:

| Stage | Core question | Required outputs |
|---|---|---|
| 1. Prepare | Are we ready to respond and preserve evidence? | IR policy, roles, contacts, evidence procedure, logging baseline, playbooks, exercises |
| 2. Detect and identify | What happened, where, when, and how confident are we? | Alert record, incident classification, affected assets, initial indicators, triage decision |
| 3. Analyze and scope | What is the full extent of compromise? | Timeline, root cause hypothesis, impacted accounts, systems, data, infrastructure, malware, and TTPs |
| 4. Contain | How do we limit damage while preserving evidence? | Containment actions, preservation decisions, business impact notes, adversary behavior observations |
| 5. Eradicate | How do we remove the adversary and close attack paths? | Malware removal, credential reset, vulnerability remediation, persistence removal, hardening actions |
| 6. Recover | How do we safely restore trusted operations? | Restore plan, validation checks, monitoring criteria, rollback options, stakeholder updates |
| 7. Learn and improve | What must change after the incident? | Lessons learned, control gaps, detection improvements, tabletop updates, attribution evidence gaps |

## Incident Response and Attribution Interface

| IR activity | Attribution risk if weak | Good practice |
|---|---|---|
| Log collection | Timeline gaps and weak confidence | Preserve raw logs, normalized events, time zone notes, and collection scope |
| Evidence handling | Loss of forensic value | Use documented chain of custody and controlled access |
| Malware handling | Tool lineage cannot be validated | Store hashes, metadata, sample source, analysis notes, and sandbox limitations |
| Infrastructure analysis | Over attribution to reused infrastructure | Record passive DNS, registrar, ASN, hosting, TLS, and alternative explanations |
| Identity analysis | Operator behavior cannot be separated from automated activity | Preserve authentication logs, MFA events, tokens, device IDs, and administrative actions |
| Communications | Premature public attribution | Separate incident facts, technical assessment, business impact, legal notification, and attribution judgment |
| Lessons learned | Same evidence gaps repeat | Convert failures into new logging, telemetry, collection, and analytic requirements |

## Minimum Incident Response Plan Template

| Section | Content |
|---|---|
| Purpose and scope | What the IR plan covers, including IT, cloud, OT, suppliers, and third party services |
| Authorities | Who can declare an incident, isolate systems, approve downtime, engage external parties, and notify regulators |
| Roles and contacts | Incident commander, SOC, IT, cloud, legal, privacy, communications, business owners, executive sponsor, external responders |
| Severity levels | Impact based severity with escalation thresholds and decision rights |
| Evidence handling | Collection, preservation, chain of custody, retention, privacy, and legal constraints |
| Communications | Internal updates, executive briefings, customer notice, regulator notice, media handling, law enforcement contact |
| Playbooks | Ransomware, data theft, business email compromise, cloud compromise, vulnerability exploitation, insider threat, DDoS, supply chain compromise |
| Recovery | Backup validation, restoration order, integrity checks, monitoring, and return to service criteria |
| Post incident review | Root cause, control failures, timeline, cost, metrics, lessons learned, and remediation plan |
| Exercise schedule | Tabletop, technical simulation, executive exercise, supplier exercise, and annual review |

## Recommended Repository Cross Links

Use this page together with:

| Related page | How to use it |
|---|---|
| [Cyber Attribution Frameworks](Cyber-Attribution-Frameworks.md) | Connect incident evidence to attribution models, actor levels, sponsorship, and confidence |
| [Investigation Techniques](Investigation-Techniques.md) | Apply SATs, ACH, WEP, LCA, and Admiralty/NATO source evaluation to incident evidence |
| [Influence Operations (IIO) Attribution](Influence%20Operations-(IIO)-Attribution.md) | Connect cyber incident response with influence operations when incidents have narrative or cognitive effects |

## References

Canadian Centre for Cyber Security. (2026). *Developing your incident response plan (ITSAP.40.003)*. Government of Canada. https://www.cyber.gc.ca/en/guidance/developing-your-incident-response-plan-itsap40003

CREST. (2014). *Cyber security incident response guide*. CREST.

Cybersecurity and Infrastructure Security Agency. (2021). *Federal government cybersecurity incident and vulnerability response playbooks*. U.S. Department of Homeland Security. https://www.cisa.gov/resources-tools/resources/federal-government-cybersecurity-incident-and-vulnerability-response-playbooks

European Union Agency for Cybersecurity. (2010). *Good practice guide for incident management*. ENISA. https://www.enisa.europa.eu/publications/good-practice-guide-for-incident-management

European Union Agency for Cybersecurity. (n.d.). *CSIRT maturity framework*. ENISA.

International Organization for Standardization. (2023). *ISO/IEC 27035-1:2023 Information technology — Information security incident management — Part 1: Principles and process*. https://www.iso.org/standard/78973.html

Kral, P. (2011). *The incident handler's handbook*. SANS Institute. https://www.sans.org/white-papers/33901/

National Cyber Security Centre. (2019). *Incident management*. https://www.ncsc.gov.uk/collection/incident-management

National Institute of Standards and Technology. (2025). *Incident response recommendations and considerations for cybersecurity risk management: A CSF 2.0 community profile* (NIST Special Publication 800-61 Rev. 3). https://doi.org/10.6028/NIST.SP.800-61r3
