# Offensive Planning and Targeting Frameworks

This page lists high-level frameworks and analytic models that are commonly referenced in military, intelligence, and national-security literature when discussing offensive planning, target selection, prioritization, operational design, and integration of cyber effects into broader operations.

The purpose of this page is educational and analytical. It supports cyber-attribution, strategic assessment, threat modeling, and defensive understanding. It does not provide operational targeting instructions.

## Summary Table

| Framework | Purpose |
|---|---|
| Joint Targeting Cycle | Military targeting process |
| NATO Joint Targeting Process | Alliance targeting governance and synchronization |
| F2T2EA | Intelligence-driven targeting |
| F3EAD | High-value target operations |
| CARVER | U.S. Army target-value and vulnerability assessment technique |
| Target Systems Analysis | System-level target and dependency analysis |
| JIPOE | Joint intelligence preparation of the operational environment |
| PMESII-PT | Operational environment analysis |
| DIMEFIL | Integration of cyber into broader instruments of power |
| MDMP | Military decision-making and course-of-action development |
| OODA Loop | Decision-cycle competition |
| Cyber Kill Chain | Intrusion lifecycle analysis |
| JADC2 | Cross-domain command-and-control integration |

## Framework Descriptions

### Joint Targeting Cycle

The Joint Targeting Cycle is a structured military targeting process used to connect strategic objectives, operational planning, target development, capability selection, execution, assessment, and feedback. In cyber and cyber-attribution analysis, it is useful for understanding how target selection may be linked to broader campaign objectives rather than treated as an isolated technical event.

### NATO Joint Targeting Process

The NATO Joint Targeting Process provides an alliance-level approach for target development, prioritization, coordination, legal review, effects assessment, and synchronization across multinational operations. For cyber-attribution analysis, it is useful as a reference point for understanding how targeting may be governed, reviewed, and integrated with political and military objectives in coalition contexts.

### F2T2EA

F2T2EA stands for Find, Fix, Track, Target, Engage, and Assess. It is an intelligence-driven targeting model that emphasizes the relationship between intelligence collection, target development, operational action, and post-action assessment. In cyber analysis, it may help analysts reason about how adversaries identify, validate, prioritize, and assess targets across a campaign.

### F3EAD

F3EAD stands for Find, Fix, Finish, Exploit, Analyze, and Disseminate. It is commonly associated with high-value target operations and emphasizes the feedback loop between operations and intelligence exploitation. For cyber-attribution work, F3EAD is relevant when assessing whether a campaign shows signs of iterative intelligence gain, follow-on exploitation, and dissemination into wider operational planning.

### CARVER

CARVER stands for **Criticality, Accessibility, Recuperability, Vulnerability, Effect, and Recognizability**. In U.S. Army doctrine it is identified as a target-assessment and target-value analysis technique. Historical U.S. Army Special Operations Forces doctrine also describes CARVER as a method used during target analysis, mission planning, and technical appreciation. More recent Army publications continue to reference it for target prioritization, critical-vulnerability analysis, threat-systems analysis, and protection assessment.

The six criteria are:

| Criterion | Defensive and Attribution Interpretation |
|---|---|
| Criticality | How important the asset, service, dependency, or function is to mission or strategic objectives. |
| Accessibility | How reachable or exposed the asset is from the adversary's perspective, including technical, organizational, physical, or supply-chain access paths. |
| Recuperability | How rapidly the defender can restore, replace, reconstitute, or work around the affected function. |
| Vulnerability | Whether an adversary plausibly possesses the capability and opportunity to affect the target. |
| Effect | The operational, strategic, economic, political, societal, or cascading consequences that could follow successful compromise or disruption. |
| Recognizability | How easily an adversary can identify, classify, locate, or distinguish the target and confirm that an effect has occurred. |

For cyber attribution, CARVER is most useful as a **hypothesis-generation and victimology framework**. It can help analysts ask why a particular organization, dependency, platform, cloud service, identity provider, telecommunications node, industrial control environment, or supply-chain component may have been selected. A target set that repeatedly concentrates on highly critical, difficult-to-recover, exposed, and readily identifiable assets may indicate deliberate prioritization rather than opportunistic scanning alone.

CARVER can also support comparative analysis across incidents. Analysts may examine whether multiple victims share similar characteristics, whether the adversary appears to understand recovery dependencies, and whether target choice aligns with broader political or military timing. These patterns can strengthen an operational assessment when combined with malware, infrastructure, TTP, intelligence, geopolitical, and temporal evidence.

CARVER should **not** be treated as proof of attribution. Many actors can independently prioritize attractive targets using similar logic. A CARVER-like pattern therefore provides contextual evidence about possible adversary planning and intent, but it does not identify an actor by itself. It should be used alongside alternative-hypothesis testing and confidence assessment.

**U.S. Army references:**

- Headquarters, Department of the Army. (2024). *FM 1-02.1, Operational Terms*. CARVER is defined as "criticality, accessibility, recuperability, vulnerability, effect, and recognizability" and identified as a target assessment technique.
- Headquarters, Department of the Army. (2018). *ATP 3-13.1, The Conduct of Information Operations*. CARVER is described as a methodology for weighing and ranking six target criteria to support targeting and planning decisions.
- Headquarters, Department of the Army. *ATP 2-01.3, Intelligence Preparation of the Battlefield/Battlespace*. CARVER is described as a target-value analysis tool used to identify and prioritize specific targets.
- Headquarters, Department of the Army. *FM 34-36, Special Operations Forces Intelligence and Electronic Warfare Operations*, Appendix D. Historical Army SOF doctrine describes the CARVER target-analysis process and its use in mission planning and technical appreciation.

### Target Systems Analysis

Target Systems Analysis examines targets as parts of larger systems, including dependencies, functions, nodes, links, vulnerabilities, and potential second-order effects. In cyber analysis, this model is especially useful for understanding why an adversary may focus on identity providers, managed service providers, cloud control planes, telecommunications, logistics, energy, or software supply-chain dependencies.

### JIPOE

JIPOE stands for Joint Intelligence Preparation of the Operational Environment. It supports structured understanding of the operational environment, adversary capabilities, terrain, systems, constraints, and likely courses of action. In cyber-attribution, JIPOE can help analysts frame technical activity within a broader operational environment that includes geography, infrastructure, organizations, dependencies, doctrine, and political context.

### PMESII-PT

PMESII-PT stands for Political, Military, Economic, Social, Information, Infrastructure, Physical Environment, and Time. It is used to analyze the operational environment and system-level conditions. In cyber analysis, PMESII-PT helps connect technical intrusions to broader strategic conditions, such as political crises, economic pressure, military operations, information campaigns, infrastructure dependencies, and timing.

### DIMEFIL

DIMEFIL extends the traditional DIME model of national power by including Diplomatic, Information, Military, Economic, Financial, Intelligence, and Law Enforcement instruments. In cyber operations analysis, DIMEFIL is useful for understanding cyber activity as one instrument within a broader state or strategic campaign, especially when technical activity is combined with influence, sanctions, intelligence activity, legal measures, or diplomatic signaling.

### MDMP

MDMP stands for Military Decision-Making Process. It is a structured planning method for mission analysis, course-of-action development, comparison, approval, and orders production. For cyber-attribution work, MDMP can help analysts understand how cyber activity may be linked to planned objectives, constraints, decision points, risk assessment, and operational sequencing.

### OODA Loop

The OODA Loop stands for Observe, Orient, Decide, and Act. It is a decision-cycle model used to understand tempo, adaptation, and competitive advantage. In cyber campaigns, adversaries may attempt to compress their own decision cycle while slowing the defender's ability to observe, orient, decide, and act. This is relevant to attribution when a campaign shows rapid adaptation to defender behavior or public reporting.

### Cyber Kill Chain

The Cyber Kill Chain is an intrusion lifecycle model that describes common phases of cyber operations from preparation through action on objectives. In this page, it is treated as an analytic framework rather than an operational guide. It helps analysts organize evidence, identify campaign maturity, map observable activity, and compare actor tradecraft over time.

### JADC2

JADC2 stands for Joint All-Domain Command and Control. It refers to the integration of sensors, data, decision-making, and effects across domains. In cyber-attribution and campaign analysis, JADC2 is relevant as a strategic concept for understanding how cyber operations may be synchronized with space, air, land, sea, electromagnetic, information, and intelligence activities.

## Use in Cyber Attribution

These frameworks can support attribution analysis by helping analysts distinguish between tactical technical activity and broader operational intent. They are especially useful when assessing:

| Analytic Question | Relevance |
|---|---|
| Why was this target selected? | Helps connect victimology, sector, geography, dependency, timing, and symbolic value to strategic objectives. |
| Was the operation isolated or campaign-based? | Helps identify planning logic, sequencing, operational tempo, and feedback loops. |
| What role did intelligence collection play? | Helps distinguish destructive, coercive, espionage, preparatory, and influence-supporting activity. |
| How does cyber activity relate to other instruments of power? | Helps assess whether cyber effects are integrated with diplomatic, information, military, economic, financial, intelligence, or law-enforcement activity. |
| What indicators suggest prioritization? | Helps assess whether target choice reflects criticality, accessibility, expected effect, dependency concentration, or recognizability. |
| Does the activity reflect system-level thinking? | Helps identify whether the actor is targeting a single victim, a sector, a supply chain, a platform, or a national-level dependency. |
| Does the campaign show adaptive learning? | Helps identify whether the actor is shortening its decision cycle, exploiting defender responses, or using feedback from previous activity. |

## Suggested Mapping to Cyber Analysis

| Cyber Analysis Need | Relevant Frameworks |
|---|---|
| Victimology and target selection | CARVER, Target Systems Analysis, Joint Targeting Cycle |
| Campaign sequencing | Joint Targeting Cycle, F2T2EA, F3EAD, Cyber Kill Chain |
| Operational environment | JIPOE, PMESII-PT, DIMEFIL |
| Strategic integration | DIMEFIL, JADC2, NATO Joint Targeting Process |
| Decision tempo and adaptation | OODA Loop, MDMP, F3EAD |
| Dependency and systemic risk | Target Systems Analysis, PMESII-PT, CARVER |

## Caution for Analysts

These frameworks should be used as analytic lenses, not as proof of attribution. Similar planning logic can appear across different actors, including states, proxies, criminal groups, hacktivists, and hybrid actors. Analysts should combine these frameworks with technical evidence, infrastructure analysis, malware analysis, victimology, timing, geopolitical context, confidence scoring, and alternative hypothesis testing.

Analysts should also avoid overfitting. A cyber incident may appear to match a military planning framework even when the activity was opportunistic, criminal, experimental, or driven by access availability rather than deliberate strategic targeting.

## Related Repository Topics

- Cyber Attribution Frameworks
- Structured Analytic Techniques
- Confidence Scoring Frameworks
- Incident Response Frameworks
- Influence Operations Attribution
- False Flag Cyber Operations
- Cyber Threat Intelligence
- Crisis Level Cyber State Frameworks
