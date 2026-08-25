# Living Document Model

The stable part is the meaning of the documents, not their file names, storage product, or granularity.

## Persistence Boundary

A workspace is a user-designated persistent location such as a repository directory, a document set, or a knowledge base.

- If no workspace is designated, keep a session-only draft and state that nothing was persisted.
- If a workspace is designated, locate existing semantic equivalents before creating anything.
- Preserve the medium's native structure, existing relevant content, links, and evidence.
- Make the narrowest update that brings the documents to the current best understanding.
- Never duplicate the same source of truth merely to fit the default file names below.

For a small local project, the default shape may be:

```text
REQUIREMENTS.md
PLAN.md
ENGINEERING_NOTES.md
```

For a larger project, Engineering Notes may be a directory organized by technical area. Choose granularity from project scale and navigation needs.

## 1. Requirements

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

## 2. Engineering Plan

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

## 3. Engineering Notes

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

## Updating After Evidence

For each new evidence item:

1. confirm its source, version, conditions, and what it actually demonstrates;
2. update Requirements if the needed outcome, constraint, or success condition changed;
3. update the Plan if the next phase, ordering, or acceptance evidence changed;
4. update Engineering Notes with the evidence-to-decision reasoning;
5. remove or rewrite obsolete current-state claims instead of leaving conflicting versions in place.

Do not create change-request identifiers or a parallel change ledger. If the host project requires formal traceability, respect that external policy, but do not make it part of this skill's core document model.
