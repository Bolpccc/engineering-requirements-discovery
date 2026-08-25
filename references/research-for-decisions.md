# Research for Engineering Decisions

Use public research to reduce a decision-relevant unknown, not to make the document look comprehensive.

## Start from the Decision

Write the research question in this form:

```text
We need to know <specific unknown>
because it changes <requirement, alternative, phase, or acceptance rule>.
We only need enough evidence to decide <next engineering choice>.
```

Do not search private repository names, customer data, credentials, unpublished incidents, or other sensitive details. Generalize the symptom and environment when searching public sources.

## Build a Diverse Evidence Portfolio

Cover the source types that can change the decision:

1. **Mechanism and contract** — official documentation, standards, source code, maintainer design notes, and primary research.
2. **Observed failures** — upstream issues, bug reports, ROS Answers, Stack Overflow, forums, postmortems, and reproducible community reports.
3. **Alternatives** — competing architectures, algorithms, tools, or mitigations and the conditions under which each works.
4. **Counterevidence** — failure cases, rejected approaches, negative results, and reports that contradict the apparent consensus.
5. **Operational fit** — environment, version, scale, hardware, safety boundary, and workload differences between the source and the current system.

Use primary sources for factual behavior and API contracts. Use community posts as experience evidence, not universal proof. Prefer several independent perspectives over many copies of the same claim.

## Evidence Card

For each material source, capture:

- **Claim:** what the source actually supports;
- **Source:** title, direct link, author or project, and publication/update date when available;
- **Evidence type:** official contract, source code, issue report, benchmark, paper, postmortem, or anecdote;
- **Environment:** relevant version, hardware, scale, configuration, and operating conditions;
- **Direction:** supports, contradicts, or qualifies the current assumption;
- **Applicability:** why it is or is not transferable to the current system;
- **Confidence:** high, medium, or low, with a short reason;
- **Decision impact:** what changes if the claim holds.

Separate quotations and observed facts from your inference. Link citations near the claims they support.

## Search Shape

Search along several angles rather than repeatedly rephrasing one query:

- component or algorithm mechanism;
- exact symptom and error semantics;
- configuration and version interactions;
- comparable incidents and fixes;
- alternatives and tradeoffs;
- safety, performance, or failure-mode counterexamples.

For technical questions, prefer current primary sources and verify version-sensitive facts. When high-stakes safety or operational conclusions are involved, public research can frame the next test but cannot replace current-system evidence or field acceptance.

## Stop Condition

Stop when:

- authoritative behavior is established;
- at least one serious alternative or counterposition has been examined;
- important environment differences are understood;
- the evidence is sufficient to choose the next iteration or phrase the remaining open question precisely.

Do not continue merely to increase the number of links. If sources conflict, preserve the conflict and define what current-system evidence would resolve it.

## Integrate Without Polluting the Core Documents

- **Requirements:** include only resulting needs, constraints, and success conditions.
- **Engineering Plan:** include the chosen implication and its acceptance evidence.
- **Engineering Notes:** keep the synthesis, alternatives, applicability limits, and unresolved conflicts.
- **Evidence Index:** keep source cards and links when the portfolio is substantial.

If browsing is unavailable, write a precise research brief and leave the claim unresolved. Never invent sources or present memory as current verification.
