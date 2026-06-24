# Detection Rule Languages, Formats, Indicators, and Retro-Hunting: Sigma, YARA, YARA-L, Snort, Suricata, capa, ClamAV, IOC, IOA, IoPC, and Retro-Hunting

This page introduces widely used detection rule languages, signature formats, capability rule formats, practical detection indicator categories, and Retro-Hunting workflows that support cyber threat intelligence, detection engineering, incident response, threat hunting, AI security monitoring, malware analysis, reverse engineering, and cyber attribution analysis.

The page covers:

1. Sigma
2. YARA
3. YARA-L
4. Snort
5. Suricata
6. capa rules
7. ClamAV signatures
8. Indicators of Compromise (IOC)
9. Indicators of Attack (IOA)
10. Indicators of Prompt Compromise (IoPC)
11. Retro-Hunting

The purpose is not to treat a rule match, indicator match, or Retro-Hunting result as attribution by itself. Detection rules, indicators, and historical searches help analysts capture repeatable evidence patterns, test hypotheses, preserve analytic logic, scope incidents, and improve visibility across telemetry sources. Attribution still requires source evaluation, alternative hypotheses, confidence language, and corroboration across technical, operational, strategic, and legal layers.

## Source Note

The YARA security project is documented through the VirusTotal YARA project site and YARA documentation. The domain `yara.com` is not the YARA detection language documentation site.

## Quick Comparison

| Language, format, indicator type, or workflow | Primary data domain | Main use | Typical user | Attribution value | Main limitation |
| --- | --- | --- | --- | --- | --- |
| Sigma | Logs and event telemetry | Portable SIEM and XDR detection logic | Detection engineers, SOC analysts, threat hunters | Captures behavioral patterns and maps activity to TTPs across platforms | Requires backend conversion and field mapping |
| YARA | Files, malware samples, byte patterns, strings, memory scanning | Malware identification and classification | Malware analysts, reverse engineers, CTI analysts | Links samples by code, strings, configuration, packer artifacts, and family traits | Poorly written rules can overfit, under-detect, or create false positives |
| YARA-L | Google Security Operations telemetry using UDM fields | Search, dashboards, rule-based threat detection, and event correlation | Google SecOps analysts and detection engineers | Correlates activity across normalized security events and supports multi-event logic | Platform specific to Google SecOps and dependent on data ingestion quality |
| Snort | Network packets and protocol traffic | IDS and IPS alerting or blocking | Network defenders, SOC, IDS/IPS engineers | Detects exploit attempts, C2 traffic, scans, payload patterns, and network tradecraft | Packet visibility, encryption, tuning, and protocol coverage shape effectiveness |
| Suricata | Network packets, protocol transactions, file extraction, and network security monitoring telemetry | IDS, IPS, network security monitoring, protocol analysis, and rule-based network detection | Network defenders, SOC analysts, threat hunters, IDS/IPS engineers | Detects exploit attempts, C2 traffic, protocol misuse, file transfer patterns, and network tradecraft with rich protocol context | Requires tuning, packet visibility, rule management, performance planning, and careful interpretation of shared or encrypted infrastructure |
| capa rules | Executable files, malware samples, static analysis features, and reverse engineering artifacts | Identify malware capabilities in executable files | Malware analysts, reverse engineers, CTI analysts | Describes what a program can do, such as persistence, discovery, encryption, C2, injection, or credential access | Capability detection does not prove intent, actor identity, or that a capability was actually executed |
| ClamAV signatures | Files, byte patterns, logical signatures, hashes, container metadata, and AV databases | Malware and file-based threat detection | Malware analysts, defenders, mail gateway operators, SOC teams | Supports repeatable file detection and can preserve malware identification logic for triage and blocking | Signature matching can be brittle, noisy, or limited by file coverage, packing, obfuscation, and update quality |
| IOC | Observable artifacts across endpoint, network, identity, cloud, and malware evidence | Detect or confirm activity that may already have occurred | SOC analysts, incident responders, CTI analysts | Links incidents through repeated infrastructure, files, accounts, or malware artifacts | Can be short-lived, reused, spoofed, purchased, or planted |
| IOA | Behavioral signals and attack sequences | Detect an attack attempt or activity in progress | Threat hunters, detection engineers, SOC analysts | Captures adversary behavior and tradecraft more durably than simple artifacts | Requires telemetry, baselining, and tuning to avoid false positives |
| IoPC | AI prompt, context, retrieval, tool-call, memory, output, and agent workflow signals | Detect prompt injection, indirect prompt injection, context manipulation, or unauthorized tool use | AI security teams, SOC analysts, application security teams | Helps distinguish AI workflow compromise from traditional endpoint or network compromise | Emerging repository term; not yet a mature global standard |
| Retro-Hunting | Historical logs, endpoint telemetry, network metadata, retained packets, cloud and identity events, malware repositories, and AI workflow logs | Search past data after new intelligence, rules, indicators, or hypotheses become available | Threat hunters, SOC analysts, incident responders, CTI analysts, detection engineers | Finds earlier activity, scopes campaigns, builds timelines, and tests whether evidence existed before initial detection | Depends on retention, telemetry quality, indexing, query precision, and analyst interpretation |

## Detection Coverage by Evidence Type

| Evidence type | Sigma | YARA | YARA-L | Snort | Suricata | capa | ClamAV | IOC | IOA | IoPC | Retro-Hunting |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Endpoint logs | High | Low | High, if ingested and normalized | Low | Low | Low | Low | High | High | Medium | High, if retained |
| SIEM telemetry | High | Low | High in Google SecOps | Low to medium, if network alerts are ingested | Medium to high, if EVE JSON or alerts are ingested | Low | Medium, if AV logs are ingested | High | High | Medium | High |
| Malware files | Low | High | Medium, if file hashes or metadata are in telemetry | Low | Medium, if file extraction or file metadata is enabled | High | High | High | Low | Low | High, if repositories are retained |
| Executable capabilities | Low | Medium | Low to medium | Low | Low to medium | High | Medium | Medium | Medium | Low | Medium to high, if samples are retained |
| Memory artifacts | Low | High | Low to medium | Low | Low | Medium, if extracted or supported by tooling | Medium | Medium | Medium | Low | Medium, if dumps are retained |
| Network packets | Low | Low | Medium, if packet-derived telemetry is ingested | High | High | Low | Low | High | Medium | Low | High, if packets or metadata are retained |
| Cloud and identity logs | High | Low | High, if normalized into UDM | Low | Low, except network-derived telemetry | Low | Low | High | High | Medium | High, if retained |
| AI prompts, RAG context, tool calls, and agent logs | Medium, if logged | Low | Medium to high, if ingested | Low | Low | Low | Low | Medium | Medium | High | High, if prompt and tool logs are retained |
| Threat hunting | High | High | High | Medium | Medium to high for network hunting | High for malware triage | Medium to high for file hunting | High | High | High | High |
| Preventive blocking | Usually indirect | Usually indirect | Usually indirect | High when deployed inline as IPS | High when deployed inline as IPS | No | Sometimes through AV enforcement | Sometimes | Sometimes | Sometimes through AI guardrails and tool controls | No, mainly investigative and scoping |

## Detection Indicator Types and Retro-Hunting

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

### Retro-Hunting

Retro-Hunting is the practice of searching historical telemetry and retained evidence after new intelligence, new rules, new indicators, new vulnerabilities, or new hypotheses become available. It helps analysts determine whether activity occurred before an alert was created, whether a campaign affected additional assets, and whether the same tradecraft appeared across multiple environments.

| Retro-hunt object | Examples | Practical use |
| --- | --- | --- |
| IOC retro-hunt | File hashes, domains, IP addresses, URLs, certificate fingerprints, registry paths | Scope known artifacts across historical data |
| IOA retro-hunt | Suspicious process chains, credential misuse, lateral movement, exfiltration staging | Identify earlier behavior that did not trigger an alert |
| IoPC retro-hunt | Prompt injection strings, malicious retrieved context, unusual tool-call chains, memory poisoning | Search AI workflow logs for prior prompt or agent compromise |
| Vulnerability retro-hunt | Exploit URI patterns, protocol misuse, anomalous requests, affected asset exposure | Determine whether a vulnerability was exploited before disclosure or patching |
| Malware retro-hunt | YARA matches, ClamAV signatures, capa capabilities, file metadata, packer traits | Find previously stored samples or payloads connected to a campaign |
| Network retro-hunt | Suricata or Snort alerts, DNS patterns, TLS fingerprints, NetFlow, packet captures | Reconstruct earlier C2, scanning, exploit delivery, or staging activity |

Retro-Hunting strengthens attribution analysis by expanding the timeline, identifying earlier infrastructure or tooling, testing campaign continuity, and revealing whether a suspected actor cluster has historical overlap with current evidence. It still does not prove actor identity alone. Analysts should document the lookback window, data sources searched, query logic, false positives, missing telemetry, and confidence level.

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

Sigma should not be used to claim actor identity on its own. A Sigma match usually supports a TTP, tool, or behavior finding. It becomes stronger for attribution when combined with malware analysis, infrastructure clustering, victimology, timing, source reliability, competing hypothesis analysis, and Retro-Hunting across retained telemetry.

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

YARA-L should be treated as platform specific detection logic. Its strength depends on telemetry ingestion, parser quality, UDM normalization, retention, and the analyst's ability to separate telemetry gaps from true absence of activity.

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

A Snort match usually supports a network behavior or exploit hypothesis. It does not independently establish actor identity, sponsorship, or intent. Encrypted traffic, NAT, shared infrastructure, proxy use, content delivery networks, compromised servers, and historical packet retention limits can all weaken attribution confidence.

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

## 5. Suricata

### Purpose

Suricata is an open source network threat detection engine used for IDS, IPS, and network security monitoring. Suricata signatures can inspect packets and application layer protocol transactions, and Suricata can produce rich event output such as EVE JSON for downstream SIEM, data lake, and threat hunting workflows.

Suricata is best suited for:

1. Network IDS and IPS detection.
2. Protocol-aware network detection and monitoring.
3. Exploit attempt, C2, scanning, and lateral movement detection.
4. File extraction and file metadata observation from network traffic.
5. Network telemetry enrichment for incident response and attribution analysis.

### Typical Rule Elements

| Element | Purpose |
| --- | --- |
| Action | Determines what happens when the rule matches, such as alert, pass, drop, reject, or rejectboth |
| Header | Defines protocol, source, destination, ports, and direction |
| Rule options | Defines message, flow, content, protocol buffers, references, sid, revision, classtype, and metadata |
| Protocol keywords | Allow protocol-aware matching, such as HTTP, TLS, DNS, SMB, SSH, SMTP, and other application layer protocols |
| File keywords | Support matching on file transfer behavior, file data, hashes, or file metadata when available |
| Thresholding and flow control | Help tune alert volume and reduce repeated noise |

### Attribution Use

Suricata can support attribution by capturing network tradecraft such as exploit delivery, staging infrastructure, C2 patterns, protocol misuse, JA3/JA4-like TLS fingerprints where available, DNS behavior, and file transfer behavior. It is useful when endpoint access is limited or when network telemetry provides the strongest cross-victim evidence.

A Suricata alert does not establish actor identity by itself. Analysts should consider encryption, NAT, proxies, compromised infrastructure, hosting churn, shared tooling, CDN use, telemetry gaps, retention limits, and rule false positives before using Suricata evidence in attribution judgments.

### Minimal Suricata Skeleton

```text
alert http $HOME_NET any -> $EXTERNAL_NET any (
    msg:"EXAMPLE suspicious HTTP request";
    flow:established,to_server;
    http.method;
    content:"GET";
    http.uri;
    content:"example";
    fast_pattern;
    classtype:bad-unknown;
    sid:2000001;
    rev:1;
)
```

## 6. capa Rules

### Purpose

capa rules are capability detection rules used with Mandiant capa to identify capabilities in executable files. Rather than only naming a malware family, capa helps analysts describe what a program appears capable of doing, such as persistence, command execution, discovery, encryption, network communication, process injection, credential access, or anti-analysis behavior.

capa rules are best suited for:

1. Malware triage.
2. Reverse engineering support.
3. Capability-based clustering.
4. Comparing samples by behavior-relevant code features.
5. Translating reverse engineering findings into repeatable analytic logic.

### Typical Rule Elements

| Element | Purpose |
| --- | --- |
| Rule name | Human readable capability statement |
| Metadata | Author, scope, references, ATT&CK mapping, examples, and library or malware context |
| Scope | Defines whether the rule applies to file, function, basic block, or instruction level features |
| Features | Strings, APIs, mnemonics, numbers, bytes, imports, namespaces, and other static analysis features |
| Logic | Boolean combinations such as and, or, optional, count, and nested feature groups |

### Attribution Use

capa rules can support attribution by helping analysts compare executable capabilities across malware samples and campaigns. Capability overlap may reveal shared tooling, reused libraries, development patterns, or operational requirements.

capa findings should not be treated as proof that a capability was executed or that the same actor operated every sample. Capability overlap can reflect common malware design, reused open source code, shared builders, commodity tooling, or copied techniques.

### Minimal capa Rule Skeleton

```yaml
rule:
  meta:
    name: example capability
    namespace: example/capability
    author: Your Name
    scope: function
    description: Detects an example executable capability.
    examples:
      - 00000000000000000000000000000000
  features:
    - and:
      - api: kernel32.CreateFileA
      - string: "example"
```

## 7. ClamAV Signatures

### Purpose

ClamAV signatures are text-based antivirus signatures used by ClamAV for malware and file-based threat detection. ClamAV supports multiple signature formats, including hash-based signatures, body-based signatures, logical signatures, container or file metadata signatures, and YARA rules.

ClamAV signatures are best suited for:

1. File-based malware detection.
2. Mail gateway and server-side scanning.
3. Hash or pattern-based blocking.
4. Malware triage and repository scanning.
5. Lightweight signature sharing for file-focused detection.

### Typical Signature Types

| Signature type | Purpose |
| --- | --- |
| Hash signatures | Match known malicious files by cryptographic hash |
| Body-based signatures | Match byte sequences or patterns in file content |
| Logical signatures | Combine multiple conditions into more expressive detection logic |
| Container and metadata signatures | Match file type, container, archive, or structural metadata conditions |
| YARA signatures | Use supported YARA rules for malware and file pattern detection in ClamAV workflows |

### Attribution Use

ClamAV signatures can support attribution by preserving file-based detection logic for malware families, campaign payloads, and known malicious artifacts. They are useful for repository scanning, email gateway detection, Retro-Hunting, and confirming whether a known payload appears across environments.

A ClamAV signature match should normally be treated as file identification or malware classification evidence. It does not independently prove actor identity, sponsor, control, or intent. Analysts should corroborate with malware analysis, infrastructure evidence, victimology, timing, and confidence assessment.

### Minimal ClamAV Logical Signature Skeleton

```text
Example.Malware.Logical;Target:0;(0&1);6578616d706c65;6d61726b6572
```

## Unified Detection Engineering Workflow

| Step | Activity | Output |
| ---: | --- | --- |
| 1 | Define the intelligence, detection, or Retro-Hunting requirement | Clear question, scope, priority, telemetry need, and lookback window |
| 2 | Identify the evidence domain | Logs, malware files, executable capabilities, memory, network packets, cloud events, identity events, AI workflow telemetry |
| 3 | Classify the detection object | IOC, IOA, IoPC, malware pattern, executable capability, AV signature, log behavior, network signature, multi-event correlation, or historical hunt query |
| 4 | Choose the rule language or representation | Sigma, YARA, YARA-L, Snort, Suricata, capa, ClamAV, indicator list, Retro-Hunting query, or more than one |
| 5 | Write the rule, indicator record, or hunt query with metadata | Rule, owner, date, source, severity, references, ATT&CK tags, confidence, caveats, time range |
| 6 | Test against known bad and known good data | True positives, false positives, false negatives |
| 7 | Tune the logic | Better selectors, exclusions, thresholds, scope limits, query optimization |
| 8 | Run Retro-Hunting where relevant | Historical hits, first-seen time, affected assets, related cases, possible missed alerts |
| 9 | Deploy and monitor | Alert quality, performance, case outcomes, suppression logic |
| 10 | Review and retire stale logic | Updated references, modified date, rule status, expiry decision |

## Choosing the Right Language, Format, Indicator Type, or Workflow

| Need | Best choice | Reason |
| --- | --- | --- |
| Share behavior based detection across SIEMs | Sigma | Vendor neutral log detection format |
| Detect malware family from binary patterns | YARA | Strong file, byte, string, and memory matching |
| Correlate normalized events in Google SecOps | YARA-L | Native structured query and rule language for Google SecOps |
| Detect exploit traffic or C2 on the network | Snort or Suricata | Packet and protocol level IDS/IPS rule logic |
| Perform protocol-aware network security monitoring | Suricata | Rich network security monitoring and protocol parsing capabilities |
| Identify malware capabilities in executable files | capa | Capability-focused rules support reverse engineering and triage |
| Create text-based AV signatures for file detection | ClamAV | Practical file and malware detection, including supported YARA use |
| Share simple observed artifacts | IOC | Practical for blocking, enrichment, scoping, and Retro-Hunting |
| Detect active adversary behavior | IOA | Captures behavior and attack sequence instead of only artifacts |
| Detect AI workflow manipulation | IoPC | Focuses on prompt, context, tool-use, memory, output, and agent state evidence |
| Search retained data after new intelligence appears | Retro-Hunting | Finds earlier activity, expands scoping, and tests campaign continuity |
| Build multi-layer detection for one campaign | Combine all relevant types | Covers logs, files, capabilities, platform telemetry, network packets, artifacts, behaviors, AI workflow evidence, and historical searches |

## Quality Checklist

| Control | Why it matters |
| --- | --- |
| State the detection objective | Prevents broad rules with unclear analytic value |
| Separate IOC, IOA, IoPC, TTP, malware capability, Retro-Hunting result, and attribution claims | Avoids treating a detection or historical hit as actor proof |
| Define the Retro-Hunting lookback period and telemetry scope | Prevents misleading conclusions from partial retention or incomplete data |
| Add source and reference metadata | Preserves traceability |
| Record confidence and caveats | Supports responsible CTI reporting |
| Include false positive notes | Improves SOC usability |
| Test on known good and known bad samples | Measures precision and recall |
| Use ATT&CK tags where appropriate | Supports coverage mapping and gap analysis |
| Preserve prompt, context, tool-call, output, and audit logs for IoPC analysis | Enables AI workflow investigation and containment |
| Track rule status and modified date | Prevents stale detection logic |
| Define owner and review cycle | Enables governance and lifecycle management |
| Review performance impact | Reduces cost, latency, and alert fatigue |
| Keep analytic logic separate from tool-specific syntax | Helps analysts translate detections across platforms |

## Detection and Attribution Caveats

| Caveat | Attribution risk | Mitigation |
| --- | --- | --- |
| Tool reuse | Same malware or tool may be used by multiple actors | Corroborate with infrastructure, timing, victimology, and TTPs |
| Infrastructure reuse | Shared, leased, or compromised systems can mislead analysts | Validate historical ownership, hosting, passive DNS, and certificate reuse |
| IOC reuse or planting | Simple artifacts may be copied, purchased, spoofed, or deliberately planted | Treat IOCs as leads, not actor proof |
| IOA overlap | Similar behavior may reflect common playbooks, public tools, or emulation | Validate sequence, timing, operational context, and telemetry quality |
| Capability overlap | Malware capability similarity may reflect common libraries or commodity design | Compare implementation details, code lineage, configuration, and operational use |
| AV signature ambiguity | File matches may identify a family or pattern but not the operator | Corroborate with reverse engineering, infrastructure, and incident context |
| IoPC ambiguity | Prompt compromise may be confused with benign model error, user error, or unsafe design | Preserve logs and test whether manipulation affected tool use, data access, or output behavior |
| Retro-Hunting bias | Historical searches may overstate certainty because retained data is incomplete, normalized differently, or queried after the analyst already has a hypothesis | Document lookback period, data sources, query logic, gaps, false positives, and alternative explanations |
| False flags | Adversaries may plant strings, paths, language artifacts, copied code, or prompt artifacts | Use ACH, Devil's Advocacy, and independent corroboration |
| Over-clustering | Similar rules may group unrelated activity | Require explicit cluster criteria and confidence levels |
| Telemetry gaps | Absence of detection may be misread as absence of activity | Document data coverage and collection limits |
| Vendor lock-in | Platform specific logic may not transfer cleanly | Preserve analytic logic separately from backend query syntax |

## Example Multi-Layer Detection Package

| Layer | Rule, indicator type, or workflow | Example output |
| --- | --- | --- |
| Network IDS/IPS | Snort or Suricata | Detect exploit attempt, suspicious protocol behavior, or C2 URI pattern |
| Endpoint and SIEM | Sigma | Detect process behavior, registry modification, or suspicious authentication |
| Malware pattern matching | YARA | Detect payload family or configuration pattern |
| Executable capability analysis | capa | Identify persistence, injection, discovery, encryption, or C2 capabilities |
| Antivirus signature detection | ClamAV | Detect known malicious file patterns or supported YARA signature matches |
| Google SecOps correlation | YARA-L | Correlate endpoint, identity, and file hash events over time |
| Indicator intelligence | IOC | Block or hunt for known malicious artifacts |
| Behavior analytics | IOA | Hunt for active attack sequences and TTPs |
| AI workflow security | IoPC | Detect prompt injection, malicious retrieved context, or unsafe tool invocation |
| Historical search | Retro-Hunting | Search retained telemetry for earlier related activity, first-seen events, affected assets, and missed detections |
| CTI assessment | Narrative and evidence register | Explain what the rules, indicators, and historical searches detect, confidence, false positives, and attribution limits |

## LLM Supported Use

LLMs can assist with rule documentation, hypothesis generation, Retro-Hunting query planning, rule translation drafts, false positive brainstorming, test case design, and indicator classification. They should not be allowed to invent indicators, sources, CVEs, malware names, actor associations, or historical search results.

| Task | Safe LLM use |
| --- | --- |
| Rule documentation | Convert technical logic into SOC facing explanation |
| Indicator classification | Separate IOC, IOA, IoPC, TTP, malware capability, Retro-Hunting result, and attribution claims |
| Retro-Hunting planning | Draft candidate lookback windows, telemetry sources, and query variants for analyst validation |
| False positive analysis | Suggest benign explanations that analysts should test |
| Cross language planning | Map the same detection idea into Sigma, YARA, YARA-L, Snort, Suricata, capa, ClamAV, IOC, IOA, IoPC, and Retro-Hunting coverage concepts |
| Peer review | Check whether rule, indicator, or hunt logic matches the stated detection objective |
| Attribution discipline | Separate detection finding and historical hit from actor, sponsor, and intent claims |

## Repository Output Template

| Field | Example |
| --- | --- |
| Detection name | Suspicious Example Activity |
| Rule language, format, indicator type, or workflow | Sigma, YARA, YARA-L, Snort, Suricata, capa, ClamAV, IOC, IOA, IoPC, or Retro-Hunting |
| Data source | Windows process creation, PE file, Google SecOps UDM event, HTTP packet, executable capability, AV signature, prompt log, tool-call log, retained SIEM telemetry, packet metadata |
| Detection objective | Identify behavior, artifact, malware family, executable capability, AI workflow manipulation, network activity, or historical evidence associated with a specific technique |
| Source intelligence | Advisory, malware report, incident case, reverse engineering note, AI security review, prompt log analysis, new IOC set, new vulnerability intelligence |
| ATT&CK or AI security mapping | Technique, tactic, prompt injection class, or control mapping where appropriate |
| Lookback period | Relevant for Retro-Hunting, for example 30, 90, 180, or 365 days, based on retention and risk |
| Confidence | Low, moderate, or high based on validation and source quality |
| False positives | Known administrative, benign, test, expected AI workflow patterns, or query artifacts |
| Attribution note | What this rule, indicator, or Retro-Hunting result supports and what it does not prove |
| Review date | Date for tuning, retirement, or update |

## References

Cisco. (2026). *Snort: Network intrusion detection and prevention system*. https://www.snort.org/

Cisco. (2026). *Snort 3 rule writing guide*. https://docs.snort.org/start/

ClamAV. (n.d.). *Signatures*. ClamAV Documentation. Retrieved June 24, 2026, from https://docs.clamav.net/manual/Signatures.html

ClamAV. (n.d.). *YARA rules*. ClamAV Documentation. Retrieved June 24, 2026, from https://docs.clamav.net/manual/Signatures/YaraRules.html

Google Cloud. (2026). *Get started: YARA-L 2.0 in SecOps*. Google Cloud Documentation. https://docs.cloud.google.com/chronicle/docs/yara-l/getting-started

Mandiant. (n.d.). *capa: The FLARE team's open-source tool to identify capabilities in executable files*. GitHub. Retrieved June 24, 2026, from https://github.com/mandiant/capa

Mandiant. (n.d.). *capa-rules: Standard collection of rules for capa*. GitHub. Retrieved June 24, 2026, from https://github.com/mandiant/capa-rules

MITRE. (n.d.). *MITRE ATT&CK*. Retrieved June 24, 2026, from https://attack.mitre.org/

OASIS Cyber Threat Intelligence Technical Committee. (2021). *STIX version 2.1*. OASIS Standard. https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html

Open Information Security Foundation. (n.d.). *Rules format*. Suricata documentation. Retrieved June 24, 2026, from https://docs.suricata.io/en/latest/rules/intro.html

OWASP Foundation. (2025). *OWASP top 10 for LLM applications 2025*. OWASP Gen AI Security Project. https://genai.owasp.org/llm-top-10/

SigmaHQ. (2026). *Sigma: Generic signature format for SIEM systems*. GitHub. https://github.com/SigmaHQ/sigma

VirusTotal. (n.d.). *YARA: The pattern matching swiss knife for malware researchers*. https://virustotal.github.io/yara/

YARA Project. (n.d.). *YARA documentation*. Read the Docs. https://yara.readthedocs.io/en/latest/
