# Security Policy

Decionis is the independent Execution Authority for high-stakes actions: teams rely on our verdicts, single-use execution grants, and signed Decision Dossiers to gate what runs. Security reports are our highest-priority inbound, and we are grateful for them.

## Reporting a vulnerability

**Please do not open a public issue for security problems.**

Email **[security@decionis.com](mailto:security@decionis.com)** with:

- The affected repository or package (`govern`, `mcp`, `docker`, `agent-safe-pipeline`, `steward`, a `shield-*` or `presence-*` SDK, or an `@decionis/*` npm package) or hosted surface, and its version.
- Steps to reproduce, or a proof of concept.
- Your assessment of impact (what an attacker gains).
- Any constraints on disclosure timing you'd like us to know about.

You will receive a human response — not an autoresponder — from the engineer on rotation.

## Response SLAs

| Stage | Commitment |
| --- | --- |
| Acknowledgement | Within **1 business day** |
| Triage & severity assessment | Within **3 business days** |
| Status updates | At least every **5 business days** until resolution |
| Fix or mitigation (confirmed critical/high) | Target **30 days** |
| Coordinated disclosure | Within **90 days** of report, or earlier by mutual agreement |

We credit reporters in release notes and advisories unless you prefer to stay anonymous.

## Scope

**In scope**

- All public repositories under [github.com/decionis](https://github.com/decionis), including `govern`, `mcp`, `docker`, `agent-safe-pipeline`, `steward`, and the `shield-*` and `presence-*` SDKs, plus the published `@decionis/*` npm packages.
- The hosted platform at `decionis.com` and `presence.decionis.com` — tested only against **your own workspace or the sandbox**.
- Anything affecting **decision integrity**: signature-verification bypass, verdict tampering, replay or reuse of a single-use execution grant, or non-determinism in policy evaluation. Treat these as highest severity.

**Out of scope**

- Denial-of-service, volumetric, or spam attacks.
- Social engineering of Decionis staff or customers.
- Findings that require an already-compromised credential or device.
- Vulnerabilities purely in third-party dependencies (report upstream — but do tell us so we can pin or patch).

## Safe harbor

We will not pursue legal action for good-faith security research that stays in scope, avoids accessing other users' data, avoids degrading the service, and gives us reasonable time to remediate before public disclosure. When in doubt, email first — we're friendly.

## Supported versions

Security fixes land on the latest release line of each package. Older majors receive fixes for critical issues at our discretion — upgrade promptly.
