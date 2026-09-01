---
name: engineering-requirements-discovery
description: Clarify ambiguous or evolving engineering goals against the real system and relevant external evidence, then maintain a lightweight local engineering map and outcome-based stage documents for the next safe iteration. Use for software, robotics, infrastructure, or other complex engineering work when the problem, constraints, success criteria, evidence base, or next iteration are not yet clear. Do not use to implement an already-settled specification, administer project trackers, publish externally, or merely reformat existing documentation.
---

# Engineering Requirements Discovery

Turn current evidence and a messy engineering goal into the smallest safe next iteration. Treat the engineering map, requirements, and plan as the current best model, not as frozen commitments.

## Boundaries

- Own `DISCUSS -> DOCUMENT -> PLAN`.
- Keep `BUILD` outside this skill. Do not implement code, run experiments, operate hardware, or begin deployment under this skill alone.
- Do not manage issues, owners, deadlines, branches, pull requests, or status synchronization.
- Persist discovery documents only in a user-designated local workspace. Without one, stay in conversation.
- External publication is a separate downstream workflow. Editing or approving the local bundle does not authorize publishing it. Hand off only after the user has reviewed the local result and explicitly confirmed it is ready for external publication.

## Load References as Needed

- Always read [requirements-interview.md](references/requirements-interview.md).
- Read [research-for-decisions.md](references/research-for-decisions.md) when public technical knowledge, similar incidents, alternatives, or counterexamples could change the next iteration.
- Read [document-model.md](references/document-model.md) whenever persistent documents are requested or already exist. Use its naming and bundle rules for a local Markdown workspace.

## Route

1. Extract what the user already supplied. Do not restart a brain dump as a questionnaire.
2. When an existing system is in scope, inspect the smallest relevant set of architecture, code, configuration, history, internal knowledge, and available evidence before asking questions. Use read-only inspection; do not ask the user for facts that can be discovered safely.
3. Before the first question, use three to five short sentences to state the current interpretation, the materially different readings that would otherwise be assumed silently, and what a useful handoff appears to be. Do not expose framework labels. Distinguish the solution the user named from the outcome they actually need.
4. Take a position. Generate candidate gaps from the user's words and current evidence, then advance one question with the greatest ability to change the direction. Anchor it in context, name the tension or hypothesis, and ask only one logical question.
5. Challenge contradictions, vague demand, weak premises, and solution fixation directly. Use open questions for concrete incidents, motivation, and dissatisfaction; use options with a recommendation for engineering tradeoffs and boundary decisions.
6. Research decision-relevant public evidence when it can materially improve the choice. Seek authoritative mechanisms, real-world reports, alternatives, and counterexamples; do not collect links without decision impact.
7. Track Problem, Goal, Success Criteria, Scope, and Consistency internally as evidence-backed readiness dimensions. Do not show a scoreboard. Keep interviewing without a fixed question limit until the core need, consequential tradeoffs, and next verification are clear; distant architecture may remain unknown.
8. When a real engineering fork remains, compare two or three viable approaches, lead with a recommendation, and include the minimum-change or status-quo option when it is credible. Do not manufacture alternatives for a factual investigation or a settled small request.
9. Before documenting, pressure-test the current model for a false problem, scope creep, hidden dependencies, and unfalsifiable success. If the review exposes a consequential gap, ask one more question; otherwise proceed.
10. When the user has named a local persistent workspace, locate an existing equivalent before creating documents. Keep a small single-stage effort on one page. For a complex multi-stage effort, maintain a lightweight Engineering Bundle: one map and one flat document per outcome-based stage. Requirements, Engineering Plan, and Engineering Notes remain internal semantic lanes, not files or page categories.
11. On resume, read the map first, then the current stage document and only the linked material that affects the current decision. Treat direct human edits as part of the shared current model: preserve decisions and preferences, verify factual or technical claims, and surface consequential contradictions instead of silently overwriting them.
12. Match document detail to engineering proximity. Make the current stage concrete enough for continuous human review, the next stage directional, and later stages skeletal. Keep the problem, constraints, design reasoning, implementation direction, and acceptance evidence together in the stage narrative rather than fragmenting them by document type.
13. Use a natural engineering-work-document voice. Prefer direct sentences and concrete nouns; do not turn internal labels such as fact, assumption, preference, unknown, decision impact, or evidence type into repetitive visible headings.
14. Use one overview diagram in the map for a multi-stage route by default. Embed diagrams in the relevant local Markdown when practical. Add a stage-local diagram only when it materially reduces explanation; do not create a diagram quota. Whenever a diagram is selected, follow Diagram Composition below.
15. When new implementation, simulation, test, field, or research evidence arrives, re-enter the loop. Update only the affected stage by default. Change the map only when the current stage, stage order, dependency, shared boundary, or key decision changes; record the reasoning without creating a change-request system.

## Lightweight Engineering Bundle

For a local Markdown workspace, use the portable flat bundle defined in [document-model.md](references/document-model.md):

```text
<project-key>-<topic-key>-engineering-bundle/
├── MAP.md
├── 01-<outcome-key>.md
├── 02-<outcome-key>.md
└── ...
```

- Derive `project-key` from an existing canonical project identifier. Derive `topic-key` from the aligned engineering problem, not an unconfirmed solution. Name stages for observable engineering outcomes, not generic phases.
- Use lowercase ASCII kebab-case for filesystem keys and the project's main language for reader-facing titles. If no stable English key exists, propose one recommended key with its basis and wait for confirmation before creating the bundle or stage. Once confirmed, keep keys stable unless the engineering scope or stage outcome materially changes.
- Do not create stage directories, stage `README.md` files, document-type files, empty attachments, or detailed future-stage content. Create `assets/` only for real artifacts that cannot reasonably be embedded or linked in place.
- Do not split a stage document merely because it is long. Only create an `appendix-<purpose-key>.md` after the user explicitly agrees that the stage can no longer be reviewed effectively as one document.
- Use the bundled [map template](assets/engineering-bundle/MAP.template.md) and [stage template](assets/engineering-bundle/STAGE.template.md) as responsibility guides. Adapt their prose and omit empty sections; do not fill them mechanically.

## Diagram Composition

- Decide whether a diagram is warranted from the engineering content before invoking a drawing workflow. A multi-stage map warrants one route overview by default. A single-stage page or stage-local explanation warrants one only when it materially clarifies an architecture, state, sequence, comparison, dependency, or failure path.
- Whenever a diagram is warranted, invoke `$mermaid-skill` automatically. This skill owns the engineering meaning, scope, labels, and document placement; `$mermaid-skill` owns diagram-type selection, Mermaid source, syntax validation, rendered preview, and readability review.
- The discovery permission boundary still applies. Without a user-designated local workspace, use `$mermaid-skill` only to produce session-local Mermaid source and, when available, temporary local validation or preview artifacts. Do not persist diagram files or send the source to Kroki or another external renderer.
- In a designated local workspace, persist or embed only the artifacts authorized for that local bundle. Do not publish diagram source or exports externally under this skill.
- If `$mermaid-skill` is unavailable, do not install it or claim that validation or rendering occurred. Preserve the diagram intent and draft source in the session, state the missing capability, and continue the engineering handoff without fabricating visual evidence.

## Optional Composition

If a compatible requirements-interview or ideation skill is already installed and clearly applies, it may supply the conversational interview. Do not install it, require a particular upstream package, or delegate the engineering boundary to it. This skill still owns:

- evidence from the existing system;
- fact/assumption/preference/unknown separation;
- the three-lane semantic model and its attention-oriented presentation in the chosen workspace;
- decision-driven research and evidence qualification;
- a restrained visual model centered on the engineering route;
- staged planning and the next-iteration readiness test;
- the boundary between discovery and build.

If compatibility is uncertain, use the bundled interview reference.

## Handoff

Finish with a compact statement of:

- the current problem and success condition;
- the next iteration and its acceptance evidence;
- assumptions being carried;
- open questions that could change the plan;
- where the map and current stage document were updated, or that they remain session-only.

If the user wants the reviewed bundle published externally, state that the local bundle must first be explicitly confirmed as complete, then route publication separately. Do not publish or synchronize it under this skill.

If the user also requested implementation, make the transition explicit and route that work separately under the permissions and safety rules of the current environment.
