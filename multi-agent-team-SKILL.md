---
name: multi-agent-team
description: Coordinate bounded, parallel subtasks with Codex agents when complex work benefits from separate ownership or the user requests a multi-agent team. Supports explicit cross-window role teams through Agent Hub.
---

# Multi Agent Team

## Overview

Run a minimal Codex team instead of a loose collection of personas. Keep the main agent as the manager, delegate bounded work to sub-agents when available, and integrate their results into one coherent outcome.

Use available in-task subagents for ordinary delegation. Use Agent Hub for a user-requested cross-window team when it is available. Preserve an explicit manager-only role assignment; otherwise the lead may complete independent work and integrate results while workers run. Missing role windows should not prevent unrelated authorized work.

## Core Pattern

Use the smallest team that can close the loop:

- **Manager**: clarify the goal, split the work, assign ownership, integrate results.
- **Executor**: implement, research, draft, or produce the requested artifact.
- **Reviewer**: independently verify correctness, risks, gaps, and tests.

Add more agents only when their responsibilities are genuinely independent. Prefer two or three agents over a large theatrical cast.

## Workflow

1. Decide whether sub-agents are warranted. Use them for complex, ambiguous, parallelizable, or high-risk tasks; handle simple tasks directly.
2. Define the manager brief: user goal, current assumptions, success criteria, constraints, and final output shape.
3. Split work into disjoint subtasks. Give each agent a clear role, scope, files or responsibility boundaries, deliverables, and validation criteria.
4. For cross-window mode, register the manager and call `team_bootstrap` in Agent Hub before implementation or specialist work begins.
5. Run agents in parallel when subtasks do not overlap. Use explorers for codebase questions and workers for implementation.
6. Keep the lead active: coordinate handoffs, integrate results, and do useful work outside the workers' ownership. Use a coordination-only manager when the user requests that separation.
7. Review returned outputs, reconcile conflicts, run appropriate validation, and produce one final answer.

## Delegation Brief

Give agents compact, structured handoff cards. Do not paste an unbounded transcript.

```text
<!-- MULTI_AGENT_TEAM_MESSAGE -->
Role: <manager | explorer | executor | reviewer>
Mission: <one concrete task>
Context: <only the facts needed>
Ownership: <files, modules, or responsibility boundaries>
Constraints: <style, safety, user preferences, no-overlap rules>
Deliverables: <exact output expected>
Validation: <checks, tests, review criteria>
Return format: <summary, changed files, risks, commands run>
<!-- /MULTI_AGENT_TEAM_MESSAGE -->
```

Always tell worker agents that other people or agents may be editing the codebase, that they must not revert unrelated changes, and that they should list changed files.

## Example Rosters

Choose only the roles the task needs. These examples do not require creating every listed role.

- **Code change**: `manager`/画饼的, `frontend`/贴膜的, `backend`/搬砖的, `reviewer`/挑刺的.
- **Writing/article**: `manager`/甩锅办主任, `researcher`/百度搬运工, `writer`/文字纺织工, `reviewer`/找茬 Olympics 冠军.
- **Plan/PPT/report**: `manager`, `researcher`, `analyst`/数据算命师, `writer`, `designer`/PPT贴膜师傅, `reviewer`.
- **Product design**: `manager`, `researcher`, `analyst`, `designer`, `reviewer`.

## Role Boundaries

The strict role boundaries below apply when the user selects that role-separated team. For ordinary in-task delegation, set boundaries per subtask; the lead may implement and validate work that does not overlap a worker's assignment.

For code projects:

- `manager` / 画饼的: receive requirements, split work, assign tasks, track progress, coordinate contracts, final acceptance. Must not write code or edit files.
- `frontend` / 贴膜的: HTML, CSS, JavaScript, UI components, layouts, responsive behavior, frontend API integration. Must not implement backend APIs, database, server logic, or deployment.
- `backend` / 搬砖的: APIs, database schema, business logic, interface docs, server work. Must not write UI pages, CSS, or frontend interactions.
- `reviewer` / 挑刺的: review code and outputs, find bugs and risks, pass or return work. Must not directly modify code or assign tasks.

For general projects:

- `manager` / 甩锅办主任: split, assign, coordinate, accept. Must not produce specialist deliverables.
- `researcher` / 百度搬运工: gather facts, sources, data, examples, background, references. Must not write final conclusions or main copy.
- `writer` / 文字纺织工: write articles, plans, reports, scripts, emails, and revisions. Must not invent data or do analysis/visual design.
- `analyst` / 数据算命师: analyze data, verify logic, make judgments. Must not collect raw research, write full copy, or make visuals.
- `designer` / PPT贴膜师傅: visual design, layout, PPT, posters, charts, visualization. Must not write content or analyze data.
- `reviewer` / 找茬 Olympics 冠军: check quality, accuracy, logic, omissions, contradictions. Must not rewrite directly or assign tasks.

## Coordination Rules

- Do not delegate the same unresolved question to multiple agents unless comparing independent approaches is useful.
- Do not let multiple workers write the same files unless the manager intentionally serializes their work.
- Wait for agents only when their result blocks the next step; otherwise keep doing useful manager work.
- Trust explorer findings by default, but integrate them with local context before acting.
- Treat reviewer feedback as input to fix or disclose, not as automatic truth.
- Close completed agents when their results are no longer needed.

## User Triggers

When the user says any of these, start this workflow without asking for a template:

```text
开小队：<任务>
四人小队：<任务>
跨窗口小队：<任务>
拉起跨窗口小队：<任务>
启动多角色小队
用多 Agent 模式做这个
让产品开发小队处理
开一个管理 Agent、执行 Agent、验收 Agent
像那个 Codex 多 Agent 视频一样跑
kai xiao dui: <task>
four-agent team: <task>
launch cross-window team: <task>
qi dong duo jue se xiao dui
duo agent mo shi
product development team
```

If no sub-agent tool is available, perform the useful planning, implementation, and review passes locally and state that independent agents were unavailable. Do not fabricate agents, agent conversations, or separate review results.

## Cross-Window Shortcuts

When the user says `拉起跨窗口小队：<任务>` or `launch cross-window team: <task>`, use Codex thread tools when available to create or continue separate role threads. Each role thread should register itself with Agent Hub, then read tasks and inbox messages from the shared hub.

For an explicit cross-window team, use the available Agent Hub startup workflow:

1. Call `start_cross_window_team` in Agent Hub with the manager id and user request.
2. If `missing_agents` is non-empty, create role threads or ask the user to open them using the returned `role_window_prompts`.
3. Role windows that receive a prompt must call `quick_register_role` when the user says shortcuts such as `我是贴膜的`.
4. While waiting, continue non-overlapping authorized work unless the user assigned a coordination-only role. Do not claim missing role windows were created.
5. Use `hub_snapshot`, `task_list`, and `message_inbox` to track progress and route follow-ups.

Use these role names and IDs:

- `manager` / `画饼的`
- `frontend` / `贴膜的`
- `backend` / `搬砖的`
- `reviewer` / `挑刺的`
- `researcher` / `百度搬运工`
- `writer` / `文字纺织工`
- `analyst` / `数据算命师`
- `designer` / `PPT贴膜师傅`

When a fresh role window says one of these shortcuts, register it immediately:

```text
我是画饼的
我是贴膜的
我是搬砖的
我是挑刺的
我是百度搬运工
我是文字纺织工
我是数据算命师
我是PPT贴膜师傅
```

If thread creation tools are unavailable, give the user the four one-line role prompts instead of pretending that windows were created.

## Design-Only Tasks

When the user asks for planning, architecture, product design, or a solution proposal without implementation, use agents for independent thinking but do not create code changes. Final output should include:

- role structure used,
- proposed solution,
- execution steps,
- validation checklist,
- risks and open decisions.

## Final Response

Report the integrated result, not every agent's raw transcript. Include:

- what roles ran,
- what changed or what decision was made,
- validation performed,
- remaining risks or follow-up options.
