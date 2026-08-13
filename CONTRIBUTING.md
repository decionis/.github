# Contributing to Decionis

Thanks for your interest in improving Decionis — the deterministic decision layer between intent and execution. We welcome bug reports, feature proposals, policy templates, connectors, documentation, and code across all public repositories in this organization.

This guide covers organization-wide conventions. Individual repositories may add their own setup and test instructions in their `README.md` or a local `CONTRIBUTING.md`, which take precedence.

## Where to start

- 🐛 **Found a bug?** Open an issue with the **Bug report** template — it asks for the affected package, a minimal reproduction, and your environment.
- ✨ **Have an idea?** Open an issue with the **Feature request** template. For community policy templates, also see the [Policy Exchange](https://decionis.com/policy-exchange?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery).
- 🔐 **Security problem?** **Never** open a public issue — follow our [security policy](SECURITY.md) and email [security@decionis.com](mailto:security@decionis.com).
- 💬 **Platform questions?** Use the [contact page](https://decionis.com/contact?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) rather than the issue tracker.
- 🌱 **First contribution?** Look for [`good first issue`](https://github.com/search?q=org%3Adecionis+label%3A%22good+first+issue%22+state%3Aopen&type=issues) across our repositories.

## Ground rules

1. **Be excellent to each other.** All participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
2. **Issue first for non-trivial changes.** Open or claim an issue before starting significant work, so we can agree on direction and nobody duplicates effort. Typo and small doc fixes can go straight to a PR.
3. **One PR, one concern.** Small, focused pull requests get reviewed quickly; grab-bag PRs stall.
4. **Determinism is the product.** Policy evaluation must stay deterministic — same input, same verdict. Changes that could affect verdict evaluation, signing, or dossier output must keep dossiers verifiable — check one produced by your change via its `verify-url` or the [dossier verification page](https://decionis.com/verify/decision-dossiers?utm_source=github&utm_medium=org_readme&utm_campaign=dev_discovery) — and the PR template asks you to confirm this.

## Development workflow

1. **Fork** the repository you're changing and create a branch: `feat/<topic>` or `fix/<topic>`.
2. **Make your change**, matching the style of the surrounding code. Add or update tests for anything you touch.
3. **Run the test suite** locally — each repo documents its own runner (typically `npm test`). All checks must be green.
4. **Write [Conventional Commits](https://www.conventionalcommits.org)** — e.g. `feat(mcp): add per-tool rate policies`, `fix(govern): honour ESCALATE on re-run`. This drives our automated changelogs and releases.
5. **Open the pull request.** The template's checklist (tests, dossier verification, documentation) must be complete before review. CI — including our own `decionis/govern` gates — must pass before merge.
6. **Review.** A maintainer will review, request changes if needed, and merge. We aim for a first response within a few business days.

## What we're especially glad to receive

- **Policy templates** — real-world gate patterns (AI-generated PR gating, Terraform apply checks, refund limits) for the Policy Exchange.
- **Integrations & connectors** — new CI providers, MCP client runtimes, or platform surfaces.
- **Reproductions** — a failing minimal example is a first-class contribution, even without a fix.
- **Docs** — anything that shortens the path from "landed on the repo" to "first verdict".

## Licensing

Unless a repository states otherwise, contributions are accepted under that repository's existing open-source license, and you certify that you have the right to submit the work.
