# Living Document Model

Requirements, Engineering Plan, and Engineering Notes are three stable **semantic lanes**, not a mandate to create exactly three files or place everything on one page. The chosen workspace should make those lanes easy to navigate, update, and relate without duplicating their source of truth.

## Persistence Boundary

A workspace is a user-designated persistent location such as a repository directory, a document set, or a knowledge base.

- If no workspace is designated, keep a session-only draft and state that nothing was persisted.
- If a workspace is designated, locate existing semantic equivalents before creating anything.
- Preserve the medium's native structure, existing relevant content, links, and evidence.
- Make the narrowest update that brings the documents to the current best understanding.
- Never duplicate the same source of truth merely to fit the default file names below.
- Preserve useful links between the lanes so a reader can move from a requirement to its plan, evidence, and current judgment.

For a small local project, the default shape may be:

```text
REQUIREMENTS.md
PLAN.md
ENGINEERING_NOTES.md
```

For a larger project, Engineering Notes may be a directory organized by technical area. Choose granularity from project scale and navigation needs.

## Discovery Hub

For a multi-page package, add a thin discovery hub. It is a navigation and orientation surface, not a fourth source of truth. Keep only:

- the current conclusion and current focus;
- a short reading route;
- links or a child-page index for the semantic lanes and supporting views;
- one overview diagram showing how problem, evidence, next iteration, and feedback relate;
- the most consequential open questions.

Do not copy the complete Requirements or Plan into the hub.

## When to Split

Keep one page when the work has one near-term iteration, a single audience, and a small evidence base. Split into linked pages when one or more of these conditions applies:

- Requirements, Plan, and Notes change at different rates;
- system-state reference material obscures the current problem or current focus;
- several technical domains need independent reading routes;
- evidence and external research are substantial enough to need their own index;
- the page has become a long sequence of unrelated tables, phases, and judgments;
- different readers need an overview, an implementation-facing plan, or a technical deep dive.

Split by stable responsibility, not by arbitrary page length. A page should answer one primary reader question.

## Naming Grammar

Use one language and one separator style within a workspace. Prefer concise role-first names:

```text
<Project>｜<Topic> Engineering Discovery        # package root, or localized equivalent
00｜Requirements Baseline: Problem and Boundaries
01｜System State: Architecture and Evidence
02｜Evolution Roadmap: Phases and Acceptance
03｜Technical Reasoning: Alternatives and Open Questions
04｜Evidence Index: Internal Sources and External Research
```

The package root is the discovery hub. Localize the role names to the workspace language; do not mix bilingual synonyms in every title. Use dates only for immutable snapshots or periodic reports, not for living pages. Reserve `00` for the first baseline page and order the rest by reading flow. Omit pages that have no real content.

## Lane 1: Requirements

Answers: **What are we actually trying to solve?**

```markdown
# Requirements

## Problem
The concrete engineering problem and its impact.

## Context
Relevant current-system state and evidence.

## Goals
Desired outcomes for the current direction.

## Constraints
Business, technical, operational, safety, compatibility, and authority limits.

## Success Criteria
Observable conditions that determine whether the current iteration succeeds.

## Scope
What is in the current scope and what is explicitly deferred.

## Current Requirements
Requirements supported by the current understanding.

## Open Questions
Decision-relevant unknowns, their impact, and closure evidence.
```

Write requirements as needed outcomes or constraints. Avoid embedding an implementation choice unless it is itself a verified constraint or confirmed decision.

## Lane 2: Engineering Plan

Answers: **What is the current best path from here?**

```markdown
# Engineering Plan

## Current State
What exists, what is verified, and what remains uncertain.

## Overall Approach
The present technical direction and why it fits the evidence.

## Phase 1
Goal, reason for doing it now, main work, boundaries, and acceptance evidence.

## Phase 2
The next likely phase at the level of detail current evidence supports.

## Later Phases
Coarser directions that should not be mistaken for commitments.

## Current Focus
The one iteration currently ready to hand off.

## Next
What will be reconsidered after Current Focus produces evidence.
```

Make the nearest phase concrete and testable. Keep later phases progressively coarser. Do not elaborate distant implementation detail merely to make the plan look complete.

## Lane 3: Engineering Notes

Answers: **Why do the current requirements and plan look this way?**

Keep only knowledge that changes or supports an engineering decision:

```markdown
# Engineering Notes

## Topic

### Question
The decision-relevant technical question.

### Evidence
Code, logs, simulation, tests, field observations, or authoritative research.

### Alternatives
Viable options and the conditions under which each fits.

### Current Finding
The current interpretation, with assumptions marked.

### Experiments
Completed experiments and results, or proposed evidence-gathering work clearly marked as not yet run.

### Conclusion
The present decision and what evidence would reopen it.
```

Do not turn Engineering Notes into a general textbook, raw log dump, or project diary.

Supporting views such as System State and Evidence Index belong beside these lanes when they improve navigation. They must link back to the requirement or decision they support rather than becoming isolated archives.

## Visual Coverage

Audit each important section for relationships that prose hides:

- architecture and dependencies;
- runtime or decision flow;
- state transitions and failure paths;
- phased evolution and acceptance gates;
- alternatives, tradeoffs, or causal chains;
- evidence provenance and confidence.

Use multiple focused diagrams instead of one oversized map. Label observed/current elements separately from proposed/future elements, and mark assumptions visibly. A diagram is evidence communication, not proof by itself.

## Updating After Evidence

For each new evidence item:

1. confirm its source, version, conditions, and what it actually demonstrates;
2. update Requirements if the needed outcome, constraint, or success condition changed;
3. update the Plan if the next phase, ordering, or acceptance evidence changed;
4. update Engineering Notes with the evidence-to-decision reasoning;
5. remove or rewrite obsolete current-state claims instead of leaving conflicting versions in place.

Do not create change-request identifiers or a parallel change ledger. If the host project requires formal traceability, respect that external policy, but do not make it part of this skill's core document model.
