# Detection Rule Languages, Formats, Indicators, Retro-Hunting, and the Pyramid of Pain

This page introduces widely used detection rule languages, signature formats, capability rule formats, practical detection indicator categories, Retro-Hunting workflows, and the Pyramid of Pain model. Together, these concepts support cyber threat intelligence, detection engineering, incident response, threat hunting, malware analysis, AI security monitoring, and cyber attribution analysis.

## Scope

This page covers:

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
12. The Pyramid of Pain

None of these should be treated as attribution by themselves. They help analysts capture repeatable evidence patterns, scope incidents, build timelines, preserve analytic logic, improve visibility, and support more disciplined attribution judgments.

## Quick Comparison

| Type | Primary data domain | Main use | Typical user | Main strength | Main limitation |
| --- | --- | --- | --- | --- | --- |
| Sigma | Logs and event telemetry | Portable SIEM and XDR detection logic | Detection engineers, SOC analysts, threat hunters | Captures behavioral detections across platforms | Requires backend conversion and field mapping |
| YARA | Files, malware samples, strings, bytes, memory | Malware identification and classification | Malware analysts, reverse engineers, CTI analysts | Good for file and malware pattern matching | Can be brittle if rules are narrow or poorly designed |
| YARA-L | Google SecOps telemetry using UDM fields | Search, dashboards, detection, and correlation | Google SecOps analysts | Strong multi-event and normalized telemetry correlation | Platform specific |
| Snort | Network packets and protocol traffic | IDS and IPS detection | Network defenders, IDS/IPS engineers | Strong packet and exploit detection | Depends on network visibility and tuning |
| Suricata | Network packets, protocol transactions, NSM telemetry | IDS, IPS, and network monitoring | Network defenders, SOC analysts, threat hunters | Rich protocol-aware network detection | Requires tuning and operational maturity |
| capa | Executable files and reverse engineering features | Identify malware capabilities | Malware analysts and reverse engineers | Describes what malware can do | Does not prove actor identity or execution |
| ClamAV | Files, signatures, hashes, containers | File and malware detection | Defenders, SOC teams, gateway operators | Practical AV style file detection | Signature matching can be evaded |
| IOC | Observable artifacts | Blocking, enrichment, scoping, and hunting | SOC, IR, CTI | Fast operational use | Can be short-lived, spoofed, or planted |
| IOA | Behavioral signals and attack sequences | Detect active attack behavior | Threat hunters and SOC analysts | More durable than simple artifacts | Requires telemetry and tuning |
| IoPC | Prompt, context, tool, output, and memory signals | Detect AI workflow compromise | AI security teams, SOC analysts | Useful for prompt and agent security | Emerging term and practice |
| Retro-Hunting | Historical retained telemetry and evidence | Search past activity after new intelligence appears | Threat hunters, SOC analysts, IR, CTI | Expands scoping and timelines | Limited by retention and data quality |
| Pyramid of Pain | Detection prioritization model | Prioritize higher-friction detections | Detection engineers, threat hunters, CTI teams | Helps focus on what hurts adversaries most | It is a model, not evidence |

## Detection Coverage by Evidence Type

| Evidence type | Sigma | YARA | YARA-L | Snort | Suricata | capa | ClamAV | IOC | IOA | IoPC | Retro-Hunting |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Endpoint logs | High | Low | High if normalized | Low | Low | Low | Low | High | High | Medium | High if retained |
| SIEM telemetry | High | Low | High | Low to medium | Medium to high | Low | Medium | High | High | Medium | High |
| Malware files | Low | High | Medium | Low | Medium | High | High | High | Low | Low | High if retained |
| Network packets | Low | Low | Medium | High | High | Low | Low | High | Medium | Low | High if retained |
| Cloud and identity logs | High | Low | High | Low | Low | Low | Low | High | High | Medium | High if retained |
| AI prompts and tool logs | Medium if logged | Low | Medium to high | Low | Low | Low | Low | Medium | Medium | High | High if retained |
| Threat hunting | High | High | High | Medium | High | High | Medium | High | High | High | High |
| Preventive blocking | Usually indirect | Usually indirect | Usually indirect | High inline | High inline | No | Sometimes | Sometimes | Sometimes | Sometimes | No |

## Detection Indicator Types

### Indicators of Compromise (IOC)

Indicators of Compromise are observable artifacts suggesting compromise or malicious activity may have occurred.

| IOC type | Examples | Practical use |
| --- | --- | --- |
| File | Hashes, filenames, paths, malware labels | Malware triage, quarantine, retro-hunt |
| Network | IPs, domains, URLs, DNS records, user agents | Blocking, enrichment, clustering |
| Host | Registry keys, services, mutexes, persistence artifacts | Endpoint investigation |
| Identity | Suspicious accounts, token abuse, impossible travel | Account compromise investigation |
| Cloud | API keys, service account changes, unusual role assignments | Cloud compromise detection |

IOCs are operationally useful, but they do not prove actor identity.

### Indicators of Attack (IOA)

Indicators of Attack are behavior-oriented signals suggesting an attack is underway or being attempted.

| IOA type | Examples | Practical use |
| --- | --- | --- |
| Execution behavior | Suspicious PowerShell or script abuse | Detect active intrusion behavior |
| Credential behavior | Password spraying, credential dumping patterns | Detect identity-focused attacks |
| Lateral movement | Suspicious RDP, SSH, admin share use | Detect movement before objectives |
| Defense evasion | Logging disabled, EDR tampering, injection | Detect visibility avoidance |
| Exfiltration behavior | Staging, compression, unusual outbound transfer | Detect theft preparation or execution |

IOAs are often more durable than basic IOCs because they capture tradecraft.

### Indicators of Prompt Compromise (IoPC)

IoPC refers to AI-specific signals suggesting that prompts, retrieved context, model outputs, tool calls, memory, or workflow state may have been manipulated.

| IoPC type | Examples | Practical use |
| --- | --- | --- |
| Prompt content | Jailbreak strings, hidden instructions, overrides | Detect direct prompt injection |
| Retrieved context | Malicious instructions inside documents or webpages | Detect indirect prompt injection and RAG poisoning |
| Tool invocation | Unexpected tool calls or unauthorized actions | Detect agent workflow manipulation |
| Output behavior | Sudden refusal bypass or data exfiltration wording | Detect compromised model output |
| Memory or state | Poisoned state or unexpected persistence | Detect durable AI workflow compromise |
| Audit signal | Prompt-output mismatch or missing approval | Support investigation and containment |

## Retro-Hunting

Retro-Hunting is the practice of searching retained historical telemetry and evidence after new intelligence, new rules, new vulnerabilities, or new hypotheses become available.

| Retro-hunt object | Examples | Practical use |
| --- | --- | --- |
| IOC retro-hunt | Hashes, domains, IPs, URLs, registry paths | Scope known artifacts across historical data |
| IOA retro-hunt | Process chains, credential misuse, lateral movement | Find earlier behavior that was not alerted |
| IoPC retro-hunt | Injection strings, malicious retrieved context, unusual tool chains | Search AI workflow logs for prior compromise |
| Vulnerability retro-hunt | Exploit patterns, protocol misuse, anomalous requests | Determine whether a vulnerability was exploited before disclosure or patching |
| Malware retro-hunt | YARA matches, ClamAV matches, capa capabilities | Find stored samples linked to a campaign |
| Network retro-hunt | Suricata or Snort alerts, DNS patterns, TLS fingerprints, NetFlow, packet captures | Reconstruct prior exploit, C2, or staging activity |

Retro-Hunting expands timelines, improves scoping, and can support attribution analysis. It still does not prove identity on its own.

## Pyramid of Pain

The Pyramid of Pain is a practical model for prioritizing detection and hunting effort. It was originally introduced by **David J. Bianco (2013)**. The model explains that some indicators are easy for adversaries to change, while others impose much greater operational cost. For detection engineering, the implication is clear: lower-level indicators still matter, but mature programs should increasingly emphasize artifacts, tools, and TTPs that impose greater pain on the adversary.

**Diagram adapted from the original Pyramid of Pain concept by David J. Bianco (2013), visually aligned to the common layered pyramid style.**

```text
                         ╱╲                                      Tough
                        ╱  ╲
                       ╱ TTPs ╲
                      ╱────────╲
                     ╱  Tools   ╲                                Challenging
                    ╱────────────╲
                   ╱ Network or   ╲                               Annoying
                  ╱ Host Artifacts ╲
                 ╱──────────────────╲
                ╱   Domain Names     ╲                            Simple
               ╱──────────────────────╲
              ╱     IP Addresses       ╲                          Easy
             ╱──────────────────────────╲
            ╱       Hash Values          ╲                        Trivial
           ╱──────────────────────────────╲
```

| Pyramid level | Typical focus | Pain to the adversary | Detection implication |
| --- | --- | --- | --- |
| Hash Values | Exact file hashes and binary matches | Trivial | Fast for blocking and triage, but easy for adversaries to change |
| IP Addresses | Source, destination, and C2 IPs | Easy | Operationally useful, but infrastructure rotates easily |
| Domain Names | Malicious domains and phishing hosts | Simple | More useful than IPs in some cases, but still replaceable |
| Network or Host Artifacts | Mutexes, paths, URI patterns, protocol traits, registry keys | Annoying | Useful for clustering, hunting, and campaign scoping |
| Tools | Malware families, loaders, scripts, offensive utilities | Challenging | Detecting tools forces meaningful adversary rework |
| TTPs | Behaviors, procedures, and operational tradecraft | Tough | Usually the most valuable long-term detection focus |

The Pyramid of Pain is a prioritization lens, not a replacement for operational blocking. Defenders should still use low-level indicators for rapid response, while building higher-level detections over time.

## Core Detection Languages and Formats

### Sigma

Sigma is a generic and open signature format for log and SIEM detections. It is best for behavior-based detections in logs, sharing detection logic across tools, and mapping detections to MITRE ATT&CK.

### YARA

YARA is used to identify and classify malware samples, files, or memory content based on strings, byte patterns, and Boolean conditions. It is useful for malware family detection, repository scanning, memory scanning, and comparing related samples.

### YARA-L

YARA-L 2.0 is Google Security Operations' structured query language for search, dashboards, detections, and multi-event correlation using normalized telemetry.

### Snort

Snort is an open source IDS and IPS for detecting malicious or suspicious network traffic. It is useful for exploit detection, C2 detection, and network-based virtual patching.

### Suricata

Suricata is an open source network threat detection engine for IDS, IPS, and network security monitoring. It provides protocol-aware detection and rich telemetry such as EVE JSON.

### capa

capa rules identify capabilities in executable files, helping analysts understand what malware can do rather than only what family it belongs to.

### ClamAV Signatures

ClamAV signatures are text-based antivirus signatures for file-focused malware detection, triage, gateway scanning, and signature sharing.

## Unified Detection Engineering Workflow

| Step | Activity | Output |
| ---: | --- | --- |
| 1 | Define the intelligence, detection, or Retro-Hunting requirement | Clear question, scope, and telemetry need |
| 2 | Identify the evidence domain | Logs, files, memory, packets, cloud, identity, AI workflow telemetry |
| 3 | Classify the object | IOC, IOA, IoPC, signature, capability, hunt query, or correlation logic |
| 4 | Choose the language or representation | Sigma, YARA, YARA-L, Snort, Suricata, capa, ClamAV, or a hunt query |
| 5 | Write logic with metadata | Owner, source, date, confidence, caveats, tags |
| 6 | Test on known bad and known good data | Precision and recall evidence |
| 7 | Tune the logic | Better selectors, exclusions, thresholds, or scope |
| 8 | Run Retro-Hunting if relevant | Historical hits, first seen, affected assets |
| 9 | Deploy and monitor | Alert quality and operational outcomes |
| 10 | Review and retire stale logic | Lifecycle and governance |

## Choosing the Right Type

| Need | Best choice | Reason |
| --- | --- | --- |
| Share behavior detections across SIEMs | Sigma | Vendor-neutral log detection |
| Detect malware family from binaries | YARA | Strong file and memory pattern matching |
| Correlate normalized events in Google SecOps | YARA-L | Native structured rule language |
| Detect exploit traffic or C2 on the network | Snort or Suricata | Packet and protocol-level logic |
| Identify malware capabilities in executables | capa | Capability-focused clustering and triage |
| Create file-focused AV signatures | ClamAV | Practical file and malware detection |
| Share simple observed artifacts | IOC | Fast scoping, blocking, and enrichment |
| Detect active adversary behavior | IOA | Captures behaviors rather than artifacts |
| Detect AI workflow manipulation | IoPC | Focused on prompt, context, tool, and memory abuse |
| Search retained data after new intelligence appears | Retro-Hunting | Finds earlier activity and campaign continuity |
| Prioritize durable detections | Pyramid of Pain | Pushes teams toward higher-friction adversary changes |

## Quality Checklist

| Control | Why it matters |
| --- | --- |
| State the detection objective | Prevents vague and low-value rules |
| Separate detection findings from attribution claims | Avoids treating hits as actor proof |
| Record confidence and caveats | Supports disciplined CTI reporting |
| Add metadata and references | Preserves traceability |
| Test on good and bad data | Measures precision and recall |
| Define ownership and review cycle | Supports governance |
| Define Retro-Hunting scope and lookback | Prevents misleading conclusions from partial retention |
| Use the Pyramid of Pain as a prioritization lens | Encourages more durable detection coverage |
| Keep logic separate from tool-specific syntax | Improves portability |

## Detection and Attribution Caveats

| Caveat | Attribution risk | Mitigation |
| --- | --- | --- |
| Tool reuse | Same malware or tool may be used by multiple actors | Corroborate with infrastructure, timing, and victimology |
| Infrastructure reuse | Shared or compromised systems can mislead analysts | Validate ownership, history, and reuse |
| IOC reuse or planting | Artifacts may be spoofed or planted | Treat IOCs as leads, not proof |
| IOA overlap | Similar behavior may reflect common playbooks or emulation | Validate sequence and context |
| Capability overlap | Similar malware capabilities may reflect common libraries | Compare implementation and lineage |
| IoPC ambiguity | Prompt compromise may be confused with model error or unsafe design | Preserve logs and validate impact |
| Retro-Hunting bias | Incomplete retention or hypothesis bias may distort interpretation | Document lookback, gaps, and alternatives |
| Pyramid of Pain misuse | Teams may ignore low-level indicators that still matter operationally | Use the model for prioritization, not exclusion |

## References

Bianco, D. J. (2013). *The Pyramid of Pain*. https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html

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
