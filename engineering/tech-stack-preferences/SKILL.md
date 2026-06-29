---
name: tech-stack-preferences
description: Align architecture and implementation decisions to the preferred technology stack.
---

# Tech Stack Preferences

## When to use

Use this skill when the task is primarily about delivery and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `tech-stack-preferences` or this source file.
- Request language includes terms like: tech, stack, preferences.
- Keywords include domain-specific execution constraints and delivery standards.

## Routing boundary

- Use as primary only when its source guidance is the closest match to the request.
- Escalate to orchestration skills when multiple domains conflict.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `subagents/tech-stack-preferences.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: Closest-fit operational decision for current task constraints.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
