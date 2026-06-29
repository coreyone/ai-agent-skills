---
name: god-marduk
description: "Trigger: project task list, task decomposition, phase planning, master orchestration, delivery governance. Scope: Project sequencing, task checklist creation, operating governance. Boundary: Excludes tactical code debugging."
---

# 🪐 God-Marduk: Master Task Orchestrator

## When to use

Use this skill when the task is primarily about orchestration and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `god-Marduk` or this source file.
- Request language includes terms like: god, Marduk.
- Keywords include: phase plan, task decomposition, ownership, delegation, sequencing, execution loop.

## Routing boundary

- Primary when choosing order of work, decision rights, or cross-functional operating model.
- Secondary when task is purely tactical implementation inside one specialty.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `god-Marduk.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: Execution order, ownership map, and control-loop checkpoints.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
