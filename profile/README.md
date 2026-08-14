<div align="center">

# Decionis

### The deterministic decision layer between intent and execution.

*Before AI acts, Decionis decides.*

[![License](https://img.shields.io/badge/license-Apache--2.0-1f6feb)](https://github.com/decionis/.github/blob/master/LICENSE)
[![Status](https://img.shields.io/badge/status-live-brightgreen)](https://decionis.com/?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)
[![Verdicts](https://img.shields.io/badge/verdicts-%3C120ms-2ea043)](https://decionis.com/docs?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)
[![Docs](https://img.shields.io/badge/docs-decionis.com-blue)](https://decionis.com/docs?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)
[![Sandbox](https://img.shields.io/badge/sandbox-no_account_needed-8250df)](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)
[![Community](https://img.shields.io/badge/community-policy_exchange-e85aad)](https://decionis.com/policy-exchange?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)

</div>

---

AI agents open pull requests, trigger deploys, issue refunds, and change production state. Decionis sits between the moment something *wants* to act and the moment it *does*: every high-stakes action is checked against policy **deterministically** — same input, same verdict — and receives **ALLOW**, **BLOCK**, **RESTRAIN**, or **ESCALATE** in under 120 ms, sealed as a cryptographically signed **Decision Dossier** you can verify offline.

## 🚀 Start here — pick your surface

| Purpose / Domain | Repository / Package | Quick start | Links |
| --- | --- | --- | --- |
| **CI/CD Action Gate** — gate risky workflow steps: deploys, AI-generated PRs, Terraform applies | [`decionis/govern`](https://github.com/decionis/govern) | `uses: decionis/govern@v1` | [Docs](https://decionis.com/docs/quickstart?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) |
| **Agent Tool Control (MCP)** — a permission layer between LLM agents and their tools | [`decionis/mcp`](https://github.com/decionis/mcp) | `npx -y --package=@decionis/mcp decionis-mcp` | [Docs](https://decionis.com/docs/protocol-mcp?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) |
| **Presence SDKs (Go · Swift)** — verify human presence before consequential actions execute | [`decionis/presence-go`](https://github.com/decionis/presence-go) · [`decionis/presence-swift`](https://github.com/decionis/presence-swift) | `go get github.com/decionis/presence-go@v0.2.0`<br>Swift: add `https://github.com/decionis/presence-swift` at `0.2.0` | [Docs](https://presence.decionis.com/developers/quickstart?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) |
| **Dossier Verification** — independently verify any signed Decision Dossier | [`decionis/govern`](https://github.com/decionis/govern) | `steps.<gate>.outputs.verify-url` | [Docs](https://decionis.com/verify/decision-dossiers?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) |
| **API Gateway Plugin** — human verification at the edge, with no application code changes | [`decionis/kong-plugin-presence`](https://github.com/decionis/kong-plugin-presence) | `luarocks install kong-plugin-presence` | [Docs](https://presence.decionis.com/developers/kong?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) |
| **Reference Architecture** — the whole pattern end to end, runnable: intent capture → verdict → human approval → safe execution | [`decionis/agent-safe-pipeline`](https://github.com/decionis/agent-safe-pipeline) | `gh repo clone decionis/agent-safe-pipeline` | [Architecture](https://github.com/decionis/agent-safe-pipeline/blob/main/ARCHITECTURE.md) · [Threat model](https://github.com/decionis/agent-safe-pipeline/blob/main/THREAT-MODEL.md) |

> 🕹️ **No account needed** — run a live policy check in the [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) and watch a real verdict and signed dossier come back.

## 🧭 How it works

```mermaid
sequenceDiagram
    autonumber
    participant T as Intent / Trigger
    participant E as Decionis Engine
    participant H as Human approver (Presence)
    participant X as Execution

    T->>E: Propose action + context
    Note over E: Policy check (deterministic)<br/>Gate 1 · State Admission<br/>Gate 2 · Execution Authority
    alt Verdict ALLOW
        E-->>X: Proceed with execution
    else Verdict BLOCK
        E-->>T: Halt, with machine-readable reasons
    else Verdict RESTRAIN
        E-->>T: Hold for human review before execution
    else Verdict ESCALATE
        E->>H: Request live human approval
        H-->>E: Approve / deny
    end
    E-->>T: Signed Decision Dossier (Ed25519, verifiable offline)
```

1. **Intent / Trigger** — a CI job step, an AI agent's tool call, or an API request declares what it wants to do *before* doing it.
2. **Decionis Engine (policy check)** — the dual-gate engine evaluates the action deterministically: Gate 1 admits the claimed state, Gate 2 decides execution authority. Same input, same verdict, in under 120 ms.
3. **Verdict** — **ALLOW** lets execution proceed, **BLOCK** halts it with reasons, **RESTRAIN** holds the action for human review, and **ESCALATE** routes to a live human check via [Presence](https://presence.decionis.com/?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery). The hosted API returns these as `APPROVE` / `REJECT` / `REQUIRE_REVIEW` and the clients normalize them, so expect both spellings on the wire.
4. **Signed Decision Dossier** — every verdict ships as an Ed25519-signed, immutable audit record. Verify any dossier independently via its `verify-url` or the [dossier verification page](https://decionis.com/verify/decision-dossiers?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) — no trust in us required.

<details>
<summary><b>🔏 What a Decision Dossier looks like</b></summary>

```json
{
  "dossier": "dsr_2026_9f2ka8",
  "action": "deploy.production",
  "verdict": "ALLOW",
  "policy": "prod-deploy-gate@v3",
  "gates": { "state_admission": "pass", "execution_authority": "pass" },
  "latency_ms": 42,
  "alg": "ed25519",
  "sig": "kQ4vR…8zPw"
}
```

</details>

## 🤝 Community & contributing

- **Contribute** — read our [contributing guide](https://github.com/decionis/.github/blob/master/CONTRIBUTING.md) and open issues with the [structured templates](https://github.com/decionis/.github/tree/master/ISSUE_TEMPLATE). We welcome bug reports, policy templates, connectors, and docs.
- **Security** — found a vulnerability? **Don't open a public issue** — see our [security policy](https://github.com/decionis/.github/blob/master/SECURITY.md) or email [security@decionis.com](mailto:security@decionis.com).
- **Policy Exchange** — share and reuse community policy templates on the [Policy Exchange](https://decionis.com/policy-exchange?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery).
- **Talk to us** — questions about the hosted platform or integrations: [contact](https://decionis.com/contact?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery).
- We follow the [Contributor Covenant Code of Conduct](https://github.com/decionis/.github/blob/master/CODE_OF_CONDUCT.md).

---

<div align="center">

**[decionis.com](https://decionis.com/?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)** · [Docs](https://decionis.com/docs?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Integrations](https://decionis.com/integrations?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) · [Sandbox](https://decionis.com/sandbox?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery)

*Every high-stakes action asks permission — and receives a signed Decision Dossier.*

</div>
