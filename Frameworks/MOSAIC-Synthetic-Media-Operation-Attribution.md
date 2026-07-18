# MOSAIC: Synthetic-Media Operation Attribution

**Author:** Yuval Sinay  
**Year:** 2026  
**Version:** 1.0

## Purpose

MOSAIC is an analyst-oriented framework for attributing synthetic-media operations. It supports structured analysis of manipulated or AI-generated images, audio, video, text, and multimodal content while separating media authenticity assessment from conclusions about the operator, sponsor, or beneficiary.

The framework is designed for cyber threat intelligence, information influence operations, FIMI analysis, incident response, law enforcement support, strategic communications, and national-security assessment.

## Core Principle

Evidence that content is synthetic or manipulated does not, by itself, identify who created, distributed, directed, or sponsored the operation. Attribution should combine independent evidence streams, test competing hypotheses, document uncertainty, and express conclusions proportionately.

## MOSAIC Analytical Dimensions

| Dimension | Analytical focus | Key questions |
| --- | --- | --- |
| **M — Media** | The synthetic or manipulated artifact and its observable characteristics | What was created or altered? Which modalities, narratives, personas, or targets are involved? What forensic indicators are present? |
| **O — Origin** | Provenance, earliest appearance, source lineage, and likely production context | Where and when did the content first appear? Can its creation, upload, or transformation history be reconstructed? |
| **S — Systems** | Models, tools, platforms, accounts, infrastructure, and distribution mechanisms | Which generation tools, editing systems, hosting services, domains, account clusters, automation, or amplification mechanisms supported the operation? |
| **A — Activity** | Operational behavior, coordination, timing, sequencing, targeting, and campaign continuity | How was the content deployed? Does the activity show synchronized posting, cross-platform coordination, paid amplification, laundering, or reuse of established tradecraft? |
| **I — Identity** | Actor, operator, proxy, sponsor, and beneficiary hypotheses | Which individuals, groups, commercial providers, proxies, or state-aligned entities may be responsible? What evidence links control, tasking, funding, or sponsorship? |
| **C — Confidence** | Evidence quality, corroboration, alternatives, gaps, and confidence language | How strong and independent are the evidence streams? Which alternative explanations remain plausible? What confidence level is justified? |

## Analytical Workflow

1. Define the synthetic-media incident or campaign boundary.
2. Preserve the original artifacts, metadata, URLs, timestamps, platform context, and chain of custody where applicable.
3. Assess the media without assuming that detection of manipulation establishes attribution.
4. Trace origin and provenance, including the earliest observable publication and derivative versions.
5. Map supporting systems, accounts, infrastructure, model indicators, and distribution channels.
6. Analyze activity patterns, coordination, targeting, narrative alignment, and operational continuity.
7. Develop identity hypotheses for creators, operators, proxies, sponsors, and beneficiaries.
8. Test competing hypotheses and actively search for contradictory or negative evidence.
9. Assign confidence separately to artifact assessment, campaign linkage, operator attribution, and sponsor attribution.
10. State the assessment, limitations, alternatives, and priority intelligence gaps.

## Evidence Matrix

| Evidence stream | Examples | Main limitation |
| --- | --- | --- |
| Media forensics | Encoding anomalies, visual artifacts, audio inconsistencies, edit traces, detector results | Detection tools may produce false positives, false negatives, or model-dependent results |
| Provenance | Content credentials, metadata, hashes, upload history, archived copies, source lineage | Metadata may be absent, stripped, fabricated, or altered |
| Technical infrastructure | Domains, hosting, IP space, redirectors, telemetry, automation services | Infrastructure may be shared, compromised, rented, or deliberately misleading |
| Platform and account behavior | Account creation patterns, coordinated posting, shared assets, synchronized engagement | Coordination does not necessarily identify the controlling actor |
| Linguistic and stylistic indicators | Language use, translation artifacts, recurrent phrasing, persona consistency | Style can be imitated, translated, or generated to create false attribution cues |
| Operational tradecraft | Timing, sequencing, laundering, proxy use, target selection, campaign reuse | Tradecraft may be copied or intentionally framed as another actor |
| Strategic context | Motive, opportunity, beneficiary analysis, geopolitical timing | Benefit or narrative alignment alone is insufficient for attribution |
| Direct evidence | Authenticated tasking, financial records, operator access, platform disclosures, credible leaks | Direct evidence may be unavailable, incomplete, contested, or sensitive |

## Confidence Model

MOSAIC recommends separate confidence statements for distinct attribution layers:

| Layer | Example assessment |
| --- | --- |
| Artifact assessment | The media is synthetic or materially manipulated |
| Campaign linkage | Multiple artifacts and accounts are part of the same coordinated operation |
| Operator attribution | A specific actor or service operated the campaign |
| Sponsor attribution | A state, organization, or principal directed, funded, or controlled the operation |
| Strategic assessment | The operation served an identifiable political, military, economic, or social objective |

Use **high**, **moderate**, **low**, or **unknown** confidence and explain the evidence basis, contradictions, and remaining gaps for each layer.

## Competing Hypotheses Template

| Hypothesis | Supporting evidence | Contradicting evidence | Evidence gaps | Confidence |
| --- | --- | --- | --- | --- |
| H1: State-directed operation |  |  |  |  |
| H2: State-aligned proxy or contractor |  |  |  |  |
| H3: Commercial influence-for-hire activity |  |  |  |  |
| H4: Domestic political or ideological actor |  |  |  |  |
| H5: Criminal, fraudulent, or financially motivated actor |  |  |  |  |
| H6: Independent creator or organic diffusion |  |  |  |  |
| H7: Deliberate false-flag operation |  |  |  |  |
| H8: Mixed, opportunistic, or multi-actor activity |  |  |  |  |

## Attribution Statement Template

Based on the available evidence, the media is assessed with **[confidence]** confidence to be **[synthetic / manipulated / authentic / undetermined]**. The associated activity is assessed with **[confidence]** confidence to constitute **[a coordinated operation / organic dissemination / undetermined activity]**.

The operation is assessed with **[confidence]** confidence to be linked to **[operator, proxy, sponsor, or unknown actor]**. This assessment is based on evidence from **[Media, Origin, Systems, Activity, Identity]**. The principal uncertainties are **[gaps]**, and plausible alternatives include **[hypotheses]**. Further collection should prioritize **[requirements]**.

## Analytical Safeguards

- Do not treat a synthetic-media detector score as proof of manipulation or authorship.
- Do not infer actor identity solely from language, visual style, narrative alignment, or beneficiary analysis.
- Distinguish content creation from distribution, amplification, direction, funding, and sponsorship.
- Record source reliability, evidence integrity, and collection conditions.
- Use multiple independent evidence streams and preserve negative evidence.
- Consider compromised accounts, shared infrastructure, contractors, proxies, and false flags.
- Require human review before public attribution, legal action, sanctions, or operational response.
- Reassess conclusions when new provenance, platform, or intelligence information becomes available.

## Scope Note

This MOSAIC framework was developed by Yuval Sinay for synthetic-media operation attribution. It is independent of, and should not be confused with, other initiatives or frameworks that use the name “Mosaic,” including the DARPA Mosaic Warfare concept.

## Recommended Citation

Sinay, Y. (2026). *MOSAIC: Synthetic-media operation attribution* [Analytical framework]. Cyber Attribution. https://github.com/yuval14/Cyber-Attribution/blob/main/Frameworks/MOSAIC-Synthetic-Media-Operation-Attribution.md

## License

This original framework is authored by Yuval Sinay and is licensed under the repository’s CC BY 4.0 terms.