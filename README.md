# AI Collaboration Standard

> Central governance repository for the user's AI-assisted software and creative projects.  
> AI 协作标准库：统一管理项目协作方式、任务交接、交付追溯与质量验收。

## Purpose / 目的

This repository records the user's current working philosophy and reusable collaboration rules. It is the common reference for project-specific repositories; it does not replace their product requirements, architecture decisions, or task books.

本仓库保存用户目前形成的 AI 协作理念与通用规则，作为不同项目共同遵循的标准。它不取代各项目自己的产品需求、架构决策和具体任务书。

## Current operating model / 当前协作模式

| Role | Responsibility |
|---|---|
| User / 用户 | Final decision-maker; approves product direction, major changes, acceptance and progression. |
| Google Gemini | Primary project planner and implementation lead; analyzes repositories, proposes plans, drafts task books, produces code/docs and performs implementation work. |
| ChatGPT GPT | Independent reviewer and quality gate; reviews plans, task books, code, evidence and deliverables; does not automatically take over planning. |
| Antigravity | Optional local execution agent; handles local file staging, extraction, integration, build/test execution and Git delivery under explicit project rules. |

**Core principle:** Gemini leads planning and implementation; GPT independently reviews and accepts; the user decides. Antigravity is an execution mechanism, not an additional product decision-maker.

## Repository map

- `standards/` — collaboration and governance standards.
- `workflows/` — end-to-end operating procedures.
- `templates/` — reusable task, handoff and review templates.
- `projects/` — project onboarding and project-specific rule templates.
- `DELIVERY/` — unified delivery intake, independent review staging and confirmed archive area.
- `CHANGELOG.md` — changes to this standard library.

## Documents

- [双 AI 协作与项目交付管理规范 V1.1（中文）](standards/双AI协作与项目交付管理规范_V1.1.md)
- [AI Collaboration and Project Delivery Standard V1.1 (English)](standards/AI-Collaboration-and-Project-Delivery-Standard-V1.1.md)
- [用户项目方向与协作偏好](standards/用户项目方向与协作偏好.md)
- [标准工作流程](workflows/标准工作流程.md)
- [项目接入指南](projects/项目接入指南.md)
- [正式任务书模板](templates/正式任务书模板.md)
- [交付回执模板](templates/交付回执模板.md)
- [独立审查报告模板](templates/独立审查报告模板.md)
- [交付中心说明](DELIVERY/README.md)

## Status and authority

V1.1 is a consolidated working draft based on the user's V1.0 proposal and subsequent discussion. Rules explicitly stated by the user are marked as confirmed. Additional operational safeguards proposed during consolidation are marked as recommendations and should not silently be treated as approved product decisions.

本库 V1.1 是基于用户提供的 V1.0 规范及后续讨论整理的工作草案。用户明确提出的规则标记为“已确认”；整理过程中补充的操作性建议标记为“建议”，不得擅自视为用户已经批准的项目决策。

The latest project-specific instruction and the user's explicit decision take precedence over this general standard when they conflict.
