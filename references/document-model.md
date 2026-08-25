# Living Document Model

Requirements, Engineering Plan, and Engineering Notes are stable semantic lanes for reasoning. They are not a required file or page structure. Present the work in the shape that gives an engineer the clearest next move with the least attention cost.

## Persistence Boundary

A workspace is a user-designated persistent location such as a repository directory, document set, or knowledge base.

- Without a designated workspace, keep a session-only draft and state that nothing was persisted.
- In a designated workspace, locate existing equivalents before creating anything.
- Preserve useful content, links, evidence, and the host medium's native structure.
- Make the narrowest update that reflects the current understanding.
- Do not duplicate a source of truth to satisfy a template.

## Choose the Reader's Axis

Use a single page when there is one near-term iteration, one audience, and a small evidence base.

For a real multi-stage effort, default to a progression-centered package:

```text
<Project>｜<Topic> Route
├── 01｜Stage 1: <plain-language outcome>
├── 02｜Stage 2: <plain-language outcome>
├── 03｜Stage 3: <plain-language outcome>
└── ...
```

The root establishes the whole route. Each child owns one engineering stage. This lets the current stage evolve without forcing readers or agents to revisit every future stage.

Use responsibility- or domain-centered pages instead only when stages are not the reader's main navigation model, for example when independent subsystems have different owners and update cadences. Do not default to pages named Requirements, System State, Reasoning, or Evidence Index merely because those concepts exist internally.

## Root Page

Keep the root deliberately thin:

- one or two short paragraphs explaining why the route exists and where work currently is;
- one overview diagram showing the stages, their main outcomes, dependencies, and current position;
- the native child-page list or direct links;
- shared safety or authority boundaries stated once.

Do not add a status dashboard, evidence taxonomy, decision framework, or repeated summaries unless the user needs them. The root should be understandable in under a minute.

## Stage Page

Use natural localized headings. A practical default is:

```markdown
# What this stage needs to solve

# Work in this stage

# What completion looks like

# Current notes

# Related material
```

These are optional responsibilities, not mandatory labels. Omit empty sections. Prefer a few concrete sentences and bullets over a dense matrix.

Requirements appear as the outcome and constraints of the affected stage. The plan appears as its work and completion evidence. Engineering Notes appear only where the reason changes a decision. Keep fact, assumption, preference, and unknown classification internally; surface it explicitly only when the distinction prevents a mistake.

## Detail Gradient

Information density must decrease with engineering distance:

- **Current stage:** concrete problem, five to seven meaningful work items when needed, four to five observable completion conditions, current constraints, and relevant sources.
- **Next stage:** goal, entry condition, likely outputs, and completion condition. Do not pre-write a detailed implementation backlog.
- **Later stages:** purpose, dependency or entry condition, and completion boundary only. Expand them when evidence brings them closer.

The numbers are ceilings and guides, not a requirement to fill space. A shorter page is better when it is sufficient.

## Writing Voice

Write as an engineer maintaining a working document:

- use one language and familiar project terms;
- prefer direct statements such as `先把实际参数覆盖关系查清楚`;
- prefer verbs and concrete objects in titles;
- avoid bilingual synonym titles, slogans, ceremonial summaries, and repeated method explanations;
- do not use internal framework labels such as `Current Conclusion`, `Evidence Objective`, `Decision Impact`, or `Fact / Assumption / Preference / Unknown` as routine visible headings;
- avoid emoji by default;
- use a callout, table, or diagram only when it makes the content easier to scan.

Do not optimize for the amount of visible structure. Optimize for how quickly a reader knows what matters now.

## Visual Model

For a multi-stage package, create one overview diagram on the root by default. It should show:

- stage order and dependencies;
- the problem each stage resolves;
- its main output;
- the current stage.

Do not add stage-local diagrams merely for visual variety. Add one only when a real architecture, state, sequence, comparison, or failure relationship would otherwise require substantial prose. There is no diagram quota and no rich-block density target.

## Research and Evidence

Keep detailed source qualification in the reasoning process. In the living package:

- place a concise takeaway in the stage it affects;
- state the applicability limit when it matters;
- link the internal document or external source nearby;
- avoid a separate evidence page unless the source collection has an independent audience or maintenance need.

Public reports broaden the decision space but do not prove current-system behavior.

## Updating After Evidence

When new evidence arrives:

1. verify what it actually demonstrates and under which conditions;
2. update the affected stage's needed outcome, work, or completion condition;
3. update the root only if the current stage, ordering, dependency, or boundary changed;
4. remove obsolete current statements rather than leaving contradictory versions;
5. leave unrelated stages untouched.

When the current stage changes, expand the newly current page and reduce obsolete operational detail in the completed stage to a compact record. Do not rewrite all stages for a local change.

Do not create change-request identifiers or a parallel project tracker. Respect an external traceability policy when one already exists, but keep it outside this skill's core model.
