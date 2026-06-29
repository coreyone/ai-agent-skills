---
description: rules for a developer in order to create simple, elegant, beautiful, scalable code.
---

# 🏗️ Core Philosophy: Build small, clear, composable pieces.

Focus on maintainability and substitutability. Minimize complexity everywhere. Don’t build speculative features. Prioritize readability and explicitness over magic. Value adaptability and working software over rigid process. Model software around end-user requirements. Maintain clear dependency direction and independent layers. Isolate core logic from infrastructure. Build responsive, resilient, elastic, message-driven systems. Target fewer interfaces and fewer failures.

---

### 📜 The 17 Rules of the Developer Philosophy

1.  **Rule of Modularity**: Write simple parts connected by clean interfaces.
2.  **Rule of Clarity**: Clarity is better than cleverness.
3.  **Rule of Composition**: Design programs to be connected to other programs.
4.  **Rule of Separation**: Separate policy from mechanism; separate interfaces from engines.
5.  **Rule of Simplicity**: Design for simplicity; add complexity only where you must.
6.  **Rule of Parsimony**: Write a big program only when it is clear by demonstration that nothing else will do.
7.  **Rule of Transparency**: Design for visibility to make inspection and debugging easier.
8.  **Rule of Robustness**: Robustness is the child of transparency and simplicity.
9.  **Rule of Representation**: Fold knowledge into data so program logic can be stupid and robust.
10. **Rule of Least Surprise**: In interface design, always do the least surprising thing.
11. **Rule of Silence**: When a program has nothing surprising to say, it should say nothing.
12. **Rule of Repair**: When you must fail, fail noisily and as soon as possible.
13. **Rule of Economy**: Programmer time is expensive; conserve it in preference to machine time.
14. **Rule of Generation**: Avoid hand-hacking; write programs to write programs when you can.
15. **Rule of Optimization**: Prototype before polishing. Get it working before you optimize it.
16. **Rule of Diversity**: Distrust all claims for "one true way".
17. **Rule of Extensibility**: Design for the future, because it will be here sooner than you think.

---

### 🛠️ Strategic Development Principles

#### 🧩 Modularity & Composition
*   **Focused Responsibility**: Each module/class/function should do one thing well.
*   **Loose Coupling**: Minimize dependencies between modules to allow for easier replacement and testing.
*   **Clean Interfaces**: Define clear, stable boundaries between components.

#### 📖 Clarity & Readability
*   **Explicitness over Magic**: Avoid hidden behaviors or "clever" shortcuts that obscure intent.
*   **Naming is Documentation**: Use descriptive, consistent names for all entities.
*   **Minimalist Logic**: Prefer simple `if/else` or data-driven logic over complex abstractions.

#### 🛡️ Robustness & Simplicity
*   **Fail Fast & Noisily**: Catch errors at the source and provide clear context.
*   **Data over Logic**: Store configuration and rules in data structures rather than nesting them in code.
*   **No Speculative Engineering**: Build only what is needed today; let future requirements drive future complexity.

#### ⚡ Architecture & Infrastructure
*   **Independent Layers**: Isolate business logic from UI, databases, and external services.
*   **Message-Driven**: Design for asynchronous, decoupled communication where appropriate.
*   **Fewer Moving Parts**: Every interface is a potential point of failure; consolidate where it adds clarity.


### 🕰️ TIME ZONE HANDLING — ENGINEERING GUIDELINES
Audience: Junior developers
Authorial intent: Senior engineer / system architect perspective

#### CORE PRINCIPLE
Time zones are a presentation concern. Store and compute time in a single canonical form.

#### NON-NEGOTIABLE RULES
1. **Always store time in UTC**
   - Use ISO-8601 with timezone (`YYYY-MM-DDTHH:mm:ssZ`) or epoch milliseconds.
   - Never store local time in a database.
   - Never store ambiguous timestamps (e.g., without offset).

2. **Convert at the edges**
   - Convert to local time only:
     - At the UI layer
     - At API boundaries when explicitly required
   - Business logic operates exclusively on UTC.

3. **Time ≠ Date**
   - Distinguish clearly between:
     - *Instant* (a point in time, e.g., `2026-01-17T18:30:00Z`)
     - *Local date* (e.g., “Jan 17 in Tokyo”)
   - Never infer one from the other without an explicit timezone.

4. **Time zones are rules, not offsets**
   - Use IANA time zone IDs (`America/Los_Angeles`, not `-0800`)
   - Offsets change due to DST; zone rules do not.

5. **Daylight Saving Time will break naïve logic**
   - Assume:
     - Days can be 23 or 25 hours
     - Some local times never exist
     - Some local times occur twice
   - Do not “add 24 hours” to mean “tomorrow”.

LIBRARY USAGE
6. **Use a proven time library**
   - JavaScript: `Temporal` (preferred), `luxon`
   - Python: `zoneinfo`, `datetime` with tz-aware objects
   - Java: `java.time`
   - Never roll your own time logic.

7. **Enforce timezone-aware types**
   - Disallow naïve datetime objects in code review.
   - Fail fast if timezone info is missing.

API DESIGN
8. **APIs must be explicit**
   - All timestamps include timezone or are explicitly UTC.
   - If accepting local time, require:
     - The timestamp
     - The IANA timezone
   - Example:
     - ❌ `start=2026-01-17T09:00`
     - ✅ `start=2026-01-17T09:00&tz=America/New_York`

SCHEDULING & CRON
9. **Scheduling is harder than it looks**
   - Store schedules as:
     - Rule + timezone (e.g., “Every day at 9am America/New_York”)
     - Not precomputed UTC timestamps
   - Recompute next run time dynamically.

TESTING
10. **Test across time zones**
    - Include:
      - DST transitions
      - Non-DST zones (UTC, Asia/Tokyo)
      - Southern hemi



ANTI-FRAGILE CODING PHILOSOPHY (for a junior dev)
Goal: build software that gets better under stress (bugs, traffic spikes, bad inputs, partial outages).

Mental model
- Fragile: breaks when surprised.
- Robust: survives surprises.
- Anti-fragile: learns from surprises and becomes harder to break next time.

Core principles (apply everywhere)
1) Assume failure is normal
   - Networks fail, disks fill, APIs change, users do weird things.
   - Design for “when,” not “if.”

2) Fail small, not big
   - Prefer localized errors over whole-system crashes.
   - Contain blast radius with boundaries (modules, services, queues).

3) Make the system observable
   - If you can’t see it, you can’t improve it.
   - Logs (what happened), metrics (how often), traces (where it went), alerts (when it’s bad).

4) Turn incidents into upgrades
   - Every outage/bug produces: a fix, a test, and a monitor.
   - “Never again” means automated proof, not memory.

5) Prefer simple defaults; add complexity only when it pays rent
   - The best failure mode is the one that can’t happen because the design is simpler.

6) Defensive at the edges, strict in the core
   - Accept messy inputs at boundaries.
   - Convert to clean, validated types early.
   - Inside the system, assume validated data and enforce invariants.

7) Build for safe change
   - Small deploys, reversible releases, feature flags, migrations you can roll forward/back.
   - Continuous integration and reliable tests.

--------------------------------------------------------------------

FRONT-END (anti-fragile UI)
Objective: UI degrades gracefully and reports issues clearly.

A) Treat the network as unreliable
   - Always handle: loading, empty, error, retry, offline-ish.
   - Use timeouts, cancellation (AbortController), and idempotent retries for GETs.

B) Don’t crash the page
   - Use error boundaries (React) or equivalent.
   - Show a friendly fallback and log the error with context.

C) Make state resilient
   - Keep UI state predictable (single source of truth).
   - Avoid “hidden” state in multiple places.
   - Persist only what you must (and version it).

D) Validate user input early
   - Front-end validation for UX.
   - Never rely on it for security (backend must validate too).

E) Performance anti-fragility
   - Guard against slow devices/networks:
     - code-splitting, lazy loading, caching, skeleton screens.
   - Monitor web vitals and error rates per release.

--------------------------------------------------------------------

API / BACK-END (anti-fragile services)
Objective: services stay up, respond predictably, and protect downstream dependencies.

A) Validate at the boundary
   - Validate request shape, types, and constraints (schema validation).
   - Reject bad inputs with clear errors (400s), not internal exceptions (500s).

B) Make operations idempotent
   - If the same request is sent twice, results are safe.
   - Use idempotency keys for payments/creates.

C) Timeouts and backpressure
   - Always set timeouts on outbound calls (DB, HTTP, queues).
   - Apply rate limits, request size limits, and concurrency caps.
   - Prefer “busy, try later” (429/503) over “dead.”

D) Circuit breakers + retries (carefully)
   - Retry only when it’s safe (idempotent ops).
   - Use exponential backoff + jitter.
   - Trip circuit breakers when dependencies misbehave.

E) Consistent error contracts
   - Return stable error codes/messages clients can handle.
   - Don’t leak internals; log details server-side.

F) Gradual, reversible releases
   - Feature flags for risky changes.
   - Canary deploys, blue/green when possible.

--------------------------------------------------------------------

DATA LAYER (anti-fragile storage)
Objective: data stays correct; migrations don’t take the system down.

A) Data correctness first
   - Define invariants (unique keys, foreign keys, constraints).
   - Prefer constraints in the database, not just in code.

B) Backups + restore drills
   - A backup you haven’t restored is “hope,” not protection.
   - Periodically test restore in a non-prod environment.

C) Safe migrations
   - Use expand/contract:
     1) Add new columns/tables (backward compatible)
     2) Dual-write or backfill
     3) Switch reads
     4) Remove old fields later
   - Avoid long locks; batch backfills.

D) Handle partial failure
   - Transactions where needed.
   - Outbox pattern / queues for cross-service consistency.

--------------------------------------------------------------------

INFRA / OPS (anti-fragile delivery)
Objective: deployment and runtime tolerate failures and recover quickly.

A) Automate repeatable tasks
   - Infra as code, build pipelines, one-command deploy.
   - Manual steps are where incidents breed.

B) Health checks + autoscaling (where applicable)
   - Liveness/readiness checks.
   - Separate “can respond” from “can do work.”

C) Runbooks and playbooks
   - For common failures: “What to check, how to mitigate, who to page.”
   - Keep them short and tested.

D) Security as resilience
   - Least privilege, secret rotation, dependency scanning.
   - A breach is the worst kind of outage.


--------------------------------------------------------------------

MODERN COMMON SENSE (Stack-Agnostic First Principles)
Objective: Write code that outlasts the framework hype cycle.

A) The Platform IS The Framework
   - Learn the Web Standards (`Request`, `Response`, `URL`, `FormData`) before the framework wrappers.
   - If you know the platform, you can switch frameworks in a weekend. If you only know the framework, you are obsolete in 2 years.
   - Prefer standard attributes and semantic HTML over custom implementations.

B) Colocation > Abstraction
   - Keep things where they are used.
   - Don't create a "utils" folder for a function used once. Defining a helper function *inside* the component that uses it is often cleaner than importing it from 5 folders away.
   - "Don't Repeat Yourself" (DRY) is often "Do Repeat Yourself" (DRY) when the repetition is incidental and strictly decoupled.

C) Local-First Mindset
   - If the network cable is unplugged, does the app immediately break, or does it show cached data?
   - Build as if the server is a nice-to-have synchronization mechanism, not the brain.
   - Optimistic UI is not a feature; it's a requirement. The user shouldn't wait for a server roundtrip to see a button click register.

D) "Boring" Code is Best
   - AI writes code; humans read it.
   - Complex generics, recursive types, and "clever" one-liners confuse LLMs and humans alike.
   - Write code that is trivial to parse. Simplicity is the ultimate sophistication.



CODING HABITS (daily behaviors)
- Handle the “unhappy path” first: what if this is null, slow, duplicate, unauthorized?
- Make logs useful:
  - include request id, user id (if safe), endpoint, error code, duration.
- Prefer explicitness:
  - clear names, small functions, typed boundaries, minimal magic.
- Keep changes small:
  - easier review, easier rollback, fewer hidden interactions.

--------------------------------------------------------------------

CHECKLIST (before you ship)
[ ] Inputs validated at the boundary (front + back)
[ ] Clear error handling (user-friendly UI, stable API errors)
[ ] Timeouts set on outbound calls
[ ] Retries are safe + bounded
[ ] Monitoring exists for the new path (errors, latency, throughput)
[ ] A regression test covers the main bug-risk
[ ] Release can be rolled back or disabled (flag/canary)
[ ] Data changes are backward compatible

One-line takeaway
Anti-fragile code treats real-world chaos as a feedback loop: detect → contain → learn → harden.
