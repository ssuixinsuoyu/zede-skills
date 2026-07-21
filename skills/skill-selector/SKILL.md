---
name: skill-selector
description: Select and invoke the most appropriate installed Agent Skill for a request. Use when the user explicitly asks which Skill to use, is unsure which Skill fits, asks to compare or route among several Skills, invokes $skill-selector, or gives a multi-stage request whose correct first Skill is unclear. Also use when the user gives feedback intended to improve this selector's persistent routing behavior. Do not use when the user has already named a valid Skill or the request clearly maps to one specific Skill.
---

# Skill Selector（Skill 选择器）

Choose the best installed Skill for the user's immediate deliverable. Invoke it only when the user also asks to perform the task; if the user asks only which Skill fits, recommend it and stop.

## First-Use Gate

Before the first selection, check `~/.skill-selector/config.json`. If `onboardingVersion` is not `1`, explain every rule below in the user's language and ask the user to confirm understanding. Do not select or invoke another Skill until the user confirms. After confirmation, record `onboardingVersion: 1` and the acceptance time locally. Repeat onboarding only when the version changes or the user asks to review the rules.

Explain all of these rules:

1. Select only Skills confirmed to be installed; never invent a Skill.
2. Match the requested deliverable and workflow, not keywords alone.
3. Select one primary Skill; chain another only when the first Skill's completed output is required by the next.
4. Ask the user when the goal, input, output, platform, path, target, naming, or expected result is not specific enough to choose safely.
5. Respect an explicitly named valid Skill unless it is missing, unsafe, incompatible, or conflicts with higher-priority instructions.
6. Use no Skill when the base Agent can handle the request more directly.
7. Feedback can improve this selector, but ambiguous feedback must be clarified and persistent changes must be confirmed and validated.
8. Verify the selected Skill, reasoning, constraints, and result before presenting the output.
9. Show user-facing Skill names as `English（中文）`; preserve the underlying English identifier for invocation.
10. Never select `skill-selector（Skill 选择器）` as its own target.

## Clarification Gate

Before choosing, identify missing details that could materially change the selected Skill or its deliverable. Ask only the smallest number of blocking questions. Continue without questions when the answer is available from the current context or the assumption is harmless and reversible.

Do not silently decide when any of these are unclear:

- whether the user wants research, planning, creation, editing, execution, or management
- the target platform, file, repository, account, or Agent environment when it changes the workflow
- whether the user wants a one-off result or a persistent Skill-level change
- which source of truth to use when similarly named Skills conflict
- the expected output format when candidates produce different artifacts

## Selection Workflow

1. Identify the concrete result the user wants now, not merely the broad topic.
2. Read available Skill names and descriptions from the current session catalog. If incomplete, inspect only documented Agent Skill directories and read metadata before opening full Skill bodies.
3. Build a shortlist of at most three Skills whose promised deliverables match the request.
4. Prefer the Skill that directly owns the immediate deliverable. For a multi-stage request, choose the earliest blocking deliverable rather than running every possibly relevant Skill.
5. Select exactly one Skill when the evidence is sufficient. Say `选择 Display Name（中文），调用标识：$skill-id。原因：一句话。`
6. If the user asks only for a recommendation or comparison, stop after the selection. If the user also asks to perform the task or explicitly says to invoke it, read the selected Skill completely and follow its instructions.
7. Ask one concise clarification when the leading candidates would produce materially different results and the request does not reveal which result the user wants.
8. If no installed Skill is a meaningful match, say that no Skill is needed and handle the request normally only when the user also asked for the underlying task.

## Selection Rules

- Match by deliverable and workflow, not by shared keywords alone.
- Prefer a specialized Skill over a broad router when both lead to the same final result.
- Use a router Skill when the request belongs to that router's bounded toolkit but the correct child route is not yet clear.
- Never select `$skill-selector` as its own target.
- When another router invokes this Skill, never route back to that caller.
- Do not invoke several Skills merely to appear thorough.
- Do not force a Skill onto simple questions that the base Agent can answer directly.
- Do not invent unavailable Skills. Suggest installation only as an optional next step.
- Read `agents/openai.yaml` when available and use its documented `display_name`. Show the exact `$skill-id` separately so the display name never changes the invocation identifier.
- If no Chinese display name exists and the translation is ambiguous, ask the user instead of silently naming it.

## Tie-Breaking

Compare overlapping candidates in this order:

1. Exact output match
2. User's explicitly stated workflow or platform
3. Required tools and available inputs
4. Narrower scope
5. Fewer unnecessary steps

Ask one question if the tie remains.

## Feedback-Driven Iteration

Treat direct feedback about selection, naming, questioning, routing, or verification as a possible request to improve this Skill.

1. Restate the concrete persistent behavior that would change.
2. Ask for clarification when the feedback could imply multiple rules or affect unrelated routes.
3. Distinguish a one-time preference from a reusable Skill rule. Do not write personal task facts into this generic Skill.
4. Show the proposed Skill-file change and obtain confirmation before writing unless the user explicitly requested that exact persistent change.
5. Preserve the current version in `~/.skill-selector/snapshots/` before modification.
6. Make the smallest relevant edit to `SKILL.md` or `agents/openai.yaml`.
7. Run `quick_validate.py` and test at least one matching case, one ambiguous case, and one no-Skill case.
8. Keep the update only when validation passes; otherwise restore the snapshot and report the failure honestly.

## Result Verification

Before presenting a selection or final result, verify all applicable checks:

- The selected Skill exists and its `SKILL.md` is readable.
- Its description and promised output directly match the user's immediate deliverable.
- No unresolved ambiguity would materially change the choice.
- The selection does not violate an explicit user instruction or higher-priority rule.
- The selector did not select itself and did not add unnecessary Skills.
- The displayed name follows `English（中文）`, comes from documented metadata when available, and is shown alongside the exact invocation identifier.
- If another Skill was executed, that Skill's own validation requirements were completed.

State failed or unverified checks honestly. Do not report intended actions as completed work.

## Examples

- `我该用哪个 Skill 把口播稿做成可点击的录屏页面？` -> recommend `Zede Interactive Explainer（交互式视觉讲解）`, show `$interactive-explainer`, and stop because the user asked only which Skill fits.
- `请判断该用哪个 Skill，并直接把这份口播稿做成可点击的录屏页面。` -> select `$interactive-explainer`, then invoke it because execution was explicitly requested.
- `这个选题怎么写成完整口播稿？` -> select the installed video-copywriting Skill, not a topic-discovery Skill.
- `我想系统学 Python` -> distinguish roadmap planning from starting an interactive lesson; ask one question if the immediate result is unclear.
- `帮我检查 Codex 和 Claude Code 里的 Skill 冲突` -> select the installed Skill-management Skill.
- `把这句话翻译成英文` -> use no Skill and translate directly.

