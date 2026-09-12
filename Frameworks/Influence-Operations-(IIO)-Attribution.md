# Influence Operations (IIO) Attribution

## Purpose

This document provides a structured methodology for attribution analysis of influence operations and information influence operations (IIO). It is intended to help analysts separate observable evidence from assessment, identify uncertainty, and communicate confidence levels in a disciplined way.

## Scope

This methodology may be used for:

| Area | Analytical focus |
| --- | --- |
| Actor attribution | Identifying likely operators, sponsors, proxies, or coordinating entities |
| Campaign attribution | Linking activity across platforms, narratives, assets, personas, and time periods |
| Infrastructure attribution | Assessing domains, accounts, pages, bots, automation, paid amplification, and technical infrastructure |
| Narrative attribution | Mapping themes, framing, target audiences, and strategic intent |
| Behavioral attribution | Evaluating coordination, timing, repetition, language patterns, and operational tradecraft |
| Strategic attribution | Connecting campaign behavior to political, military, economic, or geopolitical objectives |

## Core Principle

Attribution should not be treated as a single conclusion. It should be structured as a layered assessment:

1. What was observed.
2. What can be technically or behaviorally linked.
3. What can be inferred from context.
4. What alternative explanations remain plausible.
5. What level of confidence is justified.

## Attribution Layers

| Layer | Evidence examples | Analytical question |
| --- | --- | --- |
| Content | Posts, images, videos, slogans, hashtags, documents | What message is being promoted or suppressed? |
| Narrative | Themes, frames, grievances, conspiracy claims, identity appeals | What broader story is being constructed? |
| Behavioral | Posting cadence, coordination, repetition, synchronized activity | Does the activity show organized behavior? |
| Network | Account clusters, pages, groups, communities, shared assets | Which entities appear connected? |
| Technical | Domains, hosting, metadata, links, infrastructure, automation indicators | What technical evidence links the activity? |
| Linguistic | Language, translation artifacts, style, idioms, grammar, naming patterns | Are there linguistic indicators of origin or coordination? |
| Targeting | Audiences, geography, demographics, political communities, vulnerable groups | Who is being influenced or manipulated? |
| Strategic context | Timing, geopolitical events, elections, conflict dynamics, policy debates | Who benefits and why now? |
| Control and sponsorship | Funding, direction, proxy behavior, state alignment, tasking indicators | Is there evidence of direction, support, or sponsorship? |

## Evidence Classification

| Category | Description | Examples |
| --- | --- | --- |
| Direct evidence | Evidence that directly links an actor to the operation | Leaked tasking, platform takedown attribution, authenticated operator material |
| Strong circumstantial evidence | Multiple independent indicators pointing to the same actor or sponsor | Infrastructure reuse, coordinated assets, timing, language, known tradecraft |
| Weak circumstantial evidence | Indicators that support a hypothesis but are not decisive alone | Narrative alignment, generic geopolitical benefit, stylistic similarity |
| Contextual evidence | Background information that helps explain motive or timing | Elections, military conflict, sanctions, diplomatic disputes |
| Negative evidence | Evidence that weakens or contradicts a hypothesis | Inconsistent language, incompatible timing, lack of expected infrastructure reuse |

## Confidence Levels

| Confidence | Meaning |
| --- | --- |
| High | Multiple independent evidence streams support the assessment, and credible alternatives are unlikely |
| Moderate | Evidence supports the assessment, but important gaps or plausible alternatives remain |
| Low | The assessment is possible, but evidence is limited, indirect, or contested |
| Unknown | Evidence is insufficient to support attribution |

## Analytical Workflow

1. Define the incident or campaign boundary.
2. Collect observable evidence and preserve source context.
3. Separate content, behavior, technical, network, and strategic indicators.
4. Identify coordination patterns and amplification mechanisms.
5. Map narratives, target audiences, and intended effects.
6. Compare indicators with known actor tradecraft and prior campaigns.
7. Test competing hypotheses.
8. Assign confidence level.
9. Document uncertainty and evidence gaps.
10. State the attribution assessment clearly and proportionately.

## Influence Operation Impact and Effectiveness Assessment Models

Attribution answers who is likely responsible for an operation. Impact and effectiveness assessment address different questions: how far the operation spread, what observable effects it produced, whether it caused harm, whether it achieved strategic objectives, and whether defensive responses reduced its effectiveness.

Analysts should avoid treating reach, engagement, virality, media pickup, or platform migration as automatic evidence of persuasion or strategic success. Observable dissemination should be separated from inferred cognitive, behavioral, policy, or strategic effects.

### Comparative Model Overview

| Model / Framework | Primary focus | Reach | Harm / Effect | Countermeasure effectiveness | Main analytical value |
| --- | --- | --- | --- | --- | --- |
| Breakout Scale | Observable spread and breakout | High | Limited to higher categories | No | Real-time categorization of how far an influence operation travels across communities, platforms, mainstream media, high-profile amplifiers, and policy/action domains |
| Impact-Risk Index | Impact and risk indicators | High | Moderate | No | Combines virality, engagement, language, format, media, spreaders, calls to action, and potential offline effects |
| Response-Impact Framework | Impact of defensive responses | Moderate | High | High | Assesses whether countermeasures improve awareness, reduce amplification or harm, enable attribution and action, and strengthen resilience |
| ABCDE Framework | Actor, behavior, content, degree, effect | Moderate | High | Limited | Separates the degree of dissemination from effects such as polarization, institutional discrediting, public-health or safety risks, and security consequences |
| DISARM | Adversary behavior, responses, and assessment | Moderate | High | Moderate | Connects campaign tactics and techniques with message reach, engagement, changes in knowledge, attitudes, behavior, and defensive measures |
| CIB Detection Tree | Coordinated inauthentic behavior and impact | High | Limited to Moderate | No | Supports evaluation of outreach, interaction, target effects, and polarization alongside evidence of coordination |
| NATO StratCom COE Capability Assessment Framework | Defender capability | Indirect | Indirect | High | Evaluates organizational capability to counter disinformation, information influence, and foreign interference rather than measuring one campaign's impact |

### The Breakout Scale

Nimmo's Breakout Scale is a six-category comparative model designed around observable, replicable, and verifiable evidence. It emphasizes the extent to which an influence operation moves beyond its originating platform and community.

| Category | Observable threshold | Analytical interpretation |
| --- | --- | --- |
| Category 1 | One community on one platform | Activity remains contained within its original community and platform. |
| Category 2 | One community across multiple platforms, or multiple communities on one platform | The operation breaks out in either platform or community terms, but not both. |
| Category 3 | Multiple communities across multiple social-media platforms | The operation achieves broader cross-platform and cross-community dissemination. |
| Category 4 | Mainstream-media amplification | The operation breaks out of social media and is amplified by mainstream media. |
| Category 5 | Amplification by high-profile individuals | Celebrities, political candidates, senior public figures, or other highly visible actors substantially increase exposure. |
| Category 6 | Policy response, concrete action, or call for violence | The operation generates the highest observable category of real-world consequence under the scale. |

The Breakout Scale is especially useful when analysts lack reliable evidence of audience persuasion. Its strength is the use of observable dissemination and amplification indicators rather than assumptions about psychological effect.

### Impact-Risk Index

The Impact-Risk Index is an impact-focused approach identified in comparative disinformation research. It places substantial weight on measurable reach and engagement indicators while also considering risk and potential harm.

Suggested analytical indicators include:

| Dimension | Examples |
| --- | --- |
| Virality | Speed and scale of redistribution |
| Engagement | Reactions, comments, reposts, interaction intensity |
| Language | Linguistic reach and cross-language dissemination |
| Format | Text, image, video, synthetic media, meme, or mixed format |
| Media | Movement across social, alternative, and mainstream media |
| Spreaders | Influence and audience size of amplifying actors |
| Call to action | Requests for mobilization, participation, disruption, or other action |
| Offline effect | Evidence of activity or harm beyond the information environment |

This model is useful for prioritization because a campaign with limited attribution confidence may still warrant attention if its impact-risk profile is high.

### Response-Impact Framework

The EU DisinfoLab Response-Impact Framework evaluates what happens after defenders respond to a campaign. It shifts the analytical question from "How successful was the influence operation?" to "What effect did the response have?"

The framework organizes responses into five broad categories:

1. Exposure-related responses.
2. Community-engagement responses.
3. Distribution-related responses.
4. Infrastructure-related responses.
5. Deterrence.

Representative impact areas include increased situational awareness, reduced amplification, harm mitigation, attribution and action, resilience, and increased costs or reduced benefits for threat actors.

This makes the framework complementary to the Breakout Scale: one measures observable campaign breakout, while the other helps assess whether defensive action constrained, disrupted, or mitigated the campaign.

### ABCDE Framework

The ABCDE approach separates five analytical components: Actor, Behavior, Content, Degree, and Effect. For effectiveness assessment, Degree and Effect are especially relevant.

| Component | Measurement focus |
| --- | --- |
| Degree | Cross-platform dissemination, media pickup, multilingual amplification, and scale |
| Effect | Polarization, institutional discrediting, public-health and safety risks, threats to fundamental freedoms, and security consequences |

The distinction between Degree and Effect is useful because wide dissemination does not necessarily imply meaningful harm.

### DISARM

DISARM provides a structured representation of adversary behaviors and defensive measures across influence operations. For impact assessment, it can support monitoring of message reach and social-media engagement while also examining changes in audience knowledge, attitudes, or behavior.

Its main advantage is operational integration: campaign techniques, observable effects, and countermeasures can be represented within a common analytical structure.

### CIB Detection Tree

The Coordinated Inauthentic Behavior Detection Tree is primarily designed to identify coordinated and deceptive behavior, but comparative impact research also associates it with impact indicators such as outreach, interaction, effects on targets, and polarization.

It should therefore be treated as a supporting framework rather than as a standalone strategic-effectiveness model.

### NATO StratCom COE Capability Assessment Framework

Pamment's capability assessment framework addresses a different but complementary problem: whether an organization or national system possesses appropriate capabilities to counter disinformation, information influence, and foreign interference.

It is not a campaign impact scale. Its value is in evaluating defender readiness, capability gaps, organizational design, and whether resources and processes support the desired level of counter-influence capability.

### Integrated Four-Layer Effectiveness Model

For cyber-attribution and information-influence analysis, the following four-layer structure can combine the strengths of the models above while maintaining a clear distinction between observable reach and inferred strategic effect.

| Layer | Core question | Example indicators | Evidence caution |
| --- | --- | --- | --- |
| Exposure | Who was exposed? | Reach, impressions, views, audience penetration, communities reached | Exposure does not demonstrate persuasion. |
| Amplification | How far did the content break out? | Cross-platform spread, mainstream-media pickup, influencers, high-profile amplifiers, multilingual spread | Amplification may be hostile, critical, or corrective rather than supportive. |
| Effect | Did attitudes, behavior, trust, or institutional activity change? | Mobilization, behavioral change, trust erosion, polarization, institutional response, offline action | Causal attribution requires stronger evidence than correlation. |
| Strategic Outcome | Did the operation materially advance an objective? | Policy change, operational disruption, deterrence, social destabilization, enduring narrative adoption, strategic decision effects | Strategic outcomes are usually multi-causal and should include confidence and alternative explanations. |

### Suggested Effectiveness Assessment Fields

| Field | Example question |
| --- | --- |
| Origin | Where did the narrative or content first appear? |
| Cross-platform spread | Did it move beyond the original platform, group, or language community? |
| Amplifiers | Which high-reach accounts, media organizations, public figures, or institutions amplified it? |
| Audience reach | What evidence exists regarding exposure, impressions, views, or audience penetration? |
| Engagement | Did the content generate meaningful interaction rather than passive exposure? |
| Institutional response | Did governments, media, companies, civil society, or platforms respond? |
| Behavioral effect | Is there credible evidence of changed behavior, mobilization, voting, purchasing, protest, or operational action? |
| Policy effect | Did the operation contribute to an identifiable policy, diplomatic, military, regulatory, or organizational decision? |
| Persistence | Did the narrative or effect persist after the initial campaign period? |
| Defensive response | What countermeasures were taken and what observable consequences followed? |
| Adversary adaptation | Did the actor modify infrastructure, narratives, TTPs, or distribution in response to countermeasures? |
| Confidence | How strong is the evidence that the observed effect was caused or materially influenced by the operation? |

### Assessment Principle

A recommended analytical sequence is:

**Exposure → Amplification → Effect → Strategic Outcome**

The analyst should assign evidence and confidence separately at each layer. A campaign may have high exposure and amplification while producing little demonstrated behavioral or strategic effect. Conversely, a relatively narrow campaign may generate significant strategic consequences if it reaches a highly influential target audience or decision-making process.

### References

Nimmo, B. (2020). *The Breakout Scale: Measuring the impact of influence operations*. Brookings Institution. https://www.brookings.edu/articles/the-breakout-scale-measuring-the-impact-of-influence-operations/

Pamment, J. (2022). *A capability definition and assessment framework for countering disinformation, information influence, and foreign interference*. NATO Strategic Communications Centre of Excellence. https://stratcomcoe.org/publications/a-capability-definition-and-assessment-framework-for-countering-disinformation-information-influence-and-foreign-interference/255

Serrano, R. M., & Sessa, M. G. (2024, November 29). *Beyond disinformation countermeasures: Building a response-impact framework*. EU DisinfoLab. https://www.disinfo.eu/publications/beyond-disinformation-countermeasures-building-a-response-impact-framework/

EU DisinfoLab. (2025). *Decoding disinformation impact frameworks and indicators: A comparative study*. https://www.disinfo.eu/publications/decoding-disinformation-impact-frameworks-and-indicators-a-comparative-study/

## Common Frameworks for Influence Operations (IIO) Attribution

The following tables provide a reference map of common academic, practitioner, public sector, and industry frameworks that can support IIO attribution analysis.

### Academic Research

| No. | Framework name | Publication year | Reference |
| --- | --- | --- | --- |
| 1 | Phase-based tactical analysis of online operations | 2023 | Nimmo, B., & Hutchins, E. (2023). *Phase-based tactical analysis of online operations*. Carnegie Endowment for International Peace. https://carnegieendowment.org/research/2023/03/phase-based-tactical-analysis-of-online-operations |

*Table 1. Frameworks for Influence Operations (IIO) Attribution, Academic Research.*

### Industry Research

| No. | Framework name | Publication year | Reference |
| --- | --- | --- | --- |
| 1 | AMITT, Adversarial Misinformation Influence Tactics and Techniques Framework | 2019 | Terp, S. J., & Breuer, P. (2019). *AMITT, Adversarial Misinformation Influence Tactics and Techniques Framework*. https://drive.google.com/file/d/1_4D_QyO2u3IADeYO37en3029IXUPxSZW/view |
| 2 | MITRE Disinformation Kill Chain Model | 2019, 2021 | Public-Private Analytic Exchange Program. (2019, October). *Combatting targeted disinformation campaigns: A whole-of-society issue*. U.S. Department of Homeland Security. https://permanent.fdlp.gov/gpo150650/ia_combatting-targeted-disinformation-campaigns.pdf; Public-Private Analytic Exchange Program. (2021, August). *Combatting targeted disinformation campaigns: A whole-of-society issue, Part Two*. U.S. Department of Homeland Security. https://www.dhs.gov/sites/default/files/publications/phase_ii_-_combatting_targeted_disinformation.pdf |
| 3 | The ABCDE Framework for FIMI Analysis | 2020 | Pamment, J. (2020, September). *The EU's role in fighting disinformation: Crafting a disinformation framework*. Carnegie Endowment for International Peace. https://carnegieendowment.org/files/Pamment_-_Crafting_Disinformation_1.pdf |
| 4 | The Diamond Model for Influence Operations Analysis | 2022 | Recorded Future. (2022, October 6). *The Diamond Model for Influence Operations Analysis*. https://go.recordedfuture.com/hubfs/white-papers/diamond-model-influence-operations-analysis.pdf |
| 5 | Attributing Information Influence Operations: Identifying Those Responsible for Malicious Behaviour Online | 2022 | Pamment, J., & Smith, V. (2022). *Attributing information influence operations: Identifying those responsible for malicious behaviour online*. NATO Strategic Communications Centre of Excellence and European Centre of Excellence for Countering Hybrid Threats. https://stratcomcoe.org/publications/attributing-information-influence-operations-identifying-those-responsible-for-malicious-behaviour-online/244 |
| 6 | DISARM, The Disinformation Analysis and Response Measures Framework | 2022 | DISARM Foundation. (2022). *DISARM Framework*. https://www.disarm.foundation/framework |
| 7 | Addressing attribution: Theorizing a model to identify Russian disinformation campaigns online | 2022 | Canadian Global Affairs Institute. (2022). *Addressing attribution: Theorizing a model to identify Russian disinformation campaigns online*. https://www.cgai.ca/addressing_attribution_theorizing_a_model_to_identify_russian_disinformation_campaigns_online#Defining |
| 8 | DTAC's Framework for Attributing Influence Operations | 2024 | Microsoft. (2024). *DTAC's framework for attributing influence operations*. https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2024/07/MTAC-Attribution-Model-for-Influence.pdf |
| 9 | A Framework for Attribution of Information Influence Operations | 2025 | Palmertz, B., Isaksson, E., & Pamment, J. (2025). *A framework for attribution of information influence operations*. Project Adac.io. https://adacio.eu/a-framework-for-attribution-of-information-influence-operations |
| 10 | FIMI Exposure Matrix: A Systematic Approach to Classifying and Attributing FIMI Infrastructure | 2025 | European External Action Service. (2025). *3rd EEAS report on foreign information manipulation and interference threats*. https://www.eeas.europa.eu/eeas/3rd-eeas-report-foreign-information-manipulation-and-interference-threats_en |
| 11 | Information Influence Attribution Framework | 2026 | Dikhtiarenko, S., Heap, B., Pamment, J., & Smith, V. (2026). *Attributing Russian information influence operations: Testing the Information Influence Attribution Framework with real-world case studies* (53 pp.; ISBN 978-9934-619-68-7). NATO Strategic Communications Centre of Excellence. |
| 12 | Beyond Deepfake Detection: MOSAIC, a Confidence-Aware and Counter-Deception Framework for Synthetic-Media Operation Attribution | 2026 | Sinay, Y. (2026). Beyond deepfake detection: MOSAIC, a confidence-aware and counter-deception framework for synthetic-media operation attribution. In *Proceedings of the 2nd ACM Deepfake, Deception, and Disinformation Security Workshop (3D-Sec '26)*. Association for Computing Machinery. https://doi.org/10.1145/3843205.3845625 |

*Table 2. Frameworks for Influence Operations (IIO) Attribution, Industry Research.*

## Competing Hypotheses Template

| Hypothesis | Supporting evidence | Contradicting evidence | Evidence gaps | Confidence |
| --- | --- | --- | --- | --- |
| H1: State directed operation |  |  |  |  |
| H2: State aligned proxy |  |  |  |  |
| H3: Domestic political actor |  |  |  |  |
| H4: Commercial influence-for-hire actor |  |  |  |  |
| H5: Organic community behavior |  |  |  |  |
| H6: Mixed or opportunistic activity |  |  |  |  |

## Attribution Statement Template

Based on the available evidence, the activity is assessed with [low / moderate / high] confidence to be linked to [actor / proxy / sponsor / unknown actor].

This assessment is based on [main evidence streams], including [content], [behavior], [technical indicators], [network indicators], and [strategic context].

The main uncertainty is [uncertainty]. Plausible alternative explanations include [alternatives]. Further collection should focus on [priority evidence gaps].

## Analyst Notes

Attribution of influence operations is probabilistic. Narrative alignment alone is not sufficient for attribution. Technical indicators alone may also be insufficient where proxies, cutouts, commercial providers, compromised assets, or false flag behavior are plausible.

The strongest assessments combine behavioral, technical, network, linguistic, and strategic evidence while explicitly documenting uncertainty and alternative explanations.