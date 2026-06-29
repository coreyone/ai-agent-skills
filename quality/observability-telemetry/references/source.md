# 📊 Observability and Telemetry Rules

> "Monitoring is for when you know what questions you will want to ask. Observability is for when you don't." — Charity Majors

---

## 📜 Core Philosophy
Observability is the ability to understand the internal state of a system based entirely on its external outputs (telemetry). We reject unstructured string logging and low-cardinality metrics in favor of rich, high-cardinality structured events and distributed trace contexts. We define reliability through user-centric Service Level Objectives (SLOs) and manage operations via error budget burn rates.

---

## 📐 Observability vs. Monitoring

| Concept | Monitoring (Metrics) | Observability (Structured Events) |
| :--- | :--- | :--- |
| **Philosophy** | "Tell me when CPU > 80% or requests drop." | "Help me understand why a specific user is experiencing latency." |
| **Data Format** | Aggregated integers, low cardinality. | Wide JSON events, high cardinality (UUIDs, queries). |
| **Debugging** | Stare at pre-built dashboards; guess anomalies. | Ad-hoc query slicing across arbitrary tags. |
| **Fatigue** | High pager fatigue (alerting on symptoms/thresholds). | Low fatigue (alerting only on SLO budget depletion). |

---

## ⚡ Non-Negotiable Telemetry Rules

### 1. High-Cardinality Structured Events
*   **No Unstructured Logs**: Never write raw strings (e.g., `log.info("Order processed for user " + userId)`). Write structured JSON events:
    ```json
    {
      "event": "order_processed",
      "user_id": "usr_9f1a23",
      "order_id": "ord_8812739",
      "duration_ms": 142.5,
      "db_queries_count": 4,
      "http_status": 201,
      "app_version": "v1.4.2"
    }
    ```
*   **Include Arbitrary Context**: Inject high-cardinality keys (`user_id`, `ip_address`, `cart_id`, `request_id`) into every event span. Modern observability backends (e.g., Honeycomb, Datadog) are built to index millions of unique values instantly.

### 2. Distributed Tracing & W3C Trace Context
*   **Trace Propagation**: APIs and clients must propagate distributed tracing headers across network boundaries.
*   **Use W3C Standards**: Always parse and inject the standard `traceparent` header:
    *   Format: `version-trace_id-parent_id-trace_flags` (e.g., `00-4bf92f3577b34da6a3ce929d0e0e4736-00f067aa0ba902b7-01`).
*   **Unified Client-Server Spans**: Front-end requests (Web fetch or iOS `URLSession`) must start a span and forward the `traceparent` header to the backend so the entire request lifecycle is linked in a single trace diagram.

---

## 📉 Service Level Objectives (SLOs) & Alerting
1.  **Define SLIs from the User's Perspective**:
    *   *Good SLI*: The percentage of successful API payments that process in under 2 seconds.
    *   *Bad SLI*: The average CPU utilization of the database container.
2.  **Establish the SLO**: Set a target (e.g., 99.9% success rate over a 30-day window).
3.  **Manage the Error Budget**: The allowable failure (0.1%).
    *   *Burn Rate Alerting*: Alert engineers only if the speed of error budget consumption (burn rate) indicates the budget will be exhausted soon (e.g., consuming 2% of the budget in 1 hour). Do not alert on transient spikes.

---

## 📱 iOS Native Instrumentation (OSLog & Signpost)
*   **Use Unified Logging**: Replace raw `print()` statements with the Swift `os.Logger` framework.
*   **Leverage OSSignpost**: Instrument critical UI transitions, data fetches, and app launch phases using `OSSignpost`. This enables deep profile debugging using Xcode Instruments.
*   **Respect Privacy**: Use dynamic string interpolation private tags (e.g., `Logger().info("User \(userId, privacy: .private) logged in")`) to prevent logging personally identifiable information (PII) to system consoles.

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: PostHog, SvelteKit Error Handlers, Bun Console Logs)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing telemetry and logging stack (e.g., Datadog, Sentry, Mixpanel, Winston, Bunyan) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to PostHog, Umami, or custom SvelteKit handlers unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Decoupled High-Cardinality Product Analytics (e.g., PostHog, Umami)
*   **Principle**: *Capture rich user interaction flows using asynchronous tracking libraries that do not block the UI execution thread.*
*   *Application*: Initialize analytical clients asynchronously (e.g., PostHog or Umami web snippets). Inject context-rich tags (`user_id`, `$current_url`, experimental variant groups) into all custom actions without degrading performance.

### 2. Framework-Level Global Error Handlers (e.g., SvelteKit handleError)
*   **Principle**: *Intercept unhandled exceptions at the edge boundaries of both server and client to trace stack contexts while sanitizing client-facing messages.*
*   *Application*: In SvelteKit, implement `handleError` inside `hooks.server.ts` and `hooks.client.ts`. Server-side, log full trace details to stdout. Client-side, pipe sanitized stack alerts to telemetry collectors while rendering user-friendly generic notices (such as RFC 7807 error refs) to avoid leaking system internals.

### 3. Structured Logging Streams (e.g., Bun Console Log stdout)
*   **Principle**: *Avoid writing logs directly to local file storage within the application process; stream structured JSON to stdout.*
*   *Application*: On high-speed runtimes like Bun, emit events to `stdout` utilizing JSON structures, allowing runtime platforms (Netlify, Docker, Kubernetes) to capture and forward telemetry streams asynchronously.
