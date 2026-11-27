# AI Collaboration and Project Delivery Standard V1.1

- Status: Working draft; explicit user decisions take precedence.
- Scope: Software projects. Creative projects may reuse the role model with domain-specific quality criteria.
- Final decision-maker: The user.

## 1. Purpose

Establish a collaboration model in which Google Gemini leads project planning and implementation, ChatGPT GPT acts as an independent reviewer and quality gate, and Antigravity or another local agent may perform controlled local execution and delivery.

The goals are to use each system's strengths, reduce duplicated planning and self-approval, preserve user authority, and make every delivery traceable and evidence-based.

## 2. Roles and authority boundaries

### 2.1 User — final decision-maker (confirmed)
The user defines goals and priorities, approves product direction and major changes, accepts deliverables, and decides whether to merge or proceed.

Major requirement changes, irreversible actions, compatibility-breaking changes, important data-format changes, removal of important features, and merges into the main branch require explicit user approval under the project rules.

### 2.2 Google Gemini — project lead (confirmed)
Gemini leads planning and implementation:
- Read repository structure, documentation, source code, and history.
- Identify current state, completed work, defects, risks, and open items.
- Proactively propose next steps, technical approaches, priorities, and task breakdowns.
- Draft the initial formal task specification.
- Implement code and documentation; run tests, debug, and fix issues.
- Respond to GPT review findings or provide evidence-based technical rebuttals.
- Supply actual delivery records and test evidence.

Gemini may choose implementation details within the authorized scope. Technical autonomy does not grant authority to change product requirements. If repository facts conflict with the task specification, or scope/risk is unclear, Gemini must explain and pause the affected work rather than conceal deviations.

### 2.3 ChatGPT GPT — independent review and quality control (confirmed)
GPT is not the default overall planner or initial task-author. It must:
- Independently review Gemini's analysis, technical plans, and task specifications.
- Check requirement coverage, architecture boundaries, consistency, security, compatibility, and maintainability.
- Add verifiable tests, acceptance criteria, and risk controls.
- Respect reasonable technical alternatives; do not reject a design merely because it differs from GPT's preference.
- Inspect actual code changes, diffs, commits, test evidence, and deliverables.
- Evaluate each requirement against the approved task specification.
- Request missing evidence or corrections and assess Gemini's rebuttals on their merits.

A completion claim is not proof. After acceptance, GPT reports the result and outstanding issues; it does not automatically take over the next planning cycle unless the user asks.

### 2.4 Antigravity / local execution agent
Antigravity is an optional execution mechanism, not a third product decision-maker. When authorized by project rules, it may inspect staging files, extract and organize packages, apply changes, run builds/tests, perform Git operations, and prepare delivery records.

It must not independently change product requirements, expand scope, silently delete or overwrite historical deliverables, force-push, bypass review, or merge into the main branch. The target project's operating manual defines exact permissions.

## 3. Standard lifecycle

### Phase 1 — Gemini discovery and planning
1. Read the target repository and project-specific rules.
2. Verify the default branch, current commit, task state, and outstanding work where accessible.
3. Analyze current state, issues, dependencies, and risks.
4. Propose a plan, technical approach, priorities, and task breakdown.
5. Draft a complete task specification: context, baseline, goals, non-goals, scope, files, technical constraints, risks, tests, acceptance criteria, and delivery.
6. List assumptions and decisions that require the user's approval.

### Phase 2 — GPT independent review
1. Check completeness, correctness, and executability.
2. Separate substantive defects from acceptable design differences and personal preferences.
3. Explain findings with severity, rationale, evidence, and recommendations.
4. Add test matrices, acceptance criteria, security/privacy controls, and evidence requirements.
5. Return review findings and a revised task specification while preserving Gemini's sound planning framework.
6. Escalate major disagreements to the user.

### Phase 3 — Gemini implementation
1. Read the reviewed task specification and the latest repository state.
2. Implement the authorized code/documentation changes.
3. Run relevant tests and fix actionable failures.
4. Record actual scope, commands, results, failures, and environment limitations.
5. Explain conflicts or deviations; obtain user approval for material scope changes.
6. Deliver according to the project's Git and handoff rules.

### Phase 4 — GPT independent acceptance
1. Inspect the actual branch, commits, diff, and file contents.
2. Verify each task requirement.
3. Distinguish tests actually run, not run, blocked, and merely reasoned about.
4. Check regressions, omissions, privacy/security, compatibility, and documentation.
5. Issue one explicit result:
   - **Pass** — acceptance criteria are met; the user may consider the next phase.
   - **Conditional pass** — no blocking defect, but non-critical issues or limitations remain documented.
   - **Fail** — substantive defects or critical evidence gaps require correction.
6. The user decides whether to accept, merge, or start another phase.

### Phase 5 — Iteration
GPT records findings and open risks. Gemini uses the latest repository facts to propose the next plan. The user explicitly decides whether to start. No next phase starts automatically.

## 4. Minimum task specification

A formal task should include:
- Project context and current baseline (repository, branch, base commit).
- Goals and explicit non-goals.
- Requirements, constraints, and priorities.
- Implementation steps and file scope.
- Technical requirements, architecture boundaries, and compatibility.
- Risks, dependencies, assumptions, and approval gates.
- Test strategy, environment, and commands.
- Observable and verifiable acceptance criteria.
- Deliverables, branch/commit, and handoff requirements.
- Failure handling, rollback, and stop conditions.

Include a task ID, version, status, author/proposer, and target repository. Do not present assumptions or suggestions as approved requirements.

## 5. GitHub and delivery traceability

Every material delivery should be traceable to a task ID, task-specification version, and actual commit.

Record the repository, branch, base commit, delivery commit SHA, changed-file list, and test evidence. Preserve important original deliverables and review records.

### Recommended default: isolated delivery branches
Where adopted by the project:
- Use a separate branch per task iteration, e.g. `delivery/TASK-0001-R2`.
- Branch from the latest intended remote base and record its exact SHA.
- Do not push directly to main/master, force-push, or merge without explicit user approval.
- GPT reviews the actual delivery branch; the user decides whether to merge.
- If relevant base files changed or conflicts arise, compare and report before proceeding.

### Local staging
Projects may define a local staging directory. Follow the project operating manual. Staging files are generally excluded from version control; historical deliverables should not be silently overwritten. Each project must define its own paths and cleanup rules.

## 6. Evidence requirements

A delivery report should include:
- Repository and task ID/version.
- Base branch and base commit SHA.
- Delivery branch, delivery commit SHA, and commit URL.
- Added/modified/deleted file list.
- Build and test commands actually executed.
- Results, failures, skipped tests, and reasons.
- Known limitations, deviations, and unfinished work.
- Decisions required from the user.

Statements such as “looks correct,” “complete,” or “tests passed” without inspectable evidence are insufficient. Evidence should identify the environment and time. GPT independently verifies what it can access.

## 7. Disagreements

Gemini may challenge a GPT finding with concrete implementation details, evidence, trade-offs, and risks. GPT must reassess the evidence and correct its own mistakes when warranted. If disagreement remains, present both positions, supporting evidence, risks, and options to the user. No major requirement change may be implemented without user approval.

## 8. Operating principles

Gemini leads planning and implementation; GPT independently reviews and accepts; the user makes final decisions. Local agents operate only within delegated scope. Tasks must be clear and verifiable. Tests must be evidence-based. Changes must be traceable. Model self-attestation is not acceptance evidence. Quality must not be sacrificed for speed. Do not advance automatically without the user's explicit instruction.

## 9. Creative projects

Reuse the role model where useful, but replace software criteria with world-building consistency, character motivation, causal logic, timeline continuity, style, chapter quality, and text-version control.

## 10. Precedence and versioning

V1.1 consolidates the user's V1.0 proposal and subsequent discussion. Explicit user decisions take precedence. Recommendations must be adopted in the context of each project. Project-specific rules, the current task specification, and the user's latest explicit instruction take precedence over this general standard.
