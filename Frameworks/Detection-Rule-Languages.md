# Detection Rule Languages, Formats, and Indicators: Sigma, YARA, YARA-L, Snort, IOC, IOA, and IoPC

This page introduces widely used detection rule languages and practical detection indicator categories that support cyber threat intelligence, detection engineering, incident response, threat hunting, AI security monitoring, and cyber attribution analysis:

1. Sigma
2. YARA
3. YARA-L
4. Snort
5. Indicators of Compromise (IOC)
6. Indicators of Attack (IOA)
7. Indicators of Prompt Compromise (IoPC)

The purpose is not to treat a rule match or indicator match as attribution by itself. Detection rules and indicators help analysts capture repeatable evidence patterns, test hypotheses, preserve analytic logic, and improve visibility across telemetry sources. Attribution still requires source evaluation, alternative hypotheses, confidence language, and corroboration across technical, operational, strategic, and legal layers.

## Source Note

The YARA security project is documented through the VirusTotal YARA project site and YARA documentation. The domain `yara.com` is not the YARA detection language documentation site.

## Quick Comparison

| Language, format, or indicator type | Primary data domain | Main use | Typical user | Attribution value | Main limitation |
| --- | --- | --- | --- | --- | --- |
| Sigma | Logs and event telemetry | Portable SIEM and XDR detection logic | Detection engineers, SOC analysts, threat hunters | Captures behavioral patterns and maps activity to TTPs across platforms | Requires backend conversion and field mapping |
| YARA | Files, malware samples, byte patterns, strings, memory scanning | Malware identification and classification | Malware analysts, reverse engineers, CTI analysts | Links samples by code, strings, configuration, packer artifacts, and family traits | Poorly written rules can overfit, under-detect, or create false positives |
| YARA-L | Google Security Operations telemetry using UDM fields | Search, dashboards, rule-based threat detection, and event correlation | Google SecOps analysts and detection engineers | Correlates activity across normalized security events and supports multi-event logic | Platform specific to Google SecOps and dependent on data ingestion quality |
| Snort | Network packets and protocol traffic | IDS and IPS alerting or blocking | Network defenders, SOC, IDS/IPS engineers | Detects exploit attempts, C2 traffic, scans, payload patterns, and network tradecraft | Packet visibility, encryption, tuning, and protocol coverage shape effectiveness |
| IOC | Observable artifacts across endpoint, network, identity, cloud, and malware evidence | Detect or confirm activity that may already have occurred | SOC analysts, incident responders, CTI analysts | Links incidents through repeated infrastructure, files, accounts, or malware artifacts | Can be short-lived, reused, spoofed, purchased, or planted |
| IOA | Behavioral signals and attack sequences | Detect an attack attempt or activity in progress | Threat hunters, detection engineers, SOC analysts | Captures adversary behavior and tradecraft more durably than simple artifacts | Requires telemetry, baselining, and tuning to avoid false positives |
| IoPC | AI prompt, context, retrieval, tool-call, memory, output, and agent workflow signals | Detect prompt injection, indirect prompt injection, context manipulation, or unauthorized tool use | AI security teams, SOC analysts, application security teams | Helps distinguish AI workflow compromise from traditional endpoint or network compromise | Emerging repository term; not yet a mature global standard |

## Detection Coverage by Evidence Type

| Evidence type | Sigma | YARA | YARA-L | Snort | IOC | IOA | IoPC |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Endpoint logs | High | Low | High, if ingested and normalized | Low | High | High | Medium |
| SIEM telemetry | High | Low | High in Google SecOps | Low to medium, if network alerts are ingested | High | High | Medium |
| Malware files | Low | High | Medium, if file hashes or metadata are in telemetry | Low | High | Low | Low |
| Memory artifacts | Low | High | Low to medium | Low | Medium | Medium | Low |
| Network packets | Low | Low | Medium, if packet-derived telemetry is ingested | High | High | Medium | Low |
| Cloud and identity logs | High | Low | High, if normalized into UDM | Low | High | High | Medium |
| AI prompts, RAG context, tool calls, and agent logs | Medium, if logged | Low | Medium to high, if ingested | Low | Medium | Medium | High |
| Threat hunting | High | High | High | Medium | High | High | High |
| Preventive blocking | Usually indirect | Usually indirect | Usually indirect | High when deployed inline as IPS | Sometimes | Sometimes | Sometimes through AI guardrails and tool controls |

## Detection Indicator Types

### Indicators of Compromise (IOC)

Indicators of Compromise are observable artifacts that suggest malicious activity or compromise may have occurred. They are commonly used in incident response, threat hunting, detection engineering, malware analysis, and CTI sharing.

| IOC type | Examples | Practical use |
| --- | --- | --- |
| File | Hashes, filenames, file paths, malware family labels | Malware triage, endpoint search, quarantine, retro-hunt |
| Network | IP addresses, domains, URLs, DNS records, user agents | Network detection, blocking, enrichment, infrastructure clustering |
| Host | Registry keys, scheduled tasks, services, mutexes, persistence artifacts | Endpoint investigation and containment |
| Identity | Suspicious accounts, token use, impossible travel, MFA fatigue patterns | Account compromise investigation |
| Cloud | API keys, service account changes, cloud audit events, unusual role assignments | Cloud compromise detection and response |

IOCs can support attribution when they connect incidents through infrastructure, tooling, malware lineage, or repeated operational choices. They should not be treated as actor identity by themselves because IOCs can be reused, shared, spoofed, purchased, or planted.

### Indicators of Attack (IOA)

Indicators of Attack are behavior-oriented signals that suggest an attack is being attempted or is in progress. They focus on adversary behavior rather than only post-compromise artifacts. In practice, IOAs are often mapped to MITRE ATT&CK tactics, techniques, procedures, data sources, and detection analytics.

| IOA type | Examples | Practical use |
| --- | --- | --- |
| Execution behavior | Suspicious PowerShell, script interpreter abuse, unusual child processes | Detect active intrusion behavior |
| Credential behavior | Password spraying, token abuse, credential dumping patterns | Detect identity-focused attack activity |
| Lateral movement | Remote service abuse, suspicious admin share use, unusual RDP or SSH flows | Detect movement before final objectives |
| Defense evasion | Logging disabled, EDR tampering, suspicious process injection | Detect attempts to avoid visibility |
| Exfiltration behavior | Staging, compression, unusual outbound transfer, cloud storage misuse | Detect data theft preparation or execution |

IOAs can be more useful than simple IOCs for attribution because they capture tradecraft and operational habits. They are still not decisive alone. Behavioural overlap can reflect shared tools, public playbooks, emulation, or false flag activity.

### Indicators of Prompt Compromise (IoPC)

Indicators of Prompt Compromise are AI-specific signals suggesting that a prompt, retrieved context, connector input, model output, tool call, memory item, or agent workflow may have been manipulated. IoPC is an emerging repository term rather than a mature global standard. Use it to structure evidence for prompt injection, indirect prompt injection, context poisoning, unauthorized tool use, or instruction hierarchy manipulation.

| IoPC type | Examples | Practical use |
| --- | --- | --- |
| Prompt content | Hidden instructions, jailbreak strings, instruction override attempts, role confusion language | Detect direct prompt injection and policy bypass attempts |
| Retrieved context | Malicious instructions embedded in documents, tickets, webpages, emails, repositories, or knowledge base content | Detect indirect prompt injection and RAG poisoning |
| Tool invocation | Unexpected tool call, unusual connector access, unauthorized file or email action, unexplained privilege use | Detect agent workflow manipulation |
| Output behavior | Sudden refusal bypass, data exfiltration wording, hidden instruction compliance, unexplained change in task objective | Detect compromised model response behavior |
| Memory or state | Unexpected memory insertion, poisoned task state, modified system-like instruction, persistence across sessions | Detect durable prompt or context compromise |
| Audit signal | Prompt and output mismatch, missing user approval, abnormal action chain, failed guardrail event | Support investigation and containment |

IoPC can help distinguish an AI-system compromise path from a traditional endpoint or network compromise path. It rarely attributes an actor by itself. For attribution, combine IoPC with access logs, identity evidence, infrastructure, malware, TTPs, victimology, and campaign context.

## 1. Sigma

### Purpose

Sigma is a generic and open signature format for log and SIEM detections. It lets analysts describe suspicious or malicious log events in a platform independent way, then convert rules into backend specific queries for tools such as SIEM, XDR, data lake, and log analytics platforms.

Sigma is best suited for:

1. Behavior based detections in logs.
2. Threat hunting logic that should be shared across tools.
3. Detection coverage mapped to MITRE ATT&CK techniques.
4. Translating CTI reporting into operational detection logic.
5. Preserving detection logic in a readable, reviewable format.

### Typical Rule Elements

| Element | Purpose |
| --- | --- |
| `title` | Human readable rule name |
| `id` | Stable unique identifier |
| `status` | Rule maturity, such as experimental, test, or stable |
| `description` | What the rule detects and why it matters |
| `author` | Rule owner or contributor |
| `date` and `modified` | Lifecycle tracking |
| `logsource` | Product, service, category, and telemetry source |
| `detection` | Selection logic and condition |
| `falsepositives` | Known benign explanations |
| `level` | Alert severity |
| `tags` | ATT&CK, campaign, malware family, or control mappings |

### Attribution Use

Sigma rules can support attribution by capturing behavioral patterns that are more durable than single indicators. Examples include service creation patterns, suspicious PowerShell behavior, credential access, persistence, lateral movement, cloud control plane activity, and repeated hands on keyboard tradecraft.

Sigma should not be used to claim actor identity on its own. A Sigma match usually supports a TTP, tool, or behavior finding. It becomes stronger for attribution when combined with malware analysis, infrastructure clustering, victimology, timing, source reliability, and competing hypothesis analysis.

### Minimal Sigma Skeleton

```yaml
title: Suspicious Example Activity
id: 00000000-0000-0000-0000-000000000000
status: test
description: Detects an example suspicious behavior in log telemetry.
author: Your Name
date: 2026/06/24
logsource:
  product: windows
  category: process_creation
detection:
  selection:
    Image|endswith: "\\example.exe"
  condition: selection
falsepositives:
  - Administrative testing
level: medium
tags:
  - attack.execution
```

## 2. YARA

### Purpose

YARA is used to identify and classify malware samples, files, or memory content based on textual patterns, binary patterns, and Boolean conditions. A YARA rule usually contains metadata, strings, and a condition that determines when the rule matches.

YARA is best suited for:

1. Malware family identification.
2. File triage and malware repository scanning.
3. Memory scanning and incident response analysis.
4. Detecting code fragments, configuration strings, packer traits, and embedded artifacts.
5. Comparing related samples during attribution analysis.

### Typical Rule Elements

| Element | Purpose |
| --- | --- |
| Rule name | Identifies the rule and detection intent |
| Tags | Classifies malware family, campaign, technique, or confidence |
| `meta` | Description, author, date, reference, hash, family, version, caveats |
| `strings` | Text strings, hex patterns, regular expressions, and modifiers |
| `condition` | Boolean logic that defines a match |
| Modules | Optional structured parsing for PE, ELF, hash, math, dotnet, and other data |

### Attribution Use

YARA helps analysts link samples through malware code, embedded strings, compiler traces, configuration structures, protocol constants, payload markers, and actor mistakes. It is especially useful when hash based detection fails because the adversary modifies binaries.

YARA matches should be interpreted carefully. A match can indicate malware family, tool reuse, code reuse, builder reuse, or copied artifacts. It does not automatically prove that the same operator or sponsor is responsible for every matching sample.

### Minimal YARA Skeleton

```yara
rule Example_Malware_Family
{
    meta:
        description = "Example malware family detection"
        author = "Your Name"
        date = "2026-06-24"
        confidence = "medium"

    strings:
        $s1 = "example_config_marker" ascii wide
        $h1 = { 6A 40 68 ?? ?? ?? ?? 6A 14 }

    condition:
        uint16(0) == 0x5A4D and 1 of them
}
```

## 3. YARA-L

### Purpose

YARA-L 2.0 is Google Security Operations' structured query language for search, dashboards, and rule based threat detection. It uses normalized security telemetry, including Unified Data Model fields, to express filters, joins, aggregations, outcomes, and multi-event correlation.

YARA-L is best suited for:

1. Searching normalized security telemetry in Google SecOps.
2. Building detections from events, matches, outcomes, and conditions.
3. Correlating multiple events over a time window.
4. Producing dashboard queries and detection analytics.
5. Creating context aware detections using enriched data.

### Typical Rule Sections

| Section | Purpose |
| --- | --- |
| `meta` | Rule name, author, description, severity, and management metadata |
| `events` | Defines and filters event sources using UDM fields and event variables |
| `match` | Groups events or correlates events over a time window |
| `outcome` | Calculates values, aggregates, and alert context |
| `condition` | Defines which event variables or logic cause the rule to trigger |
| `options` | Optional rule execution controls |

### Attribution Use

YARA-L supports attribution analysis by correlating normalized event streams. It can connect process launches, file hashes, authentication activity, cloud actions, endpoint events, identity context, and AI workflow telemetry if it is ingested. This makes it useful for building an operational timeline and testing whether a suspected TTP cluster appears across multiple victims or environments.

YARA-L should be treated as platform specific detection logic. Its strength depends on telemetry ingestion, parser quality, UDM normalization, and the analyst's ability to separate telemetry gaps from true absence of activity.

### Minimal YARA-L Skeleton

```text
rule Example_Multi_Event_Detection {
  meta:
    author = "Your Name"
    description = "Example multi-event detection"
    severity = "Medium"

  events:
    $e1.metadata.event_type = "PROCESS_LAUNCH"
    $e2.metadata.event_type = "USER_LOGIN"
    $user = $e1.principal.user.userid
    $user = $e2.principal.user.userid

  match:
    $user over 5m

  condition:
    $e1 and $e2
}
```

## 4. Snort

### Purpose

Snort is an open source network intrusion detection and prevention system. Snort rules define malicious or suspicious network activity and can generate alerts when packets match rule logic. When deployed inline, Snort can also block matching traffic.

Snort is best suited for:

1. Network IDS and IPS detection.
2. Exploit attempt detection.
3. Command and control traffic detection.
4. Protocol specific signatures.
5. Network based virtual patching and compensating controls.

### Typical Rule Elements

| Element | Purpose |
| --- | --- |
| Action | What to do, such as alert, pass, drop, reject, or log |
| Protocol | Network protocol, such as TCP, UDP, ICMP, or IP |
| Source and destination | IP ranges, ports, and direction |
| Message | Human readable alert text |
| Content options | Payload strings or byte patterns |
| Flow and state | Direction, established sessions, client or server context |
| References | CVE, advisory, malware, or campaign reference |
| SID and revision | Rule identity and version control |
| Classtype and priority | Alert categorization and severity |

### Attribution Use

Snort rules can support attribution by detecting network behaviors associated with exploit delivery, staging infrastructure, C2 channels, scanning behavior, protocol misuse, and known malware communications. Snort is especially valuable when endpoint telemetry is incomplete or when the defender needs network level compensating controls.

A Snort match usually supports a network behavior or exploit hypothesis. It does not independently establish actor identity, sponsorship, or intent. Encrypted traffic, NAT, shared infrastructure, proxy use, content delivery networks, and compromised servers can all weaken attribution confidence.

### Minimal Snort Skeleton

```text
alert tcp any any -> $HOME_NET 80 (
    msg:"EXAMPLE suspicious HTTP pattern";
    flow:to_server,established;
    content:"example";
    http_uri;
    classtype:web-application-attack;
    sid:1000001;
    rev:1;
)
```

## Unified Detection Engineering Workflow

| Step | Activity | Output |
| ---: | --- | --- |
| 1 | Define the intelligence or detection requirement | Clear question, scope, priority, telemetry need |
| 2 | Identify the evidence domain | Logs, malware files, memory, network packets, cloud events, identity events, AI workflow telemetry |
| 3 | Classify the detection object | IOC, IOA, IoPC, malware pattern, log behavior, network signature, or multi-event correlation |
| 4 | Choose the rule language or representation | Sigma, YARA, YARA-L, Snort, indicator list, hunt query, or more than one |
| 5 | Write the rule or indicator record with metadata | Rule, owner, date, source, severity, references, ATT&CK tags, confidence, caveats |
| 6 | Test against known bad and known good data | True positives, false positives, false negatives |
| 7 | Tune the logic | Better selectors, exclusions, thresholds, scope limits |
| 8 | Deploy and monitor | Alert quality, performance, case outcomes, suppression logic |
| 9 | Review and retire stale logic | Updated references, modified date, rule status, expiry decision |

## Choosing the Right Language or Indicator Type

| Need | Best choice | Reason |
| --- | --- | --- |
| Share behavior based detection across SIEMs | Sigma | Vendor neutral log detection format |
| Detect malware family from binary patterns | YARA | Strong file, byte, string, and memory matching |
| Correlate normalized events in Google SecOps | YARA-L | Native structured query and rule language for Google SecOps |
| Detect exploit traffic or C2 on the network | Snort | Packet level IDS and IPS rule logic |
| Share simple observed artifacts | IOC | Practical for blocking, enrichment, scoping, and retro-hunting |
| Detect active adversary behavior | IOA | Captures behavior and attack sequence instead of only artifacts |
| Detect AI workflow manipulation | IoPC | Focuses on prompt, context, tool-use, memory, output, and agent state evidence |
| Build multi-layer detection for one campaign | Combine all relevant types | Covers logs, files, platform telemetry, network packets, artifacts, behaviors, and AI workflow evidence |

## Quality Checklist

| Control | Why it matters |
| --- | --- |
| State the detection objective | Prevents broad rules with unclear analytic value |
| Separate IOC, IOA, IoPC, TTP, and attribution claims | Avoids treating a detection as actor proof |
| Add source and reference metadata | Preserves traceability |
| Record confidence and caveats | Supports responsible CTI reporting |
| Include false positive notes | Improves SOC usability |
| Test on known good and known bad samples | Measures precision and recall |
| Use ATT&CK tags where appropriate | Supports coverage mapping and gap analysis |
| Preserve prompt, context, tool-call, output, and audit logs for IoPC analysis | Enables AI workflow investigation and containment |
| Track rule status and modified date | Prevents stale detection logic |
| Define owner and review cycle | Enables governance and lifecycle management |
| Review performance impact | Reduces cost, latency, and alert fatigue |

## Detection and Attribution Caveats

| Caveat | Attribution risk | Mitigation |
| --- | --- | --- |
| Tool reuse | Same malware or tool may be used by multiple actors | Corroborate with infrastructure, timing, victimology, and TTPs |
| Infrastructure reuse | Shared, leased, or compromised systems can mislead analysts | Validate historical ownership, hosting, passive DNS, and certificate reuse |
| IOC reuse or planting | Simple artifacts may be copied, purchased, spoofed, or deliberately planted | Treat IOCs as leads, not actor proof |
| IOA overlap | Similar behavior may reflect common playbooks, public tools, or emulation | Validate sequence, timing, operational context, and telemetry quality |
| IoPC ambiguity | Prompt compromise may be confused with benign model error, user error, or unsafe design | Preserve logs and test whether manipulation affected tool use, data access, or output behavior |
| False flags | Adversaries may plant strings, paths, language artifacts, copied code, or prompt artifacts | Use ACH, Devil's Advocacy, and independent corroboration |
| Over-clustering | Similar rules may group unrelated activity | Require explicit cluster criteria and confidence levels |
| Telemetry gaps | Absence of detection may be misread as absence of activity | Document data coverage and collection limits |
| Vendor lock-in | Platform specific logic may not transfer cleanly | Preserve analytic logic separately from backend query syntax |

## Example Multi-Layer Detection Package

| Layer | Rule or indicator type | Example output |
| --- | --- | --- |
| Network | Snort | Detect exploit attempt or C2 URI pattern |
| Endpoint and SIEM | Sigma | Detect process behavior, registry modification, or suspicious authentication |
| Malware | YARA | Detect payload family or configuration pattern |
| Google SecOps correlation | YARA-L | Correlate endpoint, identity, and file hash events over time |
| Indicator intelligence | IOC | Block or hunt for known malicious artifacts |
| Behavior analytics | IOA | Hunt for active attack sequences and TTPs |
| AI workflow security | IoPC | Detect prompt injection, malicious retrieved context, or unsafe tool invocation |
| CTI assessment | Narrative and evidence register | Explain what the rules and indicators detect, confidence, false positives, and attribution limits |

## LLM Supported Use

LLMs can assist with rule documentation, hypothesis generation, rule translation drafts, false positive brainstorming, test case design, and indicator classification. They should not be allowed to invent indicators, sources, CVEs, malware names, or actor associations.

| Task | Safe LLM use |
| --- | --- |
| Rule documentation | Convert technical logic into SOC facing explanation |
| Indicator classification | Separate IOC, IOA, IoPC, TTP, and attribution claims |
| False positive analysis | Suggest benign explanations that analysts should test |
| Cross language planning | Map the same detection idea into Sigma, YARA, YARA-L, Snort, IOC, IOA, and IoPC coverage concepts |
| Peer review | Check whether rule or indicator logic matches the stated detection objective |
| Attribution discipline | Separate detection finding from actor, sponsor, and intent claims |

## Repository Output Template

| Field | Example |
| --- | --- |
| Detection name | Suspicious Example Activity |
| Rule language or indicator type | Sigma, YARA, YARA-L, Snort, IOC, IOA, or IoPC |
| Data source | Windows process creation, PE file, Google SecOps UDM event, HTTP packet, prompt log, tool-call log |
| Detection objective | Identify behavior, artifact, malware family, AI workflow manipulation, or network activity associated with a specific technique |
| Source intelligence | Advisory, malware report, incident case, reverse engineering note, AI security review, prompt log analysis |
| ATT&CK or AI security mapping | Technique, tactic, prompt injection class, or control mapping where appropriate |
| Confidence | Low, moderate, or high based on validation and source quality |
| False positives | Known administrative, benign, test, or expected AI workflow patterns |
| Attribution note | What this rule or indicator supports and what it does not prove |
| Review date | Date for tuning, retirement, or update |

## References

Google Cloud. (2026). *Get started: YARA-L 2.0 in SecOps*. Google Cloud Documentation. https://docs.cloud.google.com/chronicle/docs/yara-l/getting-started

MITRE. (n.d.). *MITRE ATT&CK*. Retrieved June 24, 2026, from https://attack.mitre.org/

OASIS Cyber Threat Intelligence Technical Committee. (2021). *STIX version 2.1*. OASIS Standard. https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html

OWASP Foundation. (2025). *OWASP top 10 for LLM applications 2025*. OWASP Gen AI Security Project. https://genai.owasp.org/llm-top-10/

SigmaHQ. (2026). *Sigma: Generic signature format for SIEM systems*. GitHub. https://github.com/SigmaHQ/sigma

Snort. (2026). *Snort: Network intrusion detection and prevention system*. Cisco. https://www.snort.org/

Snort. (2026). *Snort 3 rule writing guide*. Cisco. https://docs.snort.org/start/

VirusTotal. (n.d.). *YARA: The pattern matching swiss knife for malware researchers*. https://virustotal.github.io/yara/

YARA Project. (n.d.). *YARA documentation*. Read the Docs. https://yara.readthedocs.io/en/latest/
