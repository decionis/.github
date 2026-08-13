# Pull request

## Summary

<!-- What does this PR change, and why? One or two sentences. -->

Closes #<!-- issue number, if any -->

## Type of change

- [ ] 🐛 Bug fix
- [ ] ✨ New feature / enhancement
- [ ] 📚 Documentation
- [ ] 🧹 Refactor / chore
- [ ] 💥 Breaking change

## How was this tested?

<!-- Commands run, environments covered, new or updated test cases. -->

## Checklist

- [ ] **Tests pass locally** — run this repo's test suite (see its README / CONTRIBUTING notes) and all checks are green.
- [ ] I added or updated tests covering this change.
- [ ] **Dossier verification (if applicable)** — this change touches verdict evaluation, signing, or dossier output, and I ran the offline verifier (`npx @decionis/verify`) against a dossier produced by this branch: determinism and signatures are intact. *(Skip if your change cannot affect decision output.)*
- [ ] **Documentation updated** — README, docs site, or inline reference reflects any behaviour change.
- [ ] No secrets, tokens, or private dossier payloads in code, fixtures, or logs.
- [ ] Commit messages follow [Conventional Commits](https://www.conventionalcommits.org) (e.g. `fix(sdk): handle ESCALATE timeout`).

<!-- By submitting this pull request, you agree to follow our Code of Conduct:
     https://github.com/decionis/.github/blob/master/CODE_OF_CONDUCT.md -->
