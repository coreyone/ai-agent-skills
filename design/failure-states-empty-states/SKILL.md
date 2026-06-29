---
name: failure-states-empty-states
description: Use when designing user feedback loops, load fallbacks, skeleton screens, error boundaries, empty states, and offline retry screens.
---

# 🛑 Core Philosophy: How an application handles failure defines the quality of its user experience.

## When to use

Use this skill when designing layout fallbacks (skeletons), coding React/Svelte error boundaries, creating empty lists states, displaying validation alerts, and handling offline network disconnect notifications.

## When not to use

Do not use this skill for backend API schema design, analytical telemetry naming plans, or continuous delivery deployments.

## Trigger cues

- Key terms: empty state, loading state, error boundary, skeleton screen, offline recovery, feedback loop, fallback layout, system exception UI, input validation UI, active state indicator.
- Designing component layouts, handling API load failures in UI, setting up empty dashboards, or creating error alerts.

## Routing boundary

- Primary for frontend visual fallbacks, UX errors, layout states, loading skeletons, and interactive recovery states.
- Secondary to `developer-web-performance` for core optimization tasks.

## Inputs required

- Target frontend framework (React, SwiftUI, SvelteKit, etc.)
- Specific component contexts (e.g., table data, dashboard layout)
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing UI frameworks and component kits (e.g., React, Tailwind, SwiftUI, shadcn).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand microinteractions, skeletons, and error messages.
4. Establish visual loading fallbacks (skeletons matching layout proportions) instead of bare loading spinners.
5. Code component-level error boundaries to isolate failures and keep the rest of the application responsive.
6. Design empty states that provide a motivational prompt and a clear call to action (CTA).
7. Incorporate clear offline indicators with automatic input caching.

## Output format

- Primary decision/output: UI Fallback designs, error boundary code templates, and copy specifications for failure states.
- Summary: One-paragraph overview of fallback UX.
- Actions: Verification checklist for loader skeletons, error scope containment, and copy clarity.
