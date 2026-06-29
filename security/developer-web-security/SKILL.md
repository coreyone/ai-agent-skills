---
name: developer-web-security
description: Use when task matches developer-web-security engineering guidance for architecture, testing, performance, security, and review.
---

# 🛡️ Web Security Hardening: Bot Defense & Attack Mitigation

## When to use

Use this skill when the task is primarily about engineering and this guidance is the most relevant operating rule set.

## When not to use

Do not use this skill as the primary guide when another skill has a tighter domain fit for the requested output.

## Trigger cues

- Request explicitly references `developer-web-security` or this source file.
- Request language includes terms like: developer, web, security.
- Keywords include: implementation, TDD, tests, architecture, performance, web security, code review.

## Routing boundary

- Primary for code quality, test strategy, security hardening, and performance engineering.
- Do not use as primary for product positioning or conversion copy strategy.

## Inputs required

- Goal or task request
- Current constraints (time, scope, platform, risk)
- Existing artifacts (code, docs, screenshots, metrics) when available
- Source of truth: `subagents/rules/developer/developer-web-security.md`

## Instructions

1. Read [references/source.md](references/source.md) first.
2. Extract the non-negotiable rules and translate them into a short execution checklist.
3. Apply the checklist to the current task, produce concrete outputs, and avoid abstract recommendations.
4. Validate outcomes with evidence (tests, screenshots, logs, diffs, or written audit findings).
5. Record decisions and tradeoffs so another engineer can continue without re-discovery.

## Output format

- Primary decision/output: Implementation approach, test coverage, and risk controls.
- Summary: one-paragraph decision or result
- Actions: compact checklist with owners and status
- Evidence: links/paths to artifacts proving completion
