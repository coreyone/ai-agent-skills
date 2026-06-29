---
name: system-architecture-rules
description: "Trigger: clean architecture, hexagonal architecture, domain model, state machine, boundary decoupling. Scope: Software modular design, dependency boundaries, architectural layering. Boundary: Excludes frontend aesthetic styling."
---

# 🏗️ Core Philosophy: Architectural integrity enables evolutionary change.

## When to use

Use this skill when designing components, establishing boundaries between system layers, selecting structural design patterns, or defining dependency graphs for Web and iOS systems.

## When not to use

Do not use this skill for raw code optimization, writing inline tests, or styling UI elements.

## Trigger cues

- Key terms: clean architecture, MVVM, modularity, layers, Swift Package Manager, monorepo, ports and adapters, hexagonal architecture, domain-driven design, dependencies.
- Requesting structural patterns, directory setups, or module boundaries.

## Routing boundary

- Primary for design patterns, high-level code layout, structural boundaries, and decoupling.
- Secondary to `developer-development-rules` for low-level clean code rules.

## Inputs required

- Target platform constraints (iOS vs Web)
- High-level business context and scalability requirements
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing technology stack (e.g., Next.js, React, Express, Swift).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to align on first-principles system design.
4. Draft an architecture diagram or dependency topology matching the target constraints using the existing stack.
5. Formulate the boundary interfaces and data transfer protocols before implementation.
6. Record major architectural tradeoffs in an Architecture Decision Record (ADR) format.

## Output format

- Primary decision/output: System component diagram, dependency flow, and boundary definitions.
- Summary: One-paragraph architectural summary.
- Actions: Verification checklist for design constraints.
