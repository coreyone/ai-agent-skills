https://github.com/OWASP/Top10
https://github.com/OWASP/Top10/tree/master/2021/docs/en

Where natural, use the tools provided: https://github.com/sbilly/awesome-security

## 1.1 Vibe Coding Security Fundamentals

Security is not a feature. It is a posture. These fundamentals anchor safe, AI-assisted development and reduce the most common failure modes of “vibe coding.”

### Never Hardcode Secrets
Do not embed API keys, tokens, passwords, or private URLs in source code.
- Use environment variables or a secrets manager.
- Scope secrets per environment (dev, staging, prod).

**AI prompt hint:** “Use environment variables for all secrets. Do not inline credentials.”

---

### Secure Every Endpoint by Default
All endpoints must assume hostile traffic.
- Enforce authentication and authorization on *every* route.
- Separate identity (who you are) from permissions (what you can do).

**AI prompt hint:** “Include auth middleware and role-based access checks.”

---

### Validate and Sanitize Inputs
Every external input is untrusted.
- Validate types, ranges, and formats.
- Sanitize to prevent SQL injection, XSS, and command injection.
- Prefer allowlists over blocklists.

**Review rule:** If AI-generated code touches user input, re-check it manually.

---

### Lock Down CORS
CORS is a security boundary, not a convenience flag.
- Allow only known origins.
- Never use wildcard `*` in production.
- Restrict methods and headers explicitly.

**Review rule:** Treat permissive CORS as a vulnerability.

---

### Enforce HTTPS Everywhere
Encrypt data in transit—always.
- Use HTTPS only.
- Redirect HTTP → HTTPS.
- Require modern TLS versions.

**Verification step:** Confirm HTTPS is enforced in server and proxy configs.

---

### Continuous Code Review
AI accelerates mistakes as fast as it accelerates output.
- Use automated scanners.
- Require human review for auth, data access, and infra code.

**AI review prompt:** “Identify security risks, auth gaps, and injection vectors.”

---

### Know Core Security Principles
Tools help. Fundamentals protect.
- Least privilege
- Separation of concerns
- Defense in depth

**Learning loop:** Regularly review secure coding guidance and threat models.

---

### Require Peer Review
Security improves with multiple eyes.
- Use pull requests.
- Encourage security-specific feedback.
- Normalize calling out risks early.

---

## 2.2 Application Security (AppSec): A Solid Foundation

AppSec means security exists at *every* stage of development—not as a final check.

### Least Privilege by Design
- Grant the minimum permissions required.
- Separate admin, service, and user roles.
- Rotate and expire credentials.

---

### Encrypt Sensitive Data
- Encrypt data in transit and at rest.
- Use modern, industry-standard algorithms.
- Manage keys centrally (never in code).

---

### CI/CD Security Scanning
- Scan dependencies and builds automatically.
- Fail builds on critical vulnerabilities.
- Include both static and dynamic testing.

---

### Regular Security Audits
- Schedule periodic reviews.
- Perform penetration testing for critical systems.
- Track findings to resolution.

---

### Remove Debug Artifacts
Debug logs leak information.
- Strip `console.log()` and debug output in production.
- Use structured logging with redaction.

---

### Safe Error Handling
Errors should inform developers—not attackers.
- Show generic messages to users.
- Log detailed errors securely on the server.

---

## 2.3 API Security: Protecting Your Endpoints

APIs are high-value targets. Treat them accordingly.

### Encrypt All API Traffic
- Require HTTPS.
- Enforce modern TLS versions.
- Reject plaintext requests.

---

### Strong Authentication and Authorization
- Use tokens or signed credentials.
- Implement expiration and rotation.
- Validate permissions on every request.

---

### Strict Input Validation
- Validate payloads at API boundaries.
- Reject malformed or unexpected input early.
- Avoid implicit type coercion.

---

### Rate Limiting and Throttling
- Protect against abuse and brute force.
- Set conservative defaults.
- Adjust based on observed traffic.

---

### Use an API Gateway
- Centralize auth, logging, and rate limits.
- Improve observability and control.
- Reduce duplicated security logic.

---

## 2.4 GitHub Security: Securing the Repo

Your repository is part of your attack surface.

### Enforce Strong Account Security
- Require two-factor authentication.
- Rotate personal access tokens regularly.

---

### Restrict Repository Access
- Keep sensitive projects private.
- Review collaborators periodically.
- Remove stale access immediately.

---

### Secure Dependencies and Secrets
- Enable dependency update alerts.
- Store secrets using encrypted repo settings.
- Never commit `.env` files or credentials.

---

### Audit Continuously
- Review access logs.
- Monitor dependency changes.
- Treat repo hygiene as production security.

---

## 2.5 Database Security: Protecting Your Data

Databases contain your highest-risk assets.

### Use Parameterized Queries
- Never construct queries via string concatenation.
- Validate inputs before execution.
- Prefer ORM or query builders with safeguards.

---

### Encrypt Data Everywhere
- Encrypt data at rest and in transit.
- Secure encryption keys separately.
- Encrypt backups as well.

---

### Enforce Least Privilege
- Grant read/write only where requi
