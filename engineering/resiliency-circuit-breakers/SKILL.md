---
name: resiliency-circuit-breakers
description: Use when designing network clients, fault-tolerant requests, retry loops, fallback strategies, timeouts, and circuit-breaker state machines.
---

# 🛡️ Core Philosophy: Assume everything will fail, and design systems that degrade gracefully.

## When to use

Use this skill when implementing network requests (fetching data, posting mutations), designing backend integrations, writing microservices communication, creating resilience decorators, or defining request timeout and queue limits.

## When not to use

Do not use this skill for styling layout states, analytics event naming schemas, or setting up auth sessions.

## Trigger cues

- Key terms: circuit breaker, exponential backoff, jitter, timeout, fallback state, bulkhead, resilience, retry policy, microservice fault, network retry.
- Designing fetch decorators, handling API timeouts, writing retry functions, or isolating service calls.

## Routing boundary

- Primary for network fault management, retry systems, circuit-breaker patterns, timeout policies, and API client wrappers.
- Secondary to `system-architecture-rules` for high-level structure.

## Inputs required

- Target programming language and network library (e.g., Axios, fetch in TS, URLSession in Swift)
- Specific latency requirements and timeout limits
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing programming language and network libraries (e.g., TypeScript/Fetch/Axios, Swift/URLSession, Python/requests).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand timeouts, retries, jitters, and circuit breakers.
4. Set explicit request timeouts on all network clients to prevent resources from locking up.
5. Implement exponential backoff with random jitter for all retry operations.
6. Design circuit-breaker wrappers (Closed, Open, Half-Open states) around downstream services.
7. Outline clear fallback behaviors (serving stale cache, cached user configurations, or empty lists).

## Output format

- Primary decision/output: Resiliency logic wrapping network requests, retry helper implementations, and circuit-breaker config.
- Summary: One-paragraph overview of request resiliency and fault strategy.
- Actions: Verification checklist for timeout limits, jitter distribution, and circuit-breaker threshold safety.
