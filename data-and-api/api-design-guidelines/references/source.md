# 🔌 API Design Guidelines

> "An API is a contract. Once you publish it, you are committed to it. Treat it as a permanent API." — Joshua Bloch

---

## 📜 Core Philosophy
APIs are the communication fabric of modern systems. A great API is self-descriptive, highly secure, easy to consume, and designed to evolve without breaking consumers. We design APIs using contract-first methodologies, leverage appropriate architectural patterns (REST, GraphQL, gRPC), and follow strict rules for backward compatibility.

---

## 🔗 The Richardson Maturity Model (REST)
We target Level 3 maturity where practical, but mandate Level 2 at a minimum:
1.  **Level 0 (The Swamp of POX)**: Single URI, HTTP POST for all operations (e.g., SOAP or basic XML/JSON-RPC).
2.  **Level 1 (Resources)**: Multiple URIs, mapping to distinct business entities (e.g., `/users`, `/orders/123`), but still using a single HTTP method.
3.  **Level 2 (HTTP Verbs)**: Correct usage of HTTP verbs (GET, POST, PUT, PATCH, DELETE) and HTTP status codes (200, 201, 400, 401, 403, 404, 409, 500).
4.  **Level 3 (Hypermedia Controls)**: HATEOAS (Hypermedia As The Engine Of Application State) - response payloads contain links explaining what actions can be taken next. *Pragmatic usage*: Include links for complex state machine transitions (e.g., order payment, cancellation).

---

## 🛠️ Tactical REST Rules & Conventions

### 1. Resource Naming (URIs)
*   **Use plural nouns**: Prefer `/orders` or `/users` over `/order` or `/user`.
*   **Hierarchy for relationships**: Use nested URIs for dependent child entities (e.g., `/users/123/addresses/456`). Limit nesting to two levels deep (e.g., `/users/123/addresses`).
*   **Kebab-case**: Use lowercase with hyphens for multi-word paths (e.g., `/payment-methods`).

### 2. HTTP Method Semantics
*   `GET`: Read-only, safe, and idempotent. Must never mutate server state.
*   `POST`: Create resource. Non-idempotent. Returns `201 Created` with a `Location` header pointing to the new resource.
*   `PUT`: Replace resource completely. Idempotent.
*   `PATCH`: Partial update to a resource. Non-idempotent (unless carefully designed).
*   `DELETE`: Remove resource. Idempotent (subsequent deletes return same success state or 404/204).

### 3. Versioning Strategy
*   **Path-based**: Put version in the URL path (e.g., `/api/v1/users`) for high visibility and simple proxy routing.
*   **Header-based**: Use custom headers or media-type content negotiation (e.g., `Accept: application/vnd.company.v1+json`) when URLs must remain resource-pure.
*   *Rule*: Never change API behavior without incrementing the version unless it is a purely additive, backward-compatible change.

### 4. Idempotency & Reliability
*   **Idempotency Keys**: For non-idempotent endpoints like POST, support the `Idempotency-Key` header.
    *   *Implementation*: Store the key (UUID) along with the response payload in Redis for 24 hours. If a request with the same key is received again, return the cached response immediately without executing the operation again.

---

## 🚨 Robust Error Handling (RFC 7807)
Standardize HTTP error responses using the **RFC 7807 (Problem Details)** format:
```json
{
  "type": "https://api.example.com/errors/insufficient-funds",
  "title": "Insufficient Funds",
  "status": 400,
  "detail": "Your current balance is $12.50, but the checkout total is $45.00.",
  "instance": "/orders/abc-123/payment",
  "invalid_params": [
    {
      "name": "payment_source",
      "reason": "Card ending in 4242 was declined."
    }
  ]
}
```
*   *Rule*: Never expose internal stack traces or database errors in public API payloads.

---

## ⚡ Non-Negotiable Performance & Scaling Rules

1.  **Pagination Standard**:
    *   **Cursor-Based**: Mandatory for infinite scroll / high-frequency data (e.g., social feeds, event logs). Use query parameters `after` (opaque base64 cursor) and `limit`.
    *   **Offset-Based**: Allow for static, small datasets only. Use `offset` and `limit`.
2.  **Rate-Limiting Response Headers**:
    *   Expose standard RFC-like headers on all authenticated API responses:
        *   `X-RateLimit-Limit`: Maximum requests allowed in the period.
        *   `X-RateLimit-Remaining`: Requests left in the current window.
        *   `X-RateLimit-Reset`: Epoch timestamp when the limit resets.
    *   Return `429 Too Many Requests` with a `Retry-After` header when limit is exceeded.
3.  **Strict Backward Compatibility (Postel's Law)**:
    *   *Rule*: Be conservative in what you send, liberal in what you accept.
    *   *Web/iOS client rule*: Clients must ignore unknown properties in API responses to allow the server to add new fields safely.

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: SvelteKit, Hono, tRPC, ts-rest, Zod)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing stack (e.g., Next.js, Express, FastAPI, NestJS) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to SvelteKit, Hono, tRPC, ts-rest, or Zod unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Framework-Integrated Server Routing (e.g., SvelteKit Server Endpoints)
*   **Principle**: *Co-locate API routers alongside application page loads for fast internal communication.*
*   *Application*: Rely on SvelteKit's native routing (`+server.ts`) and JSON serialization helpers (`import { json } from '@sveltejs/kit'`) to handle quick RESTful endpoints cleanly.

### 2. Edge-Optimized Lightweight Frameworks (e.g., Hono)
*   **Principle**: *Isolate public or decoupled microservices into ultra-lightweight, standard-based Edge runtimes.*
*   *Application*: Use minimal routers like Hono to minimize memory footprint and cold-start latency in serverless environments, leveraging standard Web APIs (`Request`/`Response`).

### 3. Type-Safe API Contracts (e.g., tRPC, ts-rest)
*   **Principle**: *Define shared client-server contracts to enforce compile-time network type safety and catch breaking payload drift.*
*   *Application*: Use tRPC or ts-rest to build shared schema definitions that are imported by both client and server code, bypassing runtime parsing bugs.

### 4. Input-Boundary Schema Validation (e.g., Zod, Valibot)
*   **Principle**: *Enforce strict request sanitization immediately at the entry point boundary before executing business logic.*
*   *Application*: Parse all incoming query parameters and request bodies using validation schemas (like Zod) and return detailed, formatted `400 Bad Request` responses on failure.
