# Engineering Requirements Discovery

An Agent Skill for turning ambiguous, evolving engineering goals into living requirements and a staged, evidence-driven plan.

It is designed for software, robotics, infrastructure, and other complex engineering work where the real requirement emerges through inspection, implementation, simulation, testing, or field evidence.

## What it does

```text
DISCUSS -> DOCUMENT -> PLAN
   ^                     |
   |--- new evidence ----|

BUILD happens outside this skill.
```

The skill:

- reads the existing engineering context before asking discoverable questions;
- extracts answers from brain dumps instead of restarting with a questionnaire;
- separates facts, assumptions, preferences, and unknowns;
- researches official mechanisms, similar incidents, alternatives, and counterexamples when they can change the decision;
- advances one high-impact uncertainty at a time;
- defines the smallest safe next engineering iteration;
- maintains Requirements, Engineering Plan, and Engineering Notes as internal semantic lanes without forcing them into the page tree;
- organizes a multi-stage effort as one concise route overview plus one maintainable page per engineering stage;
- keeps a small single-stage effort on one page instead of forcing a hierarchy;
- makes the current stage concrete, the next stage directional, and later stages deliberately brief;
- uses one route diagram by default and adds a stage-local diagram only when it reduces real explanation;
- revises the current model directly when new evidence changes the plan.

It does not implement code, run experiments, operate hardware, manage project trackers, or synchronize GitHub, Gitee, Feishu, Notion, or other storage systems.

## Install

For Codex:

```bash
git clone https://github.com/Bolpccc/engineering-requirements-discovery.git \
  ~/.codex/skills/engineering-requirements-discovery
```

For another Agent Skills compatible runtime, clone or copy this repository into that runtime's skills directory.

## Use

Explicit invocation:

```text
Use $engineering-requirements-discovery to clarify this engineering goal and define the next evidence-driven iteration.
```

You can provide a short goal, a long brain dump, existing documents, or new test evidence. If you want persistent documents, name the workspace explicitly:

```text
Use $engineering-requirements-discovery. Maintain the living documents in this repository under docs/discovery/.
```

Without a designated workspace, the skill stays in conversation and does not write files.

## Repository structure

```text
SKILL.md
agents/openai.yaml
references/requirements-interview.md
references/document-model.md
references/research-for-decisions.md
references/feishu-workspace.md
```

The skill is self-contained. If a compatible interview or ideation skill is already installed, it may provide the conversational interview, but no upstream skill is required.

## Feishu/Lark-native output

When Feishu is the designated workspace, a multi-stage effort defaults to a short route page and one child page per engineering stage. The route page contains the current position, one stage diagram, the native child-page list, and shared boundaries. The current stage carries the detail; future stages remain brief until evidence brings them closer. Feishu remains an optional presentation adapter; the core engineering model stays portable.

Example:

```text
B1｜Navigation Whiteboxing Route
├── 01｜Stage 1: Understand the Current System
├── 02｜Stage 2: Consolidate Parameters and Outputs
├── 03｜Stage 3: Validate Costmap Noise
└── ...
```

Progress normally updates one stage page. The overview changes only when the current stage, ordering, dependency, or boundary changes.

## Decision-driven research

For an open question that can change the next iteration, the skill searches along several angles: authoritative behavior, real-world failure reports, alternatives, counterexamples, and environment fit. It records what each source actually supports and keeps community experience separate from verified current-system facts.

## Acknowledgements

The interview design was informed by the one-question-at-a-time, context-first approaches in:

- [obra/superpowers — brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md)
- [nicknisi/ideation — interview engine](https://github.com/nicknisi/ideation/blob/main/references/interview-engine.md)

This repository implements a smaller, independent engineering-discovery workflow and does not copy or depend on either complete system.

## License

MIT License. See [LICENSE](LICENSE).

---

# 工程化需求挖掘

这是一个面向软件、机器人、基础设施等复杂工程项目的 Agent Skill，用来把模糊且持续变化的工程目标转化为活的需求、分阶段计划和决策依据。

## 它负责什么

它只负责：

```text
讨论需求 -> 更新当前认知 -> 形成下一阶段计划
```

开发、实验、真机操作和部署不属于本 Skill。

核心行为包括：

- 先理解已有代码、架构、约束和证据，再询问无法从环境获得的信息；
- 从长段想法中提取已经回答的内容，不重新发一份需求问卷；
- 区分事实、假设、偏好和未知；
- 针对真正影响决策的缺口，主动搜索官方机制、类似故障、社区实践、替代方案和反例；
- 默认每轮只推进一个最关键的不确定性；
- 以“下一轮工程验证是否已经足够清晰”为完成条件；
- 将 Requirements、Engineering Plan、Engineering Notes 作为内部语义车道，不强制映射成页面目录；
- 多阶段工程默认采用“一张路线总览 + 每阶段一个子页”；
- 当前阶段写具体，下一阶段保留轮廓，远期阶段只写目的和进入条件；
- 根页面默认只放一张工程演进图，阶段页只有在确实能减少解释时才增加图；
- 新证据推翻旧判断时，直接修改当前需求和计划。

它不负责写代码、运行实验、操作机器人、管理 Issue/负责人/截止时间，也不把 GitHub、Gitee、飞书、Notion 或本地 Markdown 固定为核心存储。

## 使用方式

```text
使用 $engineering-requirements-discovery，帮我把这次导航框架重构的目标问清楚，并形成下一轮可验证的工程阶段。
```

如果需要持久化，请明确指定位置：

```text
使用 $engineering-requirements-discovery，并把活文档维护在当前仓库的 docs/discovery/。
```

没有指定 Workspace 时，Skill 只在对话中维护草稿，不会自行落盘。

## 设计边界

三条语义车道稳定，但它们主要服务 AI 的判断，不要求读者先理解一套文档分类。近期阶段写具体，远期阶段保持粗略；需求和计划表达当前最佳认知，而不是不可修改的合同。

## 飞书原生输出

指定飞书时，Skill 会先盘点目标 Wiki 层级和相关页面。单阶段工作保持单页；多阶段工作默认采用“路线总览 + 每阶段一个子页”：

```text
B1｜导航白盒化路线
├── 01｜阶段一：看清当前系统
├── 02｜阶段二：收拢参数与输出
├── 03｜阶段三：验证 Costmap 离散噪声
└── ...
```

根页面只保留简短背景、当前位置、一张工程演进图、子页面列表和共同边界。普通进展只更新当前阶段；新证据只更新受影响的阶段。Callout、表格、分栏和额外画板不再作为丰富度指标，只在真正降低阅读成本时使用。

## 多角度研究

对影响下一阶段的开放问题，Skill 会同时寻找权威资料、源码与 Issue、工程实践帖子、替代方案和失败反例，并记录版本、环境相似度、可信度和对当前决策的影响。网上帖子用于拓宽视角，不会被直接当成当前系统事实。

本项目采用 MIT License。
