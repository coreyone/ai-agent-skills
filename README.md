# AI Agent Skills

Capability deck for AI IDE agents and assistants (e.g. OpenAI, Anthropic, Antigravity). Syncs product, design, and engineering contexts.

## Install

Run:
```bash
curl -sSL https://www.skills.sh/install.sh | sh -s -- coreyone/ai-agent-skills
```
*(Alternative: clone directly to target AI IDE config/skills directory)*

## PM Core Rules (First Principles)

*   **Structure > polish**: Confusing models fail. Clear architecture scales; UI updates don't fix broken logic.
*   **Decouple or cascade**: Isolate dependencies (API, DB, UI). Timeout early, retry with jitter, circuit-break external integrations. Keep failures local.
*   **Data = truth**: Standardize event naming (`object:action`). Consolidate namespaces by pushing variations to event properties. Strip PII at boundaries.
*   **Fallback UX**: Skeletons must match active layout dimensions (spinners increase perceived wait time). Empty states need motivation + CTA. offline actions require auto-caching.
*   **Zero-Downtime database changes**: Run database migrations via Expand/Contract. Code must support both old and new schema structures simultaneously during deploy windows.
*   **Security isolation**: Access tokens belong in secure sandboxes (iOS Keychain or HttpOnly/Secure cookies). Block XSS local storage extraction. Cryptographically verify JWT signatures.

## Taxonomy

```
├── product/          # Strategy & execution (create-prd, product-management, michael-bolton-rule, swarm-rules)
├── design/           # Aesthetic rules, responsive layout, motion, skeletons, empty states
├── engineering/      # Code quality, system architecture, resiliency, test-driven dev, tech-stack
├── data-and-api/     # REST/GraphQL API design, database schemas, ORM models, caching
├── security/         # Authentication protocols, identity keys, secure cookies, keychain
├── growth/           # Commerce UX optimization, conversions audit, copywriting principles, event tracking
└── quality/          # Performance debugging, telemetry observability, deployments, a11y audit
```
