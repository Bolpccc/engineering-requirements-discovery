# Requirements Interview

Use this reference for a fresh discovery session, a resumed session, or a return prompted by new engineering evidence.

## 1. Intake the Actual Input

Accept a brain dump, transcript, sketches, existing documents, a bug history, or a short goal. Do not make the user restate it in a form.

Extract what is already present before asking anything:

- the observed problem and who or what experiences it;
- why it matters now;
- the desired outcome;
- constraints and exclusions;
- claimed success conditions;
- current implementation and prior attempts;
- assumptions, contradictions, and unknowns;
- any named workspace for persistent documents.

State the current interpretation briefly. Surface materially different readings instead of silently choosing one.

## 2. Inspect the Existing System

When the work concerns an existing system, inspect only the relevant context:

- architecture and component boundaries;
- current implementation and reusable capabilities;
- configuration and operational constraints;
- nearby tests, logs, experiment results, and known failures;
- historical decisions that still constrain the next iteration.

Prefer primary engineering evidence over summaries. Keep inspection read-only. Do not start a build, test run, prototype, remote action, or hardware operation merely to answer the interview.

Do not ask the user for a discoverable repository fact. State what was found and distinguish current evidence from stale documentation or inference.

## 3. Maintain the Working Model

Classify important statements internally:

| Class | Meaning | Treatment |
| --- | --- | --- |
| Fact | Directly observed or supported by current evidence | Use as the basis for requirements and planning; cite its source when useful. |
| Assumption | Believed for now but not verified | Carry visibly and identify what evidence would confirm or overturn it. |
| Preference | A chosen tradeoff or desired direction | Preserve it unless it conflicts with a harder constraint. |
| Unknown | Missing information that can change a decision | Explore, ask, or record it as an open question. |

Reclassify statements when evidence changes. Do not promote a preference, old plan, or document assertion to fact.

## 4. Check Readiness

Track five dimensions without turning them into ceremony or a user-facing scorecard:

1. **Problem** — Is the concrete engineering problem understood in its operating context?
2. **Goal** — Is the desired change specific enough to guide a near-term decision?
3. **Success Criteria** — Is there observable evidence that can accept or reject the next iteration?
4. **Scope** — Are the current iteration and its exclusions clear?
5. **Consistency** — Do the stated requirements, constraints, evidence, and proposed direction agree?

These dimensions need only be sufficiently clear for the next useful engineering iteration. Do not wait for the final system architecture or every future phase to be known.

## 5. Select the Next Question

Choose the unresolved uncertainty with the greatest ability to change the next iteration. By default, ask one focused question and wait for its answer.

For a consequential choice:

- state the options that are genuinely viable;
- recommend one and explain the engineering reason briefly;
- ask the user to confirm or change it.

Do not ask:

- questions already answered in the input;
- questions that read-only inspection can settle;
- distant design questions that do not affect the next iteration;
- large questionnaires or generic discovery checklists.

Challenge vague language with an observable distinction. Surface contradictions directly. If two or three attempts fail because the user cannot articulate the answer, offer a small concrete strawman for correction rather than repeating the same abstract question.

## 6. Handle Knowledge Gaps

When a missing answer materially affects the direction, record:

- **Question:** the precise unknown;
- **Decision impact:** which requirement, phase, or alternative depends on it;
- **Required depth:** the minimum understanding or evidence needed;
- **Closure type:** `research`, `prototype`, `decision`, or `task`;
- **Closure evidence:** what would make the question answerable.

Do not perform the closing work under this skill alone. A prototype or experiment is a proposed next iteration or a separate handoff, not part of the interview.

## 7. Pause, Resume, and Re-enter

Pause when:

- the user asks to stop;
- remaining uncertainty depends on research, a prototype, a decision input, or outside work;
- the next iteration is already clear enough to start safely.

On resume, read the current living documents or session state. Reopen only questions that remain consequential; do not re-interview settled areas without contradictory evidence.

When new evidence arrives:

1. identify which facts, assumptions, requirements, or phase choices it affects;
2. retain conclusions still supported;
3. replace conclusions that are no longer supported;
4. update the next iteration and its acceptance evidence;
5. record the evidence and resulting judgment in Engineering Notes.

The goal is an accurate current model, not a historical accumulation of obsolete plans.
