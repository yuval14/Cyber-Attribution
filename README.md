# Cyber Attribution

A public knowledge repository for manuals, field guides, templates, and analytical notes on cyber attribution.

## Purpose

This repository is intended to host practical and research grounded material on cyber attribution. It is designed for analysts, cyber threat intelligence teams, incident responders, policy advisers, legal advisers, and national security practitioners who need a structured way to reason about the source, sponsorship, intent, and confidence level of cyber operations.

The repository separates evidence from assessment. It encourages analysts to document what is observed, what is inferred, what is externally sourced, and what remains uncertain.

## Scope

The repository covers:

| Area                     | Content type                                                                     |
| ------------------------ | -------------------------------------------------------------------------------- |
| Attribution methodology  | Manuals, guides, workflows, maturity models                                      |
| Evidence evaluation      | Evidence matrices, confidence scales, source reliability notes                   |
| Technical attribution    | Malware, infrastructure, TTPs, victimology, timing, tooling                      |
| Strategic attribution    | Intent, geopolitical context, campaign continuity, state responsibility          |
| Legal and policy framing | International law references, public attribution considerations                  |
| AI age attribution       | False flags, synthetic artifacts, automated reasoning, deception, disinformation |

Out of scope:

| Area                                     | Reason                                                                 |
| ---------------------------------------- | ---------------------------------------------------------------------- |
| Classified or sensitive operational data | This repository is intended for publishable material only              |
| Unverified actor allegations             | Attribution requires evidentiary discipline and confidence language    |
| Offensive tradecraft instructions        | The repository is focused on analysis, resilience, and responsible use |

## Recommended repository name

`cyber-attribution`

Alternative names:

| Name                          | When to use                                             |
| ----------------------------- | ------------------------------------------------------- |
| `cyber-attribution-manuals`   | If the repository will mainly hold formal manuals       |
| `cyber-attribution-framework` | If the repository will mainly define a methodology      |
| `attribution-ops-handbook`    | If the repository will mainly support operational teams |

## Suggested repository description

Manuals, guides, templates, and external references for structured cyber attribution analysis.

## Repository structure

```text
.
├── README.md
├── LICENSE.md
├── CITATION.cff
├── CONTRIBUTING.md
├── SECURITY.md
├── REFERENCES.md
├── REPOSITORY_SETUP.md
├── docs/
│   ├── README.md
│   ├── external-resources.md
│   ├── methodology/
│   │   ├── attribution-lifecycle.md
│   │   └── confidence-levels.md
│   ├── manuals/
│   │   └── _manual-template.md
│   └── templates/
│       ├── attribution-assessment-template.md
│       └── evidence-matrix-template.md
└── .github/
    ├── pull_request_template.md
    └── ISSUE_TEMPLATE/
        └── guide-request.md
```

## Core analytical principle

Attribution is a probabilistic assessment, not a binary conclusion. A good attribution product should state the evidence, competing hypotheses, confidence level, assumptions, and limits.

## Initial guide set

Start with the following documents:

1. [Attribution lifecycle](docs/methodology/attribution-lifecycle.md)
2. [Confidence levels](docs/methodology/confidence-levels.md)
3. [Attribution assessment template](docs/templates/attribution-assessment-template.md)
4. [Evidence matrix template](docs/templates/evidence-matrix-template.md)
5. [External resources](docs/external-resources.md)

## External reference anchors

This repository links to external resources rather than copying their content. Key anchors include:

| Resource                                                                     | Use in this repository                                                     |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| ODNI, _A Guide to Cyber Attribution_                                         | Baseline reference for public attribution concepts and confidence language |
| Caltagirone, Pendergast, and Betz, _The Diamond Model of Intrusion Analysis_ | Intrusion event modeling and analytic pivoting                             |
| MITRE ATT&CK                                                                 | TTP mapping and adversary behavior documentation                           |
| Attack Flow                                                                  | Structured representation of adversary behavior chains                     |
| Tallinn Manual 2.0                                                           | Legal framing for cyber operations and state responsibility discussions    |
| STIX 2.1                                                                     | Structured cyber threat intelligence representation                        |
| FIRST TLP 2.0                                                                | Information sharing and sensitivity marking                                |

See [REFERENCES.md](REFERENCES.md) for APA 7 style references.

## Recommended license

Recommended license: **Creative Commons Attribution 4.0 International, CC BY 4.0**.

Rationale: this repository is primarily for manuals, guides, templates, and educational material. CC BY 4.0 allows sharing and adaptation, including commercial use, while requiring attribution. If code is added later, consider adding a separate software license such as MIT or Apache 2.0 for the code directory.

## Attribution notice

Unless otherwise stated, original repository content is authored by Yuval Sinay and licensed under CC BY 4.0.

Suggested attribution:

> Sinay, Y. (2026). _Cyber Attribution_. GitHub. Licensed under CC BY 4.0.

## Responsible use

Do not publish sensitive indicators, victim data, personal data, intelligence sources and methods, confidential legal advice, or operational information that is not approved for release.

This repository is for educational, defensive, analytical, and policy support purposes. It does not constitute legal advice, intelligence reporting, or official government guidance unless a specific document explicitly states otherwise.
