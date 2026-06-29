---
name: observability-telemetry
description: Use when designing structured logging, application telemetry, distributed tracing, metrics, SLIs/SLOs, and user tracking behavior.
---

# 📊 Core Philosophy: You cannot optimize or debug what you do not measure.

## When to use

Use this skill when instrumenting server code, configuring OpenTelemetry, designing structured JSON logs, tracing across network requests (W3C trace context), defining performance metrics, and setting up SLO targets.

## When not to use

Do not use this skill for database index tuning, auth configuration, or layout adjustments.

## Trigger cues

- Key terms: observability, telemetry, logging, tracing, metrics, Sentry, OpenTelemetry, Honeycomb, Datadog, SLI, SLO, OSLog, Signpost, W3C tracecontext, high-cardinality, structured events.
- Creating logging frameworks, tracing network calls, setting up dashboards, defining SLO parameters, instrumenting performance code.

## Routing boundary

- Primary for logging design, tracing propagation, alerting definitions, metrics aggregation, and instrumentation.
- Secondary to `developer-web-performance` for core optimization tasks.

## Inputs required

- Target analytics/observability platform (e.g., Sentry, Honeycomb, Apple Instruments)
- System SLO targets and alerting criteria
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing telemetry and monitoring tools (e.g., Datadog, Sentry, Mixpanel, Winston, Bunyan, OpenTelemetry).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand structured events and telemetry.
4. Design high-cardinality structured events instead of flat text logs using the project's logging libraries.
5. Propagate tracing contexts (W3C standards) across all network requests.
6. Define system Service Level Objectives (SLOs) focused on user-facing symptoms.
7. In iOS apps, implement native OSLog and OSSignpost instrumentation.

## Output format

- Primary decision/output: Logging schema, OpenTelemetry setup code, and SLO configuration.
- Summary: One-paragraph overview of observability and alerting strategy.
- Actions: Verification checklist for log cardinality, trace coverage, and symptom-based alerting.
