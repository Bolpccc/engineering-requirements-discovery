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
- advances one high-impact uncertainty at a time;
- defines the smallest safe next engineering iteration;
- maintains the semantic equivalents of Requirements, Engineering Plan, and Engineering Notes;
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
```

The skill is self-contained. If a compatible interview or ideation skill is already installed, it may provide the conversational interview, but no upstream skill is required.

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
- 默认每轮只推进一个最关键的不确定性；
- 以“下一轮工程验证是否已经足够清晰”为完成条件；
- 维护 Requirements、Engineering Plan、Engineering Notes 三种稳定语义；
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

三类文档的语义稳定，但文件名、存储介质和颗粒度由项目决定。近期阶段写具体，远期阶段保持粗略；需求和计划表达当前最佳认知，而不是不可修改的合同。

本项目采用 MIT License。
