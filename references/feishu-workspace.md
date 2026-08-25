# Feishu-Native Workspace Adapter

Read this reference only when the user designates a Feishu/Lark Wiki or Docx location. Preserve the core semantic lanes while using Feishu's hierarchy, rich blocks, citations, and whiteboards as native capabilities.

## Capability and Safety Boundary

- Prefer user identity for personal Wiki and Docx resources.
- Use `lark-wiki` for space and node hierarchy, `lark-doc` v2 for document bodies, and `lark-whiteboard` for querying or updating existing/complex boards when those capabilities are available.
- Read the runtime's current Feishu skill instructions before calling the CLI. Do not assume old command syntax.
- A named Feishu workspace authorizes scoped document work, not unrelated Wiki traversal, permissions, messages, tasks, or external publication.
- Creating several pages, moving existing content, or restructuring an existing Wiki tree materially changes navigation. Present the proposed tree and content mapping before that mutation unless the user already approved the exact structure.
- Never overwrite an existing page merely to improve layout. Preserve citations, images, whiteboards, attachments, embedded resources, and block identities through revision-guarded block edits.

If Feishu tools are unavailable, produce a proposed page tree, document drafts, and Mermaid sources in conversation; state that nothing was published.

### Tool Route

Use the runtime's current shortcuts rather than inventing endpoints:

| Intent | Route |
| --- | --- |
| resolve the supplied Wiki URL or identify the exact node | `wiki +node-get` |
| inspect authorized children or directly relevant peers | `wiki +node-list` |
| create approved hub or child pages | `wiki +node-create` |
| inspect outline, section, full body, revision, and block IDs | `docs +fetch --api-version v2` |
| insert, replace, move, or copy bounded blocks | `docs +update --api-version v2` |
| preview or download document media and board thumbnails | `docs +media-preview` / `docs +media-download` |
| inspect or revise an existing board | `whiteboard +query` / `whiteboard +update` |

## 1. Inspect the Authorized Workspace

Resolve the supplied Wiki node or Docx and inspect only the relevant scope:

1. identify the exact node, object type, title, parent, and existing children;
2. fetch the target outline before fetching full or section content;
3. inventory headings, tables, callouts, citations, bookmarks, images, attachments, embedded resources, and whiteboards;
4. inspect directly related child or sibling titles/outlines only when authorized and useful for naming, duplication, or evidence routing;
5. distinguish a hub page, a living technical page, a dated snapshot, and a source archive.

Do not duplicate a nearby source page. Link it with a document cite or bookmark and summarize only the decision-relevant implication.

## 2. Choose One Page or a Page Set

For a small discovery, keep a single Docx with clear sections. For a complex engineering topic, prefer a hub with role-focused child pages:

```text
<Project>｜<Topic>工程发现
├── 00｜需求基线：问题、目标、边界与成功条件
├── 01｜系统现状：架构、源码与运行证据
├── 02｜演进路线：阶段、门槛与下一步
├── 03｜技术研判：方案、假设与开放问题
└── 04｜证据索引：内部材料、外部研究与实验
```

Adapt the nouns to the topic but keep the grammar consistent: `NN｜semantic role：specific scope`. Use one language across the page set. Do not date living pages; use a date for snapshots only. Omit empty roles and avoid splitting pages whose content always changes together.

The package root is the hub and should contain:

- an opening callout with the current conclusion and current focus;
- a reading route and a native child-page list;
- a compact status grid or table;
- one overview diagram;
- links to the most consequential open questions and evidence.

It should not repeat every requirement, phase, or technical note.

## 3. Compose Native Feishu Documents

Use Feishu XML rich blocks rather than pasting a long Markdown-like stream:

- `<callout>` for the front-loaded conclusion, recommendation, risk, or pending confirmation;
- `<grid>` for compact alternatives and before/after comparisons;
- `<table>` for parameter registries, evidence ledgers, acceptance matrices, and structured mappings;
- `<checkbox>` only for immediate checks, not as a second project tracker;
- `<cite type="doc">` for related internal documents and `<bookmark>` or linked citations for external sources;
- `<sub-page-list>` on Wiki hub pages;
- `<whiteboard>` for important relationships.

Maintain visual rhythm: no long run of undifferentiated paragraphs, consistent heading depth, semantic color use, and a non-text block in each major section when it improves comprehension.

## 4. Visual Coverage Audit

Review each major claim for a better visual form:

| Content | Preferred visual |
| --- | --- |
| components, owners, dependencies, topics, or data paths | architecture or dependency diagram |
| request-to-result behavior or cross-component interaction | sequence or flow diagram |
| lifecycle, safety gate, retry, or failure transitions | state diagram |
| phases, dependencies, gates, and feedback | roadmap, timeline, or Gantt |
| alternatives and tradeoffs | comparison diagram or decision tree |
| causes, risks, or failure propagation | fishbone or causal chain |
| evidence sources and confidence | evidence map |
| branching concepts or reading routes | mind map |

Use Mermaid for focused flowcharts, sequence diagrams, state diagrams, class diagrams, mind maps, Gantt charts, and pies when the Feishu renderer supports the syntax. Use SVG/whiteboard workflows for dense architecture, swimlanes, comparisons, fishbones, evidence maps, and other layouts needing stronger visual design.

Prefer several focused boards over one giant board. Every diagram must:

- communicate a relationship that prose or a table hides;
- distinguish observed/current, proposed/future, and assumed elements;
- use the document's language and terminology;
- be traceable to the source sections or evidence it summarizes;
- remain readable in a rendered preview.

For a complex multi-page engineering discovery package, the default visual set is:

1. a hub overview connecting problem, current evidence, current focus, and the feedback loop;
2. a current-system architecture or end-to-end data/decision flow;
3. a phased roadmap with acceptance gates and evidence feedback;
4. additional focused state, sequence, comparison, risk, or evidence diagrams wherever they carry a core conclusion.

Omit a default diagram only when the relationship does not exist; do not replace it with decorative imagery.

For an existing Mermaid board, read its source before updating, overwrite only when replacing the whole board, and verify the resulting source or preview. Feishu Mermaid variants can have layout limitations; render a minimal sample first for unusual syntax and fall back to a simpler diagram or SVG when labels overlap.

## 5. Internal and External Evidence

Use Feishu as an evidence network, not a text dump:

- cite relevant internal Wiki/Docx sources instead of copying them;
- keep source title, version/date, evidence type, applicability, and supported claim together;
- represent external sources with direct bookmarks or citations near the supported claim;
- place substantial source portfolios in the Evidence Index and keep only conclusions in Requirements and Plan;
- separate observed system evidence, public-source evidence, inference, and pending validation.

Public posts and similar incidents broaden the discussion but do not prove behavior in the current system.

## 6. Write and Verify Incrementally

For a new page set:

1. create the approved Wiki hierarchy;
2. create each page as a skeleton with title, opening callout, headings, and intended visual anchors;
3. fill non-overlapping sections in bounded updates;
4. add citations and focused diagrams;
5. fetch after each mutation and verify before continuing.

For an existing page:

1. fetch the latest revision and block IDs;
2. use precise insert, replace, move, or copy operations;
3. preserve all resource tokens and citations;
4. refetch because replacement may change block IDs;
5. do not reuse stale revision or block identifiers.

Final readback must verify:

- titles, numbering, parent-child relationships, and reading order;
- revision advancement and intended block placement;
- required content appears once and preserved content remains;
- citations and bookmarks resolve to the intended sources;
- every diagram exists, contains content, and has a readable source or preview;
- the hub links to the current focus, semantic lanes, and evidence.

If a write returns EOF, timeout, or an ambiguous response, stop and fetch the exact target before any retry. Do not resend blindly or claim completion from the request alone.
