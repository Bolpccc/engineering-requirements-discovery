# Lightweight Engineering Bundle

Use this model when the user designates a persistent workspace. The bundle is a human-readable engineering conversation surface: one global map and one continuous document per outcome-based stage. Requirements, plans, and decision notes remain semantic responsibilities inside that writing, not a page taxonomy.

## Persistence Boundary

- Without a designated workspace, keep a session-only draft and state that nothing was persisted.
- In a designated workspace, locate an existing equivalent before creating anything. Preserve useful content, links, evidence, and the host medium's native structure.
- Use a single page for a small effort with one near-term iteration, one audience, and a small evidence base.
- Default to a bundle when the work spans multiple engineering outcomes or the current stage needs sustained requirements, architecture, implementation, and verification discussion.
- Do not duplicate a source of truth merely to make the bundle look self-contained.

## Local Markdown Shape

Use one flat directory:

```text
<project-key>-<topic-key>-engineering-bundle/
├── MAP.md
├── 01-<outcome-key>.md
├── 02-<outcome-key>.md
├── 03-<outcome-key>.md
└── assets/                    # only when real non-embedded artifacts exist
```

Do not create `stages/`, stage directories, stage `README.md` files, or files named after internal categories such as `requirements.md`, `architecture.md`, `implementation-plan.md`, `verification.md`, or `decisions.md`. Those separations force a reviewer to reconstruct one design argument across several files.

Create `assets/` only for an image, raw attachment, or other real artifact that cannot reasonably be embedded or linked at its existing source. Name a local artifact `<stage-id>-<purpose-key>.<ext>`. Do not create an empty assets directory.

## Stable Naming Contract

Bundle and stage names are derived, not improvised:

- Bundle directory: `<project-key>-<topic-key>-engineering-bundle`.
- Stage document: `NN-<outcome-key>.md`, with a two-digit stage number.
- Appendix, only after explicit user approval: `appendix-<purpose-key>.md`.

Use lowercase English ASCII kebab-case for filesystem keys and the project's main language for reader-facing Markdown titles.

Derive keys in this order:

1. `project-key` comes from the repository, product, or project's existing canonical identifier. Do not create a shorter alias for convenience.
2. `topic-key` comes from the aligned engineering problem. Do not name the bundle after a proposed solution unless that solution has become the agreed scope.
3. `outcome-key` names the observable engineering result of the stage, preferably with a concrete verb and object, such as `understand-current-system` or `define-target-architecture`.

Reject weak keys such as `phase-1`, `misc`, `optimization`, `new-design`, or another label that does not say what becomes true. Do not add dates, status, authors, or content versions to filenames.

Reuse an existing confirmed key for the same project, topic, or stage. When no stable English key exists, propose one recommended key, state which agreed phrase it represents, and wait for confirmation before creating the bundle or new stage. Once confirmed, keep the key stable across later wording changes. Rename it only when the engineering scope or outcome materially changes, then update every affected link in the same bounded edit.

## MAP.md

Use [MAP.template.md](../assets/engineering-bundle/MAP.template.md) as a responsibility guide. The map should be understandable in under a minute and contain only:

- why the bundle exists and what overall success means;
- the current stage, why it is current, and what it unlocks;
- numbered stage outcomes, entry conditions, completion evidence, dependencies, and links;
- shared constraints and confirmed decisions that affect more than one stage;
- one route diagram when the multi-stage relationship warrants it.

The map is not a dashboard or executive summary. Do not add owners, deadlines, issue state, evidence taxonomies, change logs, or repeated stage summaries. Keep one current stage unless the work is explicitly paused or all stages are complete.

The route diagram and the linked stage list express the same model. Update both when the current stage, stage order, dependency, or boundary changes. Do not redraw the diagram for prose-only edits.

## Stage Document

Use [STAGE.template.md](../assets/engineering-bundle/STAGE.template.md) as a responsibility guide, not a form to fill. A stage document should let a person follow one continuous engineering argument from the problem to the proposed implementation and its verification.

For the current stage, preserve the content needed to understand:

- the actual problem, impact, and intended outcome;
- confirmed facts, requirements, constraints, and necessary assumptions;
- how the design developed and which tradeoffs changed it;
- the current architecture or implementation direction and affected scope;
- evidence that accepts the stage and an observed result that would reject the direction;
- unresolved questions that still require human judgment;
- source, evidence, and research links that affect the current decision.

These are content responsibilities, not mandatory headings. Combine them into natural project-language prose, rename or merge headings, and omit empty sections. Do not label every paragraph as fact, assumption, preference, unknown, requirement, or decision.

Keep the next stage directional: goal, entry condition, likely result, and completion boundary. Keep later stages skeletal: purpose, dependency, and completion boundary only. Expand them when evidence brings them closer.

Do not split a stage merely because it becomes long. First remove obsolete process notes, duplicated evidence, and material that belongs at its original source. Only when the document can no longer be reviewed effectively in one pass may the agent recommend one purpose-specific appendix. Create it only after the user explicitly agrees; never introduce a nested stage tree.

## Resume and Joint Editing

On every return to an existing bundle:

1. Read `MAP.md` first.
2. Resolve its current-stage link and read that stage document.
3. Load only linked material that can change the current decision.
4. Inspect relevant current-system evidence before treating a factual edit as verified.
5. Continue from the current gap rather than restarting discovery.

Direct human edits are part of the shared current model. Preserve changed decisions, priorities, and preferences. Check factual, evidentiary, and technical claims against available evidence. If a manual edit conflicts with another constraint, stage boundary, or acceptance condition, state the conflict and resolve the highest-impact decision instead of silently choosing one version or restoring old prose.

## Narrow Update Rule

- Ordinary implementation, simulation, test, field, or research evidence updates only the affected stage.
- Update the map only when the current marker, stage order, dependency, shared constraint, key decision, or document link changes.
- Leave unrelated stages untouched.
- When work advances, expand the newly current stage and compress the completed stage to its durable conclusion, decisive tradeoffs, and valid evidence.
- Remove obsolete current statements rather than leaving contradictory versions or adding a chronological change ledger.
- Use Git or the host workspace's revision history for change history. Do not create a parallel change-request or task system.

## Build Handoff Readiness

The current stage is ready to hand to a separate BUILD workflow only when one document can explain:

- the implementation outcome and affected scope;
- the selected design and consequential tradeoffs;
- constraints and assumptions the implementer must preserve;
- evidence that will accept the implementation;
- a result that would reject the current direction;
- open questions that still block or could materially change implementation.

If a consequential item is missing, continue discovery or frame the precise research, prototype, decision, or outside task that will close it. This skill does not perform the build.

## Other Workspace Adapters

Preserve the same reader model in Feishu, Notion, or another document system: one lightweight map and one flat page per outcome-based stage. Use native links and editable diagrams, but do not recreate the removed document-type hierarchy. Follow the adapter's mutation and readback rules.
