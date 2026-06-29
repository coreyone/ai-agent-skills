# Software Maestro

Capability orchestra for AI IDE agents. Conducts product strategy, design systems, and engineering execution from a single developer baton.

## Install

```bash
curl -sSL https://www.skills.sh/install.sh | sh -s -- coreyone/software-maestro
```
*(Alternative: clone directly to target AI IDE config/skills directory)*

## PM Core Rules (First Principles)

*   **Customer truth > roadmaps**: Validate user behavior before coding features. Strategy is deciding what *not* to build. Radical execution transparency.
*   **High-intent strategy**: Maximize goal certainty, minimize user effort. Quality is a non-negotiable product feature.
*   **Decouple or cascade**: Isolate dependencies (API, DB, UI). Timeout early, retry with jitter, circuit-break external integrations. Keep failures local.
*   **Visual density & hierarchy**: Typography-first, strict grids, size/weight/whitespace hierarchy. Every element earns its spot.
*   **Wayfinding (IA)**: Structure for instant orientation. Clear answers: Where am I? What’s here? What’s next? Predictable labels, map to mental maps.
*   **Tactile interaction**: Don't make them think. Recognition over recall. Max 5–7 choice boundaries. Design for "good enough" selection (satisficing).
*   **Inclusive/A11y**: WCAG AA (4.5:1 contrast). Min 48px touch zones. Full keyboard/ARIA support.
*   **Responsive density**: Desktop F-pattern. Mobile thumb zones. Tablet: hover-independent layouts.
*   **Inputs & Conversion**: Single-column forms. Labels over inputs. Validate on blur. One primary CTA. Failures must preserve user data and provide immediate recovery options (RFC 7807).
*   **Data = truth**: Standardize event naming (`object:action`). Consolidate namespaces; push variations to properties. Strip PII at boundaries.
*   **Zero-Downtime changes**: Database migrations via Expand/Contract. Code must support both old and new schemas during deploy windows.

## Taxonomy

```
├── product/          # Strategy & execution (create-prd, product-management, michael-bolton-rule, swarm-rules, god-marduk)
├── design/           # Aesthetic rules, responsive layout, motion, skeletons, empty states
├── engineering/      # Code quality, system architecture, resiliency, test-driven dev, tech-stack
├── data-and-api/     # REST/GraphQL API design, database schemas, ORM models, caching
├── security/         # Authentication protocols, identity keys, secure cookies, keychain
├── growth/           # Commerce UX optimization, conversions audit, copywriting principles, event tracking
└── quality/          # Performance debugging, telemetry observability, deployments, a11y audit
```
