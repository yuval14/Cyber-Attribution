# Investigation Techniques for Cyber Attribution

This page provides a practical set of structured analytic techniques that can be used during cyber attribution investigations, including LLM assisted investigations. The goal is to improve reasoning discipline, expose uncertainty, test alternative explanations, and prevent premature attribution.

These techniques support analysis. They do not replace forensic validation, source reliability assessment, legal review, or intelligence oversight.

## Summary

| No. | Technique | Main question | Attribution value | Typical output |
|---:|---|---|---|---|
| 1 | Key Assumptions Check | What must be true for the current assessment to hold? | Surfaces hidden assumptions and fragile reasoning | Assumption register and collection gaps |
| 2 | Analysis of Competing Hypotheses (ACH) | Which hypothesis is least inconsistent with the evidence? | Tests multiple plausible explanations side by side | ACH matrix and surviving hypotheses |
| 3 | Devil's Advocacy | What is the strongest case against the current judgment? | Challenges confirmation bias and weak evidence | Challenge memo and evidence gap list |
| 4 | Pre-Mortem Analysis | How could this attribution judgment later prove wrong? | Identifies failure modes before publication or escalation | Failure scenarios and mitigation actions |

## Where the Techniques Fit in an Attribution Workflow

1. Define the incident, scope, victimology, and operational timeline.
2. Separate observations from inferences and externally sourced reporting.
3. Build candidate attribution hypotheses.
4. Run the four techniques in sequence or as peer review gates.
5. Revise confidence language and identify collection requirements.
6. Document what is known, what is inferred, what remains uncertain, and why.

## 1. Key Assumptions Check

### Purpose

A Key Assumptions Check identifies the assumptions that must be true for an attribution judgment to remain valid. It is useful when an assessment appears strong but depends on context, past reporting, vendor clustering, or presumed actor behavior.

### Inputs

| Input | Description |
|---|---|
| Initial judgment | The current attribution statement and confidence level |
| Evidence list | Technical indicators, TTPs, infrastructure, malware, timing, victimology, and reporting |
| Context | Geopolitical timing, campaign history, targeting logic, and known actor behavior |
| Source notes | Origin, reliability, corroboration, and limitations of each source |

### Method

1. State the current judgment in one sentence.
2. List every assumption required for that judgment to be true.
3. Mark each assumption as evidence supported, inferred, contextual, or uncertain.
4. Rate each assumption by criticality and confidence.
5. Identify assumptions that would materially change the attribution if proven false.
6. Convert weak assumptions into collection tasks.

### Template

| Assumption | Type | Criticality | Confidence | What could disprove it? | Follow up action |
|---|---|---|---|---|---|
| The observed infrastructure is controlled by the assessed actor | Inferred | High | Evidence that the infrastructure was reused, leased, compromised, or shared | Validate infrastructure history and ownership changes |
| Malware similarity reflects actor continuity rather than tool reuse | Inferred | High | Evidence that the tool is public, leaked, sold, or used by multiple actors | Compare code, build artifacts, and operational context |

### Output

The output is an assumption register that tells the analyst which parts of the assessment are solid, which are fragile, and which require additional collection.

## 2. Analysis of Competing Hypotheses (ACH)

### Purpose

ACH compares multiple attribution hypotheses against the same evidence set. Instead of asking which hypothesis looks most attractive, ACH asks which hypotheses are most inconsistent with the evidence. Diagnostic evidence should receive more weight than evidence that fits many hypotheses.

### Example Hypotheses

| Hypothesis | Description |
|---|---|
| H1 | A state intelligence service conducted the operation directly |
| H2 | A contractor or proxy conducted the operation on behalf of a state |
| H3 | A criminal actor reused tools, infrastructure, or tradecraft associated with the state actor |
| H4 | The operation was designed as a false flag or deception effort |

### Method

1. Define mutually distinguishable hypotheses.
2. List evidence and assumptions separately.
3. Score each item against each hypothesis.
4. Focus on inconsistency and diagnosticity, not only support.
5. Remove or weaken hypotheses that are strongly inconsistent with reliable evidence.
6. Preserve plausible alternatives when evidence remains ambiguous.

### ACH Matrix Template

Use simple marks consistently:

| Mark | Meaning |
|---|---|
| C | Consistent |
| I | Inconsistent |
| N | Neutral or not diagnostic |
| ? | Unknown or requires collection |

| Evidence item | H1 | H2 | H3 | H4 | Notes |
|---|---:|---:|---:|---:|---|
| Joint advisory links activity to a known actor cluster | C | C | N | ? | Supports cluster association, but not necessarily direct state control |
| Infrastructure previously used by multiple operators | I | C | C | C | Weakens direct control claim |
| Victimology matches strategic state interest | C | C | N | C | Supports motive, but is not independently decisive |

### Output

The output is a short finding that states which hypotheses were rejected, which remain plausible, and what evidence would distinguish between the surviving explanations.

## 3. Devil's Advocacy

### Purpose

Devil's Advocacy deliberately challenges the leading attribution judgment. It is useful before public attribution, legal escalation, sanctions, diplomatic action, or high impact defensive measures.

### Method

1. Assign an analyst or reviewer to argue against the current judgment.
2. Identify the strongest alternative explanation.
3. Challenge source reliability, evidence freshness, clustering logic, and confidence language.
4. Ask whether the evidence proves actor identity, actor control, operational sponsorship, or only technical similarity.
5. Produce a challenge memo with evidence gaps and suggested wording changes.

### Challenge Questions

| Area | Questions |
|---|---|
| Technical evidence | Could malware, infrastructure, tooling, or TTPs have been reused or copied? |
| Source reliability | Is the key evidence independently corroborated? |
| Actor control | Does the evidence show direct control, sponsorship, tolerance, or only association? |
| Deception | Could the operation include false flags, planted artifacts, or misleading infrastructure? |
| Confidence | Is the confidence level stronger than the evidence justifies? |

### Output

The output is a challenge memo that improves the assessment, even if the original judgment remains unchanged. The memo should identify what would make the judgment stronger, weaker, or more precise.

## 4. Pre-Mortem Analysis

### Purpose

A Pre-Mortem asks the team to imagine that the attribution judgment was later proven wrong and then explain why. This helps identify failure modes before the assessment is finalized.

### Method

1. Assume the assessment has failed six months after release.
2. List the most plausible reasons for failure.
3. Identify which failure modes are preventable through additional collection, wording changes, or peer review.
4. Add mitigations before the assessment is used for decision making.

### Failure Mode Template

| Failure mode | How it could happen | Impact on attribution | Mitigation |
|---|---|---|---|
| Shared contractor activity | A contractor served several state or non state clients | Direct state attribution becomes overstated | Distinguish actor cluster from sponsor and control |
| Tool reuse | A second actor reused malware, scripts, or infrastructure | Technical similarity becomes less diagnostic | Require corroborating evidence beyond tool overlap |
| False flag | The actor planted misleading artifacts | Attribution points toward the wrong sponsor | Test deception indicators and require independent corroboration |
| Vendor over clustering | Separate campaigns were merged into one actor cluster | Actor continuity is overstated | Review cluster criteria and confidence thresholds |

### Output

The output is a list of failure scenarios, mitigation actions, and recommended changes to confidence language.

## LLM Supported Use

LLMs can help structure analysis, generate alternative hypotheses, and stress test reasoning. They should not be treated as evidence sources unless their output is grounded in verifiable material supplied by the analyst.

### Example Prompts

| Technique | Prompt |
|---|---|
| Key Assumptions Check | List the assumptions required for this attribution judgment to be true. Separate evidence supported assumptions from inferred assumptions. |
| ACH | Build an ACH matrix for the following hypotheses and evidence items. Identify which evidence is diagnostic and which hypotheses remain plausible. |
| Devil's Advocacy | Challenge this attribution assessment. Identify weak evidence, alternative explanations, and overconfident wording. |
| Pre-Mortem | Assume this attribution judgment is proven wrong in six months. List the most likely reasons and propose mitigations. |

### LLM Guardrails

| Risk | Control |
|---|---|
| Fabricated evidence | Use only analyst supplied evidence or cited sources |
| Overconfident wording | Require confidence language and uncertainty notes |
| Source laundering | Preserve source origin, date, and reliability notes |
| Hidden assumptions | Ask the model to list assumptions before conclusions |
| Confirmation bias | Require at least two plausible alternative hypotheses |

## Example Confidence Adjustment

| Stage | Judgment |
|---|---|
| Before structured techniques | High confidence attribution to MSS based on a joint advisory |
| After structured techniques | Moderate confidence attribution to MSS based on the joint advisory and prior examples of contractors serving multiple clients |

The adjustment does not necessarily reject the original attribution. It makes the judgment more precise by distinguishing actor cluster, sponsorship, control, and confidence.

## Recommended Use in Repository Outputs

When writing cyber attribution assessments, include a short reasoning discipline section:

| Field | Example |
|---|---|
| Techniques used | Key Assumptions Check, ACH, Devil's Advocacy, Pre-Mortem |
| Main assumptions | Infrastructure control, tool exclusivity, actor continuity |
| Alternatives considered | State service, contractor or proxy, criminal reuse, false flag |
| Evidence gaps | Control evidence, independent corroboration, infrastructure reuse history |
| Confidence impact | Confidence reduced from high to moderate pending additional corroboration |

## References

Caltagirone, S., Pendergast, A., & Betz, C. (2013). *The diamond model of intrusion analysis*. ThreatConnect.

Heuer, R. J., Jr. (1999). *Psychology of intelligence analysis*. Center for the Study of Intelligence, Central Intelligence Agency.

Janis, I. L. (1972). *Victims of groupthink: A psychological study of foreign-policy decisions and fiascoes*. Houghton Mifflin.

Klein, G. (2007). Performing a project premortem. *Harvard Business Review, 85*(9), 18-19.

Office of the Director of National Intelligence. (2018). *A guide to cyber attribution*. Cyber Threat Intelligence Integration Center.

Pherson, R. H., & Heuer, R. J., Jr. (2021). *Structured analytic techniques for intelligence analysis* (3rd ed.). CQ Press.

Rid, T., & Buchanan, B. (2015). Attributing cyber attacks. *Journal of Strategic Studies, 38*(1-2), 4-37. https://doi.org/10.1080/01402390.2014.977382
