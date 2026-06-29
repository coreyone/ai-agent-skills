---
description: Philosophy, rules, and tactics for hardening web applications against bots and malicious actors. Inspired by CrowdSec's collaborative defense approach.
---

# 🛡️ Web Security Hardening: Bot Defense & Attack Mitigation

*Your application is under attack the moment it goes live. Modern threats are automated, distributed, and intelligent. Defense must be layered, behavioral, and collaborative.*

---

## 🎯 The Prime Directive
**"Defense in depth means no single layer is trusted to stop all threats."**
Bots evolve. Attackers adapt. Your defenses must be multi-layered, behavioral, and continuously learning.

> "The attacker only needs to be right once. Defenders need to be right every time." — *Security Axiom*

---

## 🧠 The CrowdSec Philosophy

### 1. Detect Here, Remedy There
Separate detection from remediation.
- Log analysis happens centrally.
- Blocking can occur at multiple layers (CDN, WAF, application, firewall).
- This decoupling enables flexible, proportional responses.

**Implementation:** Use edge protection (Cloudflare, Vercel Edge) for fast blocking, application middleware for fine-grained control.

---

### 2. Behavioral Detection Over Signature Matching
Signatures catch known attacks. Behavior catches novel ones.
- Track velocity (requests per second).
- Monitor patterns (sequential page access, missing referrers, unusual User-Agents).
- Detect credential stuffing, scraping, and enumeration by behavior, not just payload.

**AI prompt hint:** "Implement rate limiting based on request patterns, not just IP counts."

---

### 3. Collaborative Defense
Share threat intelligence. Benefit from collective knowledge.
- Use community blocklists (CrowdSec, AbuseIPDB, Spamhaus).
- Report attacks back to the community.
- Subscribe to real-time threat feeds.

**Resource:** [CrowdSec Hub](https://hub.crowdsec.net) | [AbuseIPDB](https://www.abuseipdb.com/)

---

## 🔒 Core Hardening Rules

### Bot Detection & Fingerprinting
Distinguish humans from bots before they reach your logic.

| Signal | Human | Bot |
|--------|-------|-----|
| JavaScript execution | ✅ Yes | ❌ Often No |
| Cookie acceptance | ✅ Yes | ❌ Often No |
| Mouse movement patterns | Organic | None/Linear |
| Request timing | Variable | Uniform |
| TLS fingerprint | Browser-consistent | Library-consistent |

**Tactics:**
- Deploy JavaScript challenges for suspicious traffic.
- Use CAPTCHA as a fallback, not a first line.
- Implement invisible honeypot fields in forms.

```html
<!-- Honeypot field: bots fill this, humans don't see it -->
<input type="text" name="website" style="display:none" tabindex="-1" autocomplete="off">
```

**Review rule:** If a form doesn't have bot protection, it's vulnerable.

---

### Rate Limiting & Throttling
Abuse happens at scale. Rate limits make scale expensive.

- **Global limits:** 100 requests/minute per IP (adjust for your use case).
- **Endpoint limits:** Sensitive endpoints (login, signup, API) get stricter limits.
- **Sliding windows:** Use sliding window algorithms for smooth limiting.
- **Exponential backoff:** Increase delays for repeat offenders.

```typescript
// Example: SvelteKit rate limiting middleware concept
const RATE_LIMIT = 100; // requests
const WINDOW_MS = 60 * 1000; // 1 minute

function checkRateLimit(ip: string): boolean {
  const key = `rate:${ip}`;
  const count = cache.get(key) || 0;
  if (count >= RATE_LIMIT) return false;
  cache.set(key, count + 1, WINDOW_MS);
  return true;
}
```

**AI prompt hint:** "Add rate limiting middleware with per-IP and per-endpoint limits."

---

### Security Headers
Headers are your first line of browser-side defense.

```typescript
// Essential security headers for SvelteKit/Node
const securityHeaders = {
  'X-Content-Type-Options': 'nosniff',
  'X-Frame-Options': 'DENY',
  'X-XSS-Protection': '1; mode=block',
  'Referrer-Policy': 'strict-origin-when-cross-origin',
  'Permissions-Policy': 'camera=(), microphone=(), geolocation=()',
  'Content-Security-Policy': "default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline';",
  'Strict-Transport-Security': 'max-age=31536000; includeSubDomains; preload'
};
```

**Verification step:** Use [securityheaders.com](https://securityheaders.com) to audit your headers.

---

### IP Reputation & Blocklists
Not all IPs are equal. Known bad actors should be blocked at the edge.

**Integration options:**
- **CrowdSec:** Self-hosted, community-driven blocklist with bouncers.
- **Cloudflare:** Built-in bot management and IP reputation.
- **Fail2ban:** Classic host-based intrusion prevention.

**Tactics:**
- Block IPs from known VPN/proxy/Tor exit nodes for sensitive operations.
- Allow VPN traffic for general browsing (don't punish privacy users).
- Implement progressive trust—new IPs get more scrutiny.

---

### Authentication Hardening
Login flows are the #1 bot target.

- **Account lockout:** Lock after 5 failed attempts (with exponential backoff).
- **Credential stuffing defense:** Detect login attempts from same IP with different usernames.
- **Device fingerprinting:** Flag logins from new devices.
- **MFA enforcement:** Require MFA for sensitive accounts.

```typescript
// Credential stuffing detection pattern
const loginAttempts = new Map<string, Set<string>>();

function detectCredentialStuffing(ip: string, username: string): boolean {
  const users = loginAttempts.get(ip) || new Set();
  users.add(username);
  loginAttempts.set(ip, users);
  
  // More than 3 different usernames from same IP in short window = suspicious
  return users.size > 3;
}
```

**Review rule:** If login doesn't have brute-force protection, it's vulnerable.

---

### Web Application Firewall (WAF) Rules
Block malicious payloads before they reach your application.

**Common attack patterns to block:**
- SQL injection: `' OR '1'='1`, `; DROP TABLE`, `UNION SELECT`
- XSS: `<script>`, `javascript:`, `onerror=`
- Path traversal: `../`, `..%2F`, `/etc/passwd`
- Command injection: `; ls`, `| cat`, `` `whoami` ``

**Tactics:**
- Use managed WAF rules (Cloudflare, AWS WAF, Vercel).
- Log blocked requests for threat intelligence.
- Review false positives regularly—don't break legitimate traffic.

---

## 🕵️ Detection Scenarios

### Brute Force Detection
```yaml
# CrowdSec-style scenario definition
name: http-brute-force
description: Detects HTTP brute force attempts
filter: "evt.Meta.log_type == 'http_access'"
groupby: "evt.Meta.source_ip"
capacity: 5
leakspeed: 10s
blackhole: 5m
```

**Behavior:** More than 5 failed login attempts in 10 seconds = 5 minute block.

---

### Scraping Detection
- Rapid sequential access to paginated content.
- Missing or fake referrer headers.
- Accessing resources in non-human order (e.g., page 1, 2, 3, 4, 5 in exact sequence).
- User-Agent mismatch (claims Chrome but TLS fingerprint says Python).

---

### Credential Enumeration
- Different usernames, same password (reverse brute force).
- Sequential username attempts (user1, user2, user3...).
- Timing attacks on "user not found" vs "wrong password" responses.

**Defense:** Always use constant-time responses for auth. Same message, same delay.

---

## 🛠️ Implementation Checklist

### Edge Layer (CDN/Proxy)
- [ ] Enable DDoS protection.
- [ ] Configure rate limiting at the edge.
- [ ] Enable managed WAF rules.
- [ ] Integrate IP reputation blocklists.
- [ ] Set up geo-blocking if applicable.

### Application Layer
- [ ] Implement rate limiting middleware.
- [ ] Add honeypot fields to all forms.
- [ ] Set security headers on all responses.
- [ ] Log failed authentication attempts.
- [ ] Implement account lockout with backoff.

### Monitoring & Response
- [ ] Alert on unusual traffic patterns.
- [ ] Log blocked requests with context.
- [ ] Review blocklist effectiveness weekly.
- [ ] Have an incident response plan for attacks.

---

## 📚 Resources

| Resource | Purpose |
|----------|---------|
| [CrowdSec](https://crowdsec.net) | Collaborative IDS/IPS with community blocklists |
| [Cloudflare Security](https://www.cloudflare.com/security/) | Edge security, WAF, bot management |
| [OWASP Bot Management](https://owasp.org/www-project-web-security-testing-guide/) | Testing guide for bot defenses |
| [Have I Been Pwned API](https://haveibeenpwned.com/API/v3) | Check credentials against breach databases |
| [Fail2ban](https://www.fail2ban.org/) | Host-based intrusion prevention |

---

## 🏆 The "Hardened Application" Checklist

- [ ] **Rate limiting** is enforced at edge and application layers.
- [ ] **Security headers** score A+ on securityheaders.com.
- [ ] **Bot detection** uses behavioral signals, not just CAPTCHAs.
- [ ] **Login flows** have brute-force and credential stuffing protection.
- [ ] **WAF rules** block common attack patterns.
- [ ] **IP reputation** is integrated for known bad actors.
- [ ] **Logging** captures enough context for threat analysis.
- [ ] **Alerts** fire on anomalous behavior patterns.

---

*Remember: Security is a process, not a product. Every blocked attack is a lesson. Every successful attack is a failure to learn from others' mistakes. Collaborate, share, and defend together.*
