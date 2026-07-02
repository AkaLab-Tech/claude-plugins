# History

Completed work log. Newest first. Each entry references the PR(s) that delivered the work.

## 2026-07

### Supply-chain guardrails: add the standard atelier `.npmrc` — 2026-07-02
**PR:** [#6](https://github.com/AkaLab-Tech/claude-plugins/pull/6) — branch `feature/marketplace-manifest`

Every other AkaLab-Tech repo carries the atelier `.npmrc` (`ignore-scripts=true`,
`minimum-release-age=10080`, `audit-level=moderate`); this repo was missing it.
Defense-in-depth only — the repo is a JSON manifest with no npm dependencies —
but it keeps the org baseline uniform if npm is ever invoked here.

Note: this PR originally shipped a full marketplace manifest authored against a
stale local clone; upstream PRs #1–#3 had already delivered the catalog, so the
branch was re-cut to this remaining delta.
