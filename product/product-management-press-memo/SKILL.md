---
name: product-management-press-memo
description: "Trigger: press release, PM memo, PRD memo, product launch narrative, launch story. Scope: Writing press releases and future launch stories for project alignment. Boundary: Excludes writing functional code or task tracking."
---

# product management press memo

## When to use

Use this skill when the task is primarily about product and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `product-management-press-memo` or this source file.
- Request language includes terms like: product, management, press, memo.
- Keywords include: PRD, success metrics, goals/non-goals, user journey, roadmap, launch memo.

## Routing boundary

- Primary for problem definition, PRD scope, metrics, and product narrative.
- Do not use as primary for deep UI styling or low-level code implementation.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `subagents/product manager/product-management-press-memo.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: Problem scope, measurable outcomes, and what not to build yet.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
