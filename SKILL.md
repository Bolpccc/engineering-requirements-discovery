---
name: engineering-requirements-discovery
description: Clarify ambiguous or evolving engineering goals against the real system, then maintain living requirements, a staged engineering plan, and decision-relevant notes. Use for software, robotics, infrastructure, or other complex engineering work when the problem, constraints, success criteria, or next iteration are not yet clear. Do not use to implement an already-settled specification, administer project trackers, or merely reformat existing documentation.
---

# Engineering Requirements Discovery

Turn current evidence and a messy engineering goal into the smallest safe next iteration. Treat requirements and plans as the current best model, not as frozen commitments.

## Boundaries

- Own `DISCUSS -> DOCUMENT -> PLAN`.
- Keep `BUILD` outside this skill. Do not implement code, run experiments, operate hardware, or begin deployment under this skill alone.
- Do not manage issues, owners, deadlines, branches, pull requests, or status synchronization.
- Treat GitHub, Gitee, Feishu, Notion, and local Markdown as replaceable storage. Do not encode a storage product into the engineering model.
- A request to discover requirements does not authorize persistent writes or external actions. Use the workspace the user explicitly names; without one, stay in conversation.

## Route

1. Read [requirements-interview.md](references/requirements-interview.md) and run the interview from what the user already supplied.
2. When an existing system is in scope, inspect the smallest relevant set of architecture, code, configuration, history, and available evidence before asking questions. Use read-only inspection; do not ask the user for facts that can be discovered safely.
3. Separate facts, assumptions, preferences, and unknowns. Advance one highest-impact uncertainty per turn by default and give a recommended answer when a real choice is required.
4. Stop interviewing when the next useful engineering iteration is clear enough to start safely, even if the eventual architecture remains uncertain. Preserve unresolved decision-relevant gaps as open questions.
5. When the user has named a persistent workspace, read [document-model.md](references/document-model.md), locate or create the semantic equivalents of Requirements, Engineering Plan, and Engineering Notes, and update them minimally. Otherwise maintain a session draft only.
6. When new implementation, simulation, test, or field evidence arrives, re-enter the loop. Reassess the requirements and plan directly; record the reasoning in Engineering Notes instead of creating a change-request system.

## Optional Composition

If a compatible requirements-interview or ideation skill is already installed and clearly applies, it may supply the conversational interview. Do not install it, require a particular upstream package, or delegate the engineering boundary to it. This skill still owns:

- evidence from the existing system;
- fact/assumption/preference/unknown separation;
- the three-document semantic model;
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
