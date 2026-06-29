---
name: the-elements-of-style-principles
description: "Trigger: writing style, copy editing, simple copy, prose check, text clarity. Scope: Writing clear, direct, and concise English copy. Boundary: Excludes code formatting or marketing value propositions."
---

# PRINCIPLE I: STRUCTURAL INTEGRITY (The Architecture of Writing)

## When to use

Use this skill when the task is primarily about growth and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `The-Elements-of-Style-Principles` or this source file.
- Request language includes terms like: The, Elements, of, Style, Principles.
- Keywords include: CRO, funnel, CTA, conversion, commerce UX, positioning, marketing copy.

## Routing boundary

- Primary for conversion, messaging, launch funnel, and commerce/audit optimization.
- Do not use as primary for core infrastructure, API contracts, or test architecture.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `subagents/rules/marketing/The-Elements-of-Style-Principles.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: Conversion path, message hierarchy, and experiment priority.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
