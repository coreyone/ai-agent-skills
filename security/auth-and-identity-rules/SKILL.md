---
name: auth-and-identity-rules
description: "Trigger: OAuth 2.1, JWT session, Secure cookies, Keychain storage, auth flow, user authentication. Scope: User authentication, session storage, authorization boundaries. Boundary: Excludes generic data caching."
---

# 🔑 Core Philosophy: Trust must be earned and constantly verified.

## When to use

Use this skill when designing sign-in flows, implementing role-based or attribute-based access control (RBAC/ABAC), securing API endpoints, managing JWT lifecycle, storing tokens, and integrating identity providers (IdPs) like Apple Sign-In or Passkeys.

## When not to use

Do not use this skill for basic visual layout of forms, telemetry logs, or general database schema indexing unrelated to security.

## Trigger cues

- Key terms: authentication, authorization, OAuth, OIDC, JWT, token, Keychain, HttpOnly, Passkey, WebAuthn, OAuth 2.1, PKCE, MFA, SAML, RBAC, session, secure storage.
- Implementing login, token decryption/signature verification, setting up middleware cookies, or handling authorization headers.

## Routing boundary

- Primary for security flows, authentication mechanics, credential storage, and authorization verification.
- Secondary to `developer-web-security` for broader transport and network defenses.

## Inputs required

- Selected identity system (e.g., OAuth 2.1 authorization server, Cognito, Firebase Auth)
- Security requirements (e.g., PCI-DSS, GDPR, platform guidelines)
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing identity and authentication tools (e.g., NextAuth, Passport, Auth0, Firebase Auth, Firebase Admin).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand first-principles identity and authorization security.
4. Standardize on OAuth 2.1 flows with PKCE enabled for all native and public clients within the project's framework.
5. Validate incoming JWTs cryptographically (verifying issuer, audience, and signature algorithm).
6. Store client-side credentials in secure sandboxes (iOS Keychain or HttpOnly/Secure/SameSite cookies).
7. Enforce Passkey support using WebAuthn APIs for high-security, passwordless entry.

## Output format

- Primary decision/output: Authentication flow diagrams, token storage design, and authorization policy code.
- Summary: One-paragraph overview of identity and token security.
- Actions: Verification checklist for threat modeling and secure credential management.
