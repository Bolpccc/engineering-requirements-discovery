---
name: engineering-requirements-discovery
description: Clarify ambiguous or evolving engineering goals, maintain a lightweight local engineering bundle, and interpret detailed engineering plans as system behavior and observable outcomes for human decisions. Use for software, robotics, infrastructure, or other complex engineering work when requirements are unsettled, a staged plan must be maintained, or a technical owner needs to understand what an existing plan will actually change. Do not use to implement an already-settled specification, administer project trackers, publish externally, or perform a general code or architecture review.
---

# Engineering Requirements Discovery

Turn current evidence and a messy engineering goal into the smallest safe next iteration, keep its technical plan coherent, then explain what that plan means for the real system without destroying its cognitive map. Treat the engineering map, requirements, and plan as the current best model, not as frozen commitments.

## Boundaries

- Own `DISCUSS -> DOCUMENT -> PLAN`.
- Own read-only interpretation of an existing engineering plan when the user needs a Human Decision View rather than a redesign.
- Keep `BUILD` outside this skill. Do not implement code, run experiments, operate hardware, or begin deployment under this skill alone.
- Do not manage issues, owners, deadlines, branches, pull requests, or status synchronization.
- Persist discovery documents only in a user-designated local workspace. Without one, stay in conversation.
- External publication is a separate downstream workflow. Editing or approving the local bundle does not authorize publishing it. Hand off only after the user has reviewed the local result and explicitly confirmed it is ready for external publication.

## Load References as Needed

- Read [requirements-interview.md](references/requirements-interview.md) for discovery, bundle maintenance prompted by new evidence, or when plan interpretation exposes a goal mismatch. A pure interpretation request does not load the interview workflow.
- Read [research-for-decisions.md](references/research-for-decisions.md) when public technical knowledge, similar incidents, alternatives, or counterexamples could change the next iteration.
- Read [document-model.md](references/document-model.md) whenever persistent documents are requested or already exist. Use its naming and bundle rules for a local Markdown workspace.
- Read [plan-interpretation.md](references/plan-interpretation.md) when the user wants to understand, explain, judge, or align an existing engineering plan, and after this skill creates or materially updates a technical plan.

## Operating Modes

- **Discover and plan:** use the Route below when the problem, desired outcome, scope, tradeoffs, or acceptance evidence are still unsettled.
- **Maintain a bundle:** resume from `MAP.md` and the current stage when new evidence or a changed decision must update the technical model.
- **Interpret a plan:** when a detailed engineering plan already exists and the user's need is to understand its effects, preserve the plan's semantic anchors and produce a conversation-only Human Decision View. Do not restart requirements discovery unless the interpretation exposes a material mismatch between the plan and the user's actual problem.

After creating or materially updating a technical plan, automatically finish with the interpretation mode in the conversation. The technical bundle remains the implementation-grade source; the Human Decision View is a reading and decision layer, not another bundle artifact.

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

## Engineering Plan Interpretation

Do not summarize a detailed plan by inventing a new information architecture. Preserve the order and recognizable identity of its major problem blocks, proposal numbers, causal dependencies, status boundaries, safety constraints, architecture responsibility changes, acceptance evidence, rejection conditions, and later stages.

For each important semantic block, translate only as far as needed to make this chain clear:

```text
technical mechanism -> system behavior -> observable effect -> problem coverage -> acceptance result
```

Lead with what a person will observe, then retain the minimum technical term needed to return to the source, such as `State Lattice`, `costmap generation`, `MPPI`, or `Safety Gate`. Allocate explanation by decision value rather than source length. Compress ordinary functions, file lists, parameters, formulas, log fields, and corner cases unless they change behavior, ownership, safety, compatibility, or a consequential tradeoff.

Never turn an existing capability into a new change or a planned capability into a completed one. Use the source plan's claims first, then read only directly referenced and readily available evidence that can verify a consequential state. Clearly distinguish source-declared, independently verified, and unverified status. Do not expand interpretation into a full audit.

State what a proposal directly solves, may improve, and does not solve whenever those boundaries affect the decision. If the plan targets a different mechanism from the user's observed problem, explain the mismatch and return to discovery instead of silently redesigning the plan.

Keep the Human Decision View in the conversation by default. Do not add it to `MAP.md`, stage documents, templates, or bundle files. If the user asks to persist the interpretation, require a user-designated destination outside the technical bundle.

## Proportionate Verification

Choose the least expensive evidence that can falsify the current engineering hypothesis and protect the next change. Rigor means matching verification effort to causal uncertainty and consequence, not rebuilding a complete A/B baseline for every small change.

- When an interface contract, mechanism, and current source already establish a defect, recommend the direct correction in the build handoff. Ask for a targeted check, a representative known-good regression, and one relevant failure case; do not require a broad comparison merely to restate the known mechanism.
- When the cause is mostly clear but field conditions may affect it, specify the smallest observation that locates the environmental contribution, then one representative validation after correction.
- Escalate to frozen-input A/B, parameter matrices, or a full benchmark only when competing causal explanations remain, attribution matters, results are materially input-sensitive, or a safety-critical tradeoff such as thresholds, envelopes, obstacle retention, or destructive behavior must be measured.
- Treat ordinary variation in physical systems as expected. Reuse conclusions and baselines whose governing mechanism and invariants still hold; refresh only the state that can change the current decision. Do not make insignificant scene, timestamp, pose, or sensor drift trigger wholesale baseline reconstruction.
- Stop gathering evidence once it is sufficient to choose the next iteration, detect a meaningful regression, and state what result would overturn the decision. Additional comparison without decision impact is process overhead, not rigor.

This principle does not weaken safety boundaries. Use stronger controls where the cost of a false conclusion is high, but keep the evidence focused on the actual hazard or unresolved causal fork.

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

After discovery or bundle maintenance, finish with a compact statement of:

- the current problem and success condition;
- the next iteration and its acceptance evidence;
- assumptions being carried;
- open questions that could change the plan;
- where the map and current stage document were updated, or that they remain session-only.

When a technical plan was created or updated, follow that handoff with the conversation-only Human Decision View defined in [plan-interpretation.md](references/plan-interpretation.md). For a pure interpretation request, provide the Human Decision View directly without repeating the discovery handoff. Start with the overall system outcome and current status, preserve the source plan's major sequence, and end with the next observable test, rejection signals, and source anchors for deeper reading.

If the user wants the reviewed bundle published externally, state that the local bundle must first be explicitly confirmed as complete, then route publication separately. Do not publish or synchronize it under this skill.

If the user also requested implementation, make the transition explicit and route that work separately under the permissions and safety rules of the current environment.
