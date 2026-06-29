---
name: api-design-guidelines
description: "Trigger: REST API, GraphQL schemas, HTTP methods, RFC 7807, endpoint structure, API contracts. Scope: API schema design, error models, request/response structures. Boundary: Excludes client-side visual layouts."
---

# 🔌 Core Philosophy: APIs are contracts; once published, they are hard to break.

## When to use

Use this skill when designing web endpoints, data exchange schemas, error structures, rate-limiting frameworks, pagination, and SDK interfaces.

## When not to use

Do not use this skill for frontend state management, local storage layout, or layout styling.

## Trigger cues

- Key terms: REST, RESTful, API, OpenAPI, Swagger, GraphQL, gRPC, tRPC, endpoint, schema, request/response, versioning, URL structure, HTTP status, JSON API, payload.
- Designing API specs, designing microservices interaction, defining payload models.

## Routing boundary

- Primary for network protocol schemas, RESTful constraints, serialization definitions, and API evolutionary practices.
- Secondary to `developer-web-security` for authentication protocols.

## Inputs required

- Target protocol requirements (REST, GraphQL, gRPC, etc.)
- Scalability requirements and pagination targets
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing technology stack (e.g., Next.js, FastAPI, Express, Django).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand contract-first API design.
4. Draft API endpoints using OpenAPI (REST) or schema definitions (GraphQL) matching the project's tooling.
5. Standardize error formats using RFC 7807 problem details.
6. Define clear query filters, sorting, and cursor-based pagination parameters.

## Output format

- Primary decision/output: API Endpoint specifications, JSON schema definition, and versioning rules.
- Summary: One-paragraph API design overview.
- Actions: Verification checklist for HTTP compatibility, error robustness, and pagination standards.
