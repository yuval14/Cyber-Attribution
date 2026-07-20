# CLOAK Concealment Framework

## Concealment Layers for Online Anonymity and Knowledge

CLOAK is an open knowledge base for mapping the methods cybercriminals and other threat actors use to conceal their identities, infrastructure, communications, activities, and operational traces. Inspired by the structure of MITRE ATT&CK, CLOAK shifts the analytical focus from how an adversary conducts an attack to how the adversary avoids identification, investigation, attribution, and disruption.

The framework was developed through qualitative research that examined more than 200 operational security guides from the open web and the dark web. Its initial January 2025 release documented 13 tactics, 109 techniques, 679 sub-techniques, 586 procedures, and 1,387 unique TTP components.

## Why CLOAK Matters for Cyber Attribution

Traditional cyber attribution frequently emphasizes malware, infrastructure, victimology, timing, targeting, and attack techniques. CLOAK adds another analytical dimension: concealment tradecraft.

Concealment behavior can provide attribution-relevant evidence when analysts examine recurring combinations of anonymity services, infrastructure separation, identity compartmentalization, communication discipline, anti-forensics, physical security, deception, and trace-removal practices.

A single concealment technique rarely supports attribution by itself. However, a consistent combination of concealment choices may contribute to a behavioral or operational fingerprint when correlated with other evidence.

## Three Layers of Concealment

### 1. Technical Layer

The technical layer focuses primarily on creating anonymity and reducing technical visibility.

Common examples include:

- Tor, VPNs, proxies, and layered routing
- Encryption and protected communications
- Virtual machines and environment isolation
- Anti-fingerprinting measures
- Hardened systems and privacy-focused configurations
- Log deletion, secure wiping, and trace removal
- Obfuscation of infrastructure and network activity

### 2. Behavioral Layer

The behavioral layer focuses on sustaining anonymity over time through operational discipline.

Common examples include:

- Compartmentalization of identities and activities
- Avoidance of identity reuse
- Minimal disclosure of personal information
- Threat modeling and risk management
- Need-to-know practices
- Communication discipline and silence
- Cover stories, deception, and misinformation
- Separation of operational and personal routines

### 3. Physical Layer

The physical layer supports continuity, reduces exposure to physical collection, and limits forensic recovery.

Common examples include:

- Faraday bags or cages
- Tamper detection
- Secure storage
- Physical destruction of devices or media
- Removal or concealment of hardware components
- Paper wallets and offline storage
- Document shredding
- Location, travel, and meeting security

## Coverage Across the Operation Lifecycle

CLOAK can be applied across the full lifecycle of an operation:

| Phase | Concealment focus | Examples |
| --- | --- | --- |
| Before | Preparation and infrastructure setup | Identity creation, infrastructure procurement, compartmentalization, device preparation |
| During | Operational security and activity concealment | Encrypted communications, anonymity services, timing discipline, low-footprint behavior |
| After | Cleanup, disruption resistance, and recovery | Trace removal, log deletion, media destruction, infrastructure abandonment, identity rotation |

## Analyst Use Cases

### Understand Adversary OpSec

CLOAK helps analysts examine how threat actors think about anonymity, exposure, operational continuity, and law-enforcement pressure.

### Build a Common Vocabulary

The framework provides a structured language for describing concealment tactics, techniques, sub-techniques, and procedures in intelligence reports, investigations, indictments, and technical assessments.

### Identify Visibility and Detection Gaps

Analysts can map known or expected concealment behavior against available telemetry to identify blind spots in endpoint, identity, network, cloud, communications, financial, and physical evidence collection.

### Support Threat Hunting

CLOAK can help convert concealment hypotheses into hunting questions, such as:

- Which accounts were created using similar infrastructure or timing patterns?
- Are multiple identities linked through device, browser, payment, DNS, or hosting artifacts?
- Are there signs of log deletion, timestomping, secure wiping, or backup avoidance?
- Does the actor repeatedly use the same anonymity stack or infrastructure procurement model?
- Are there recurring operational pauses, communication windows, or behavioral constraints?

### Support Cyber Attribution

CLOAK-derived observations can contribute to attribution when combined with malware analysis, infrastructure analysis, victimology, temporal patterns, geopolitical context, human intelligence, financial evidence, and alternative-hypothesis testing.

### Improve Investigation and Disruption Planning

Understanding expected concealment methods can help investigators prioritize evidence sources, anticipate anti-forensic actions, preserve volatile artifacts, and design disruption strategies.

## Example Analyst Mapping

| Concealment area | Possible observations | Attribution or hunting value |
| --- | --- | --- |
| Identity concealment | Burner accounts, identity rotation, no reuse of personal identifiers | Cluster personas and compare account-creation patterns |
| Infrastructure concealment | Proxy chains, bulletproof hosting, compromised VPS, domain fronting | Correlate DNS, hosting, registrar, certificate, and payment artifacts |
| Communication concealment | Encrypted channels, steganography, protocol obfuscation | Analyze metadata, timing, traffic shape, and unusual protocol behavior |
| Artifact removal | Log deletion, wiping, timestomping, history clearing | Recover shadow copies, journals, backups, and residual metadata |
| Detection evasion | False flags, decoys, noise generation, misleading artifacts | Test inconsistencies and compare competing hypotheses |
| Footprint minimization | Living-off-the-land, low dwell time, limited actions | Hunt for rare administrative sequences and low-volume anomalies |

## Recommended Analytical Workflow

1. **Collect observations** from logs, endpoints, networks, cloud systems, identity platforms, HUMINT, OSINT, financial records, and physical evidence.
2. **Map observations to CLOAK** tactics, techniques, sub-techniques, and procedures.
3. **Identify visibility gaps** and determine which concealment behaviors may be unobservable with existing telemetry.
4. **Develop hypotheses** regarding actor discipline, infrastructure management, identity separation, and trace-removal behavior.
5. **Hunt and validate** using independent data sources and alternative explanations.
6. **Assess attribution value** while distinguishing direct evidence, circumstantial evidence, inference, and uncertainty.
7. **Support disruption** by identifying dependencies, recurring concealment patterns, and operational weaknesses.

## Analytical Cautions

CLOAK should not be treated as a deterministic attribution mechanism.

Analysts should consider the following limitations:

- Many concealment techniques are widely available and are not unique to a specific actor.
- Sophisticated actors may deliberately imitate another actor's OpSec practices.
- Some techniques may be outdated, ineffective, or inconsistently applied.
- Absence of evidence may reflect collection gaps rather than absence of a technique.
- Concealment behavior must be evaluated together with technical, operational, strategic, and legal evidence.
- Confidence statements should clearly separate observed facts from analytical judgments.

## Relationship to Other Frameworks

CLOAK complements rather than replaces established frameworks:

- **MITRE ATT&CK** explains how adversaries conduct operations.
- **CLOAK** explains how adversaries conceal themselves and their operations.
- **MITRE D3FEND** supports defensive countermeasure mapping.
- **MITRE Engage** supports adversary engagement and deception planning.
- **Diamond Model** supports relationships among adversary, capability, infrastructure, and victim.
- **STIX 2.1 and CASE/UCO** can support structured representation and exchange of evidence and intelligence.

## Key Takeaway

Cyber attribution should look beyond malware and attack infrastructure. Understanding how an adversary hides, separates identities, controls communications, removes traces, and manages physical exposure can transform apparent noise into evidence for detection, investigation, attribution, and disruption.

## Author

Yuval Sinay

## Reference

Deben, M. (2025). *Concealment layers for online anonymity and knowledge (CLOAK)* [Computer software and knowledge base]. GitHub. https://github.com/Mickinthemiddle/CLOAK

## Related Resource

Interactive CLOAK knowledge base: https://opsectechniques.com
