---
description: Philosophy, values, and tactics for the legendary web front-end coder. A guide from a senior architect to a junior developer.
---

---
title: Performance-First Website Playbook
goal: Make every page feel instant by default.
principle: Ship HTML early, ship JavaScript late (or not at all).
---

# ⚡ Performance-First Instructions (Use When Natural)

## 1) Default to Server-Rendered HTML
- Render full HTML on the server for every navigable page.
- Ensure the first response contains meaningful content (no empty shells).
- Treat JavaScript as an enhancement, not a requirement.

## 2) Minimize Client-Side JavaScript
- Avoid SPA frameworks unless interaction complexity truly requires them.
- Prefer plain HTML + CSS for layout, navigation, and content.
- Use JavaScript only for:
  - progressive enhancement
  - optional interactivity
  - post-render optimizations

## 3) Optimize for First Paint, Not Architecture Fashion
- Measure success by:
  - Time to First Byte (TTFB)
  - Largest Contentful Paint (LCP)
  - Interaction readiness
- Do not introduce libraries that delay rendering or block HTML parsing.

## 4) Ship Content Before Chrome
- Eliminate:
  - animations that delay usability
  - popups that block content
  - unnecessary transitions
- The primary task must be usable immediately on page load.

## 5) Aggressively Cache Rendered HTML
- Cache full HTML responses at the CDN layer when possible.
- Use cache keys that vary only on what truly changes (auth, locale, pricing).
- Prefer cache invalidation over dynamic recomputation.

## 6) Prefetch Intelligently
- Prefetch next-likely HTML documents on:
  - hover
  - focus
  - viewport proximity
- Fetch HTML, not JSON blobs.
- Cancel prefetches when intent disappears.

## 7) Treat Navigation as Document Loads
- Use standard links (`<a href>`) for navigation.
- Avoid JS-only routing unless required.
- Allow the browser to do what it is already excellent at.

## 8) Keep the DOM Dense but Simple
- Favor fewer, information-rich pages over many thin ones.
- Optimize for scanning, not decoration.
- Dense does not mean cluttered; it means purposeful.

## 9) Progressive Enhancement Only
- The site must function fully with:
  - JavaScript disabled
  - slow connections
  - low-power devices
- Enhancements should improve speed or ergonomics, never gate access.

## 10) Assume Users Value Speed Over Delight
- Tradeoffs:
  - Speed > animation
  - Clarity > novelty
  - Reliability > trend alignment
- If a feature does not measurably improve task completion, remove it.

## 11) Instrument, Don’t Guess
- Track real-user metrics (RUM), not lab-only scores.
- Watch for regressions in:
  - TTFB
  - LCP
  - input latency
- Block merges that worsen baseline performance.

## 12) Make “Fast” a Cultural Constraint
- Treat performance budgets as non-negotiable.
- Require justification for:
  - new JS bundles
  - new frameworks
  - new client-side dependencies
- Default answer to “can we add this?” is “no — prove it.”

---
outcome: Pages that feel instant, resilient, and boring in the best possible way.
reference_model: McMaster-Carr-style performance pragmatism.
---
