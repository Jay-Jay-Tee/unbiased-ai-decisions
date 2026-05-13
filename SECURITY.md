# SECURITY.md

# Security Policy

## 📌 Supported Versions

The latest version of Unveil is actively maintained for security and stability improvements.

| Version | Supported |
|---|---|
| Latest Release | ✅ |
| Older Releases | ❌ |

---

# 🔒 Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly.

Include:
- vulnerability description
- affected component(s)
- reproduction steps
- possible impact
- screenshots/logs if applicable

Please avoid publicly disclosing vulnerabilities before they are reviewed.

---

# ⚠️ Security Scope

Unveil includes:
- AI/ML pipelines
- explainability systems
- API endpoints
- Firebase integrations
- Gemini-based classification systems
- model evaluation workflows

Security considerations apply to:
- data handling
- model integrity
- inference APIs
- credential management
- dataset exposure
- prompt injection risks

---

# 🔑 Secrets & Credentials

Never commit:
- API keys
- Firebase credentials
- `.env` files
- access tokens
- production secrets

Use:
- `.env.example`
- environment variables
- secret management systems

Before pushing code:

```bash
git status
```

Verify sensitive files are excluded.

---

# 🧠 AI & ML Security Considerations

Contributors should be aware of:

## Prompt Injection Risks
LLM-integrated systems may be vulnerable to:
- prompt manipulation
- jailbreak attempts
- malicious inputs

Validate and sanitize external inputs wherever possible.

---

## Model Integrity
Avoid:
- unverified model artifacts
- unsafe pickle loading
- untrusted serialized objects

Only use trusted model files and validated sources.

---

## Bias & Fairness Risks
Because Unveil analyzes fairness and explainability:
- outputs should not be treated as absolute truth
- fairness metrics should be interpreted carefully
- datasets may contain historical bias

Always document assumptions and limitations.

---

# 🌐 API Security

Recommended practices:
- validate request payloads
- sanitize user inputs
- rate-limit endpoints where appropriate
- avoid exposing internal stack traces
- use secure authentication for production deployments

---

# 📦 Dependency Security

Before deployment:
- audit dependencies regularly
- keep packages updated
- avoid abandoned libraries
- review transitive dependencies

Recommended:

```bash
pip list --outdated
npm audit
```

---

# 🛡 Frontend Security

Frontend contributors should:
- avoid exposing secrets in client-side code
- sanitize rendered content
- validate uploaded data
- avoid insecure DOM injection patterns

---

# ⚖️ Responsible Disclosure

Please do NOT:
- exploit vulnerabilities maliciously
- expose private datasets
- leak credentials
- publicly disclose unpatched vulnerabilities

Responsible disclosure helps protect contributors and users.

---

# 📌 Disclaimer

Unveil is primarily an educational and research-oriented AI transparency project.

It is not guaranteed to be production hardened without additional:
- security review
- infrastructure hardening
- authentication systems
- deployment safeguards

---

# 🚀 Final Note

Security, transparency, and responsible AI development are shared responsibilities.

Thank you for helping make Unveil safer and more trustworthy.
