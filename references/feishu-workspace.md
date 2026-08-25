# Feishu-Native Workspace Adapter

Read this reference only when the user designates a Feishu/Lark Wiki or Docx location. Preserve the engineering model while using Feishu's hierarchy, document references, and whiteboards with restraint.

## Capability and Safety Boundary

- Prefer user identity for personal Wiki and Docx resources.
- Use `lark-wiki` for hierarchy, `lark-doc` v2 for bodies, and `lark-whiteboard` for querying or updating boards when available.
- Read the runtime's current Feishu skill instructions before calling the CLI.
- A named Feishu workspace authorizes only the scoped documentation work, not permissions, messages, tasks, code, tests, hardware, or external publication.
- A hierarchy change requires an approved tree and content mapping. Preserve old pages in an archive when restructuring unless the user explicitly requests deletion.
- Fetch the latest revision before editing and read back after every mutation. On EOF, timeout, or an ambiguous response, fetch the exact target before any retry.

If Feishu tools are unavailable, return the proposed tree, page drafts, and diagram source in conversation; state that nothing was published.

## Tool Route

| Intent | Route |
| --- | --- |
| resolve the supplied Wiki node | `wiki +node-get` |
| inspect relevant children or peers | `wiki +node-list` |
| create an approved stage page or archive | `wiki +node-create` |
| inspect outline, body, revision, and block IDs | `docs +fetch --api-version v2` |
| make a bounded body update | `docs +update --api-version v2` |
| move an existing Wiki page | `wiki +move` |
| inspect a board source or preview | `whiteboard +query` |

## Inspect Before Choosing the Shape

1. Resolve the exact node, object type, title, parent, and children.
2. Fetch the target outline before fetching the full body.
3. Inventory headings, links, citations, images, attachments, embedded resources, and whiteboards that must survive.
4. Inspect only directly relevant children or siblings when needed for naming, duplication, or evidence routing.
5. Distinguish a living root, a stage page, an immutable snapshot, and an archive.

Do not copy a nearby source page. Cite it and keep only the implication needed for the current stage.

## Default Multi-Stage Wiki Shape

For a multi-stage engineering route, use:

```text
<Project>｜<Topic>路线
├── 01｜阶段一：<自然、动词化的目标>
├── 02｜阶段二：<自然、动词化的目标>
├── 03｜阶段三：<自然、动词化的目标>
├── ...
└── 99｜旧结构归档
```

Use the workspace language consistently. Avoid bilingual titles. Use dates only for immutable snapshots or periodic reports.

Keep the root minimal:

- two short paragraphs at most;
- one Mermaid or whiteboard overview of stage order, stage outcome, and current position;
- `<sub-page-list>` or direct stage links;
- shared safety and authority boundaries stated once.

Do not add a status table, evidence index, multiple reading routes, or framework explanation by default.

## Stage Detail

For the current stage, use short localized sections for:

- what needs to be solved;
- the work in this stage;
- observable completion conditions;
- current notes that change the work;
- related internal or external material.

For the next stage, keep only the goal, entry condition, likely output, and completion boundary. For later stages, keep a short purpose plus entry and completion conditions. Do not make distant pages look implementation-ready.

When a stage accumulates substantial source material, link the existing documents first. Create a nested source page under that stage only when it has a real independent maintenance need; do not recreate a root-level evidence taxonomy.

## Feishu Writing Style

Use ordinary engineering prose. Feishu rich blocks are tools, not a quality score.

- default to paragraphs and short lists;
- use at most one opening callout on the current stage when it adds a real warning or decision;
- use a table only for genuinely repeated fields or comparisons;
- use checkboxes only for immediate checks, not as a second task tracker;
- use document cites and bookmarks near the statement they support;
- avoid emoji, decorative grids, repeated colored boxes, and English framework labels;
- do not require a non-text block in every section or target a rich-block percentage.

The page should feel like a maintained engineering note, not a generated report.

## Diagram Rule

For a multi-stage package, the root has one overview diagram by default. A simple vertical Mermaid flowchart is preferred because it remains readable in Feishu and on narrow screens. Each stage node should contain only:

- stage number and short name;
- the problem it resolves;
- the main output.

Mark the current stage visibly. Link navigation through the native child-page list rather than overloading diagram nodes.

Create a stage-local diagram only when it replaces substantial explanation of an actual architecture, state, sequence, comparison, or failure path. Do not create diagrams for evidence provenance, generic feedback loops, or document organization unless the user asks for them.

Always read back the diagram source and render a preview. If labels overlap or the result is too wide, simplify the labels or switch to a vertical layout.

## Targeted Maintenance

The default update unit is one stage page:

- ordinary progress updates the current stage only;
- new research updates the stage whose decision it affects;
- the root changes only when the current marker, order, dependency, or boundary changes;
- other stages remain untouched;
- when work advances, expand the new current stage rather than pre-filling all later stages.

## Restructuring an Existing Wiki

1. Fetch the latest root and child revisions and inventory resources.
2. Create the new stage pages in reading order.
3. Fill and read back each page independently.
4. Create the archive after the stage pages so it appears last.
5. Move the superseded pages into the archive without changing their bodies.
6. Rewrite the root only after all children and the archive verify.
7. Read back the final hierarchy, root body, document references, and diagram source/preview.

Do not delete the old structure merely to make the tree look clean. If a move or write result is ambiguous, stop and inspect the actual hierarchy before continuing.
