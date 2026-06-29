---
name: design-information-architecture-rules
description: "Trigger: sitemap, navigation, menu structure, wayfinding, labeling, search facets, routing links. Scope: Visual hierarchies, wayfinding, navigation model, sitemaps. Boundary: Excludes backend route handlers or page performance tuning."
---

# Information Architecture (IA) Rules — First Principles + Execution Playbook

## When to use

Use this skill when the task is primarily about design and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `design-information-architecture-rules` or this source file.
- Request language includes terms like: design, information, architecture, rules.
- Keywords include: IA, usability, responsive layout, design system, aesthetic direction, motion.

## Routing boundary

- Primary for UX architecture, visual hierarchy, responsiveness, and interface behavior.
- Do not use as primary for backend architecture, threat modeling, or release operations.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `subagents/rules/design/design-information-architecture-rules.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: User flow clarity, interaction model, and visual system constraints.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
