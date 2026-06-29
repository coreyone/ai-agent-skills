# 📈 Analytics and Event Tracking Guidelines

> "If you can’t measure it, you can’t improve it." — Peter Drucker
> "The only way to build a great product is to understand how users interact with it, in high fidelity." — Alistair Croll & Benjamin Yoskovitz (Lean Analytics)

---

## 📜 Core Philosophy
Product telemetry is the compass of engineering and product design. A great behavioral tracking system is organized around a unified, predictable taxonomy, maintains clean identity resolution, is decoupled from UI render loops, and respects user privacy constraints. We design events around user actions rather than server mechanisms, and rely on structured properties to convey details instead of polluting the event namespace.

---

## 🏛️ Foundational Tracking Taxonomy

### 1. The Object-Action Syntax
Standardize all event names using the `object:action` format (or similar unified conventions). This guarantees that analysts and systems can filter events systematically.
*   *Good Event Names*:
    *   `sign_up:completed`
    *   `product:added_to_cart`
    *   `checkout:step_started`
*   *Bad Event Names* (unstructured, raw, or inconsistent):
    *   `UserClickedRegister`
    *   `addToCart`
    *   `Step 2 Started`

### 2. Event Consolidation vs. Property Pollution
*   **Rule of Parsimony**: Do not create unique events for minor variations in execution. Consolidate events and push variations into the **Properties Payload**.
    *   *Anti-pattern*: Creating `click_blue_signup_button` and `click_red_signup_button`.
    *   *Correct approach*: Create a single event named `cta:clicked` and include properties detailing the context:
        ```json
        {
          "cta_type": "sign_up",
          "placement": "hero_banner",
          "button_color": "blue",
          "current_url": "https://example.com/pricing"
        }
        ```

---

## 👤 Identity Resolution & User Lifecycle

To maintain accurate conversion metrics across anonymous and authenticated states, enforce the standard two-step identity mapping:

1.  **Anonymous State**: On initial load, generate a cryptographically random UUID and store it in local cookies/storage (e.g., `anonymous_id`). Attach this `anonymous_id` to all page views and event tracking payloads.
2.  **Authentication Handshake**: When the user signs in or registers, execute an `identify` or `alias` call linking the `anonymous_id` to the secure backend `user_id`.
3.  **Authenticated State**: From that point forward, all tracking events must be bound to the canonical `user_id`. The analytics engine will merge the behavioral streams, preserving marketing attribution and funnels.

---

## 🛡️ Privacy by Design (PII Hardening)
Behavioral tracking must never capture Personal Identifiable Information (PII).
*   **Non-Negotiable Rules**:
    *   Strip out: raw email addresses, physical addresses, credit card numbers, passwords, phone numbers, and full names from event properties.
    *   If email is needed for matching (e.g., in integrations), hash it using SHA-256 before transmission.
    *   Intercept outbound payloads via middleware to filter variables matching standard patterns (like emails or credit cards).

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: PostHog, Segment, Mixpanel)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing tracking tools (e.g., Segment, Mixpanel, Amplitude, Google Analytics) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to PostHog or custom local trackers unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Asynchronous Client Instrumentation (e.g., PostHog Web SDK)
*   **Principle**: *Load tracking SDKs asynchronously to avoid blocking critical rendering path operations.*
*   *Application*: Initialize SDK scripts using defer/async attributes. Queue track calls locally in memory until the network library has fully loaded and handshakes are established.

### 2. Autocapture vs. Precision Tracking
*   **Principle**: *Rely on explicit event tracking for core funnels, and use autocapture only for exploratory analysis.*
*   *Application*: While tools like PostHog support autocapture (log all clicks/pageviews), critical conversion milestones (e.g., checkout completes, invoice paid) must be instrumented explicitly in code with structured schemas to ensure they do not break when CSS selectors or layouts change.

### 3. Server-Side Telemetry (e.g., PostHog Node/Bun SDK)
*   **Principle**: *Track high-value business mutations on the server to prevent ad-blocker dropouts.*
*   *Application*: For events that define revenue or user creation, capture the event inside the SvelteKit or Hono server handler *after* the database transaction succeeds. This guarantees 100% data integrity even if the client browser runs strict content blockers.
