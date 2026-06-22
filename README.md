# Cyber Attribution

A public knowledge repository for structured cyber attribution methodology, references, and analytical notes.

## Purpose

This repository supports disciplined cyber attribution analysis. It is intended for analysts, cyber threat intelligence teams, incident responders, policy advisers, legal advisers, and national security practitioners who need a structured way to reason about the source, sponsorship, intent, and confidence level of cyber operations.

The core principle is to separate evidence from assessment. Analysts should document what is observed, what is inferred, what is externally sourced, what remains uncertain, and how confidence is expressed.

## Scope

| Area | Focus |
| --- | --- |
| Attribution methodology | Analytical frameworks, workflows, confidence language, and reasoning discipline |
| Evidence evaluation | Technical evidence, source reliability, alternative hypotheses, and uncertainty |
| Technical attribution | Malware, infrastructure, TTPs, tooling, timing, victimology, and campaign patterns |
| Strategic attribution | Intent, geopolitical context, operational continuity, sponsorship, and state responsibility |
| AI age attribution | False flags, synthetic artifacts, automated analysis, deception, and information operations |

## Repository structure

```text
.
├── README.md
├── LICENSE.md
└── Methodology/
    └── attribution-methodology.md
```

## Main document

Start here:

[Cyber Attribution Methodology](Methodology/attribution-methodology.md)

This document lists common cyber attribution frameworks from academic and industry research. It is intended to serve as the foundation for future manuals, guides, and analytical templates.

## Analytical layers

| Layer | Main question | Example output |
| --- | --- | --- |
| Technical attribution | What infrastructure, tools, malware, and behaviors were used? | Actor cluster, campaign family, technical indicators |
| Operational attribution | How was the operation planned and executed? | Campaign model, operational pattern, intrusion lifecycle |
| Strategic attribution | Why was the operation conducted, and who benefits? | Motive, intent, geopolitical context |
| Legal attribution | Can conduct be attributed to a state or legally responsible entity? | State responsibility assessment |
| Policy attribution | How should the assessment support response? | Public attribution, diplomacy, sanctions, legal action, or defensive response |

## External reference anchors

The repository links to external resources rather than copying their content. Key anchors include ODNI cyber attribution guidance, the Diamond Model, MITRE ATT&CK, Attack Flow, STIX 2.1, FIRST TLP 2.0, and legal scholarship on state responsibility and public attribution.

## License

Original repository content is authored by Yuval Sinay and licensed under CC BY 4.0 unless a specific file states otherwise.

Suggested attribution:

> Sinay, Y. (2026). _Cyber Attribution_. GitHub. Licensed under CC BY 4.0.

## Responsible use

Do not publish sensitive indicators, victim data, personal data, intelligence sources and methods, confidential legal advice, or operational information that is not approved for release.

This repository is for educational, defensive, analytical, and policy support purposes. It does not constitute legal advice, intelligence reporting, or official government guidance unless a specific document explicitly states otherwise.
