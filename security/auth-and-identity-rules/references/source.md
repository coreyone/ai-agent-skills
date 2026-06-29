# 🔑 Auth and Identity Rules

> "Securing an application is not about building walls; it’s about establishing trusted boundaries." — Vittorio Bertocci

---

## 📜 Core Philosophy
Identity is the cornerstone of system trust. A secure auth system operates on the principle of **Zero Trust** (never trust, always verify). We treat authentication (who you are) and authorization (what you can do) as separate domains, enforce modern cryptographic standards (OAuth 2.1, OIDC, WebAuthn), and mandate secure, sandboxed storage for credentials.

---

## 🔐 OAuth 2.1 & OpenID Connect Standards
*   **No Implicit Grant**: The OAuth 2.0 Implicit Flow is deprecated due to token leakage risks in URL parameters.
*   **Authorization Code with PKCE**: Every public client (Single Page App, mobile app) and confidential client (backend server) must use the **Authorization Code Flow with PKCE** (Proof Key for Code Exchange).
    *   *Mechanism*: Client generates a cryptographically random `code_verifier`, hashes it to create a `code_challenge`, sends the challenge in the authorize request, and verifies it by sending the raw verifier during the token request.
*   **OIDC (OpenID Connect)**: Use OIDC for authentication. The Identity Token (`id_token`) is a JWT meant for the client UI containing user profile claims. The Access Token (`access_token`) is meant for the Resource Server (API) and should be opaque to the client.

---

## 📦 Client-Side Secure Storage

### 1. iOS (Keychain Services)
*   **Use the Keychain**: Never store access tokens, refresh tokens, or passwords in `UserDefaults` or local file directories.
*   **Strict Access Control**: Set the accessibility attribute carefully:
    *   Use `kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly` for background syncing.
    *   Use `kSecAttrAccessibleWhenUnlockedThisDeviceOnly` for highly sensitive user-initiated flows.
    *   Setting `kSecAttrSynchronizable = false` ensures credentials never leave the device unless explicitly desired.

### 2. Web (XSS & CSRF Defenses)
*   **Do Not Use LocalStorage**: Storing tokens in `localStorage` makes them accessible to any JavaScript running on the page, leaving them vulnerable to Cross-Site Scripting (XSS) leaks.
*   **Secure Cookies / BFF Pattern**:
    *   **Backend-for-Frontend (BFF)**: Web apps should use a lightweight server proxy that handles OAuth flows. It stores tokens in a server-side session and issues a cryptographically signed cookie to the browser.
    *   **Cookie Attributes**: Cookies must include:
        *   `HttpOnly`: Prevents client-side JS from reading the cookie (neutralizes XSS extraction).
        *   `Secure`: Ensures the cookie is only transmitted over HTTPS.
        *   `SameSite=Strict` or `SameSite=Lax`: Defends against Cross-Site Request Forgery (CSRF).

---

## 🛡️ JWT Verification Best Practices

When verifying JSON Web Tokens (JWT) at the API Gateway or Resource Server:
1.  **Block `alg: none`**: Explicitly reject tokens with the `alg` header set to `none`.
2.  **Verify the Signature**: Use the public keys exposed via the Identity Provider's JSON Web Key Set (JWKS) endpoint. Cache these keys in memory to minimize latency, but respect HTTP cache headers.
3.  **Assert Standard Claims**:
    *   `iss` (Issuer): Must match the expected identity provider URL.
    *   `aud` (Audience): Must match the client identifier or API resource name.
    *   `exp` (Expiration Time): Must be in the future. Validate with a small clock-skew tolerance (maximum 1-2 minutes).
    *   `nbf` (Not Before): Must be in the past.

---

## 🔑 Passkeys & WebAuthn
*   **Passwordless Future**: Support phishing-resistant **Passkeys** using the WebAuthn standard.
*   **Public Key Cryptography**: The server stores only the public key. Authentication is completed when the device cryptographically signs a server-generated challenge using the matching private key locked behind the user's biometrics (Face ID/Touch ID or Windows Hello).

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: Better Auth, SvelteKit Hooks, Secure Session Cookies)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing identity stack (e.g., Auth0, Firebase Auth, NextAuth, Clerk) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to Better Auth or custom SvelteKit cookie handlers unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Unified Authentication Abstraction (e.g., Better Auth)
*   **Principle**: *Rely on battle-tested, standards-compliant authentication libraries instead of implementing custom crypto or session management.*
*   *Application*: Standardize on tools like Better Auth to handle session state, multi-factor setups, and passwordless authentication securely.

### 2. Middleware Session Propagation (e.g., SvelteKit Server Hooks)
*   **Principle**: *Intercede, resolve, and inject user sessions at the server ingress hook to propagate identity downstream.*
*   *Application*: Use SvelteKit Server Hooks (`hooks.server.ts`) to validate incoming session cookies on every request and populate the context (`event.locals.user`), making session data instantly available to downstream routing handlers without redundant DB queries.

### 3. Secure Transport Cookie Attributes (e.g., Better Auth Cookie Options)
*   **Principle**: *Lock down session cookies at the browser storage level to prevent XSS-based exfiltration and CSRF cross-origin leakage.*
*   *Application*: Verify that cookies are configured with `httpOnly: true`, `secure: true`, and `sameSite: "Lax"` or `"Strict"`. Limit local development to HTTP localhost interfaces only.
