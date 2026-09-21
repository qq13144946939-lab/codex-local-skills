# Codex Local Skills / Codex 本地技能集合

## Overview / 项目简介

This repository provides a curated collection of Codex skill definitions adapted
for practical software-engineering workflows. It turns repeatable working
principles into reviewable, composable guidance for communication, deliverable
quality, collaboration, frontend design, safe maintenance, and authorized
security analysis.

本仓库整理了一组面向实际软件工程流程的 Codex 技能定义，将可复用的工作原则沉淀为可审查、可组合的指导，覆盖沟通表达、交付质量、协作开发、前端设计、安全维护和经授权的安全分析。

## Included skills / 收录技能

| Skill | English description | 中文说明 |
| --- | --- | --- |
| `caveman` | Optional response compression that preserves technical detail, evidence, uncertainty, and safety information. | 可选的回复压缩模式，保留技术细节、证据、不确定性和安全信息。 |
| `full-output-enforcement` | Keeps requested deliverables complete without replacing implementation with placeholders or fabricated progress. | 确保交付内容完整，避免用占位符或虚构进度替代实际实现。 |
| `gpt-taste` | Supports distinctive marketing and portfolio interfaces with editorial typography and purposeful motion when appropriate. | 在合适的场景下，以编辑式排版和有目的的动效支持有辨识度的营销页与作品集界面。 |
| `multi-agent-team` | Coordinates bounded parallel work and integrates results without inventing agents or review outcomes. | 协调边界清晰的并行工作并整合结果，不虚构智能体或评审结论。 |
| `ponytail` | Favors the smallest safe implementation while preserving validation, accessibility, security, and error handling. | 倾向于最小且安全的实现，同时保留验证、无障碍、安全和错误处理。 |
| `reverse-skill-router` | Routes authorized reverse-engineering and security-analysis work to an appropriate specialist workflow. | 将经授权的逆向工程和安全分析任务路由至合适的专业流程。 |

Each skill is available under `skills/<skill-name>/SKILL.md`.

每个技能均位于 `skills/<skill-name>/SKILL.md`。

## Design principles / 设计原则

- Follow the user's intent, the existing architecture, and established project conventions. / 遵循用户意图、现有架构和项目既有约定。
- Prefer simple, maintainable changes without removing necessary validation, accessibility, security controls, or error handling. / 优先选择简单、可维护的改动，但不牺牲必要的验证、无障碍、安全控制或错误处理。
- Keep claims evidence-based: do not fabricate tool output, agent activity, test results, or project metrics. / 所有结论以证据为基础，不虚构工具输出、智能体活动、测试结果或项目指标。
- Treat security-related guidance as authorization-bound and scope-sensitive. / 将安全相关指导严格限定在已授权范围和明确边界内。
- Keep credentials, logs, machine-specific state, and local backup files out of the repository. / 不将凭据、日志、本机状态和本地备份文件放入仓库。

## Usage / 使用方式

Use a selected `SKILL.md` as a Codex skill entrypoint and install it through
the skill loader supported by your Codex-compatible environment. The skills are
composable; explicit user requirements always take precedence.

将所需的 `SKILL.md` 作为 Codex 技能入口，并通过兼容环境支持的技能加载器安装。各技能可以组合使用；用户的明确要求始终具有优先级。

## Project status / 项目状态

This is the initial public release of a locally maintained adaptation set.
Public usage metrics are not yet established; the goal of this release is to
make the workflow guidance transparent, reviewable, and reusable.

这是本地维护适配集的首次公开发布。目前尚未形成公开使用指标；本次发布旨在让工作流程指导透明、可审查、可复用。

## Scope and attribution / 范围与署名

These files are community-maintained adaptations and are not an official OpenAI
product. Review the licensing and attribution requirements of upstream material
before redistributing or modifying the skills further.

这些文件是社区维护的适配版本，并非 OpenAI 官方产品。再次分发或继续修改前，请审查上游材料的许可证和署名要求。

Only the current `SKILL.md` files and this README are included. Local backup
files and machine-specific state are intentionally excluded.

仓库只包含当前版本的 `SKILL.md` 和本 README，已明确排除本地备份文件与本机状态。
