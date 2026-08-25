---
name: engineering-requirements-discovery
description: Clarify ambiguous or evolving engineering goals against the real system and relevant external evidence, then maintain living requirements, a staged engineering plan, and decision-relevant notes. Use for software, robotics, infrastructure, or other complex engineering work when the problem, constraints, success criteria, evidence base, or next iteration are not yet clear. Do not use to implement an already-settled specification, administer project trackers, or merely reformat existing documentation.
---

# Engineering Requirements Discovery

Turn current evidence and a messy engineering goal into the smallest safe next iteration. Treat requirements and plans as the current best model, not as frozen commitments.

## Boundaries

- Own `DISCUSS -> DOCUMENT -> PLAN`.
- Keep `BUILD` outside this skill. Do not implement code, run experiments, operate hardware, or begin deployment under this skill alone.
- Do not manage issues, owners, deadlines, branches, pull requests, or status synchronization.
- Treat GitHub, Gitee, Feishu, Notion, and local Markdown as replaceable storage. Do not encode a storage product into the engineering model.
- A request to discover requirements does not authorize persistent writes or external actions. Use the workspace the user explicitly names; without one, stay in conversation.

## Load References as Needed

- Always read [requirements-interview.md](references/requirements-interview.md).
- Read [research-for-decisions.md](references/research-for-decisions.md) when public technical knowledge, similar incidents, alternatives, or counterexamples could change the next iteration.
- Read [document-model.md](references/document-model.md) when persistent documents are requested or already exist.
- Read [feishu-workspace.md](references/feishu-workspace.md) only when the user designates Feishu/Lark as the workspace.

## Route

1. Extract what the user already supplied. Do not restart a brain dump as a questionnaire.
2. When an existing system is in scope, inspect the smallest relevant set of architecture, code, configuration, history, internal knowledge, and available evidence before asking questions. Use read-only inspection; do not ask the user for facts that can be discovered safely.
3. Research decision-relevant public evidence when it can materially improve the choice. Seek authoritative mechanisms, real-world reports, alternatives, and counterexamples; do not collect links without decision impact.
4. Separate facts, assumptions, preferences, unknowns, and conflicting evidence. Advance one highest-impact uncertainty per turn by default and give a recommended answer when a real choice is required.
5. Stop interviewing when the next useful engineering iteration is clear enough to start safely, even if the eventual architecture remains uncertain. Preserve unresolved decision-relevant gaps as open questions.
6. When the user has named a persistent workspace, maintain Requirements, Engineering Plan, and Engineering Notes as internal semantic lanes. Keep a small single-stage effort on one page. For a multi-stage effort, present the lanes through a concise overview and one page per engineering stage by default; do not expose the internal classification as the page tree unless it genuinely helps the reader.
7. Match document detail to engineering proximity. Make the current stage concrete, the next stage directional, and later stages skeletal. Write for the engineer's attention, not for apparent completeness.
8. Use a natural engineering-work-document voice. Prefer direct sentences and concrete nouns; do not turn internal labels such as fact, assumption, preference, unknown, decision impact, or evidence type into repetitive visible headings.
9. Use one overview diagram for the multi-stage route by default. Add a stage-local diagram only when it materially reduces explanation; do not create a diagram quota or a rich-block quota.
10. When new implementation, simulation, test, field, or research evidence arrives, re-enter the loop. Update only the affected stage by default. Change the overview only when the current stage, stage order, or stage boundary changes; record the reasoning without creating a change-request system.

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
- where the living documents were updated, or that they remain session-only.

If the user also requested implementation, make the transition explicit and route that work separately under the permissions and safety rules of the current environment.
