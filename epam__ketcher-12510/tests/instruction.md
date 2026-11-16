# Issue

**Title:** ci: run openspec validate and check:autotests on every PR

## Description

## Summary

Two checks that ran only locally now run in CI on every PR.

```diff
 ci.yml  (job: build)
   npm ci → audit → build
   npm test
+  openspec validate --all --strict
+  openspec validate --archived
   example-ssr build, lint, types
+  npm run check:autotests      # tsc + eslint in ketcher-autotests
```

`check:autotests` already fails on master: #12497 (#12320) left an unused `ComboBoxValue` import in `SettingsDialog.ts`, and `setSettingsOptions` destructured `value` from a union where `SwitcherOptionEntry` has no `value`. The first commit fixes that, so the new gate starts green.

```diff
- for (const { option, value } of sortedOptions) {
+ for (const entry of sortedOptions) {
+   const { option } = entry;
+   const value = 'value' in entry ? entry.value : undefined;
```

## Evidence

Run locally, the same commands CI runs:

| Command | master | this branch |
| --- | --- | --- |
| `npm run check:autotests` | fails: 2 `tsc` errors, 1 `eslint` error, all in `SettingsDialog.ts` | passes |
| `openspec validate --all --strict --no-interactive` | 16 passed, 0 failed | 16 passed, 0 failed |
| `openspec validate --archived --no-interactive` | 6 passed, 0 failed | 6 passed, 0 failed |
| `openspec validate --all --strict` on a copy with one spec broken (`SHALL` removed) | — | exit 1, so the gate does fail |
| `npm run check:agent-docs` | — | ok |

Verified in the app: n/a. No editor code changes. `SettingsDialog.ts` is an E2E page object, and its runtime behavior is the same: `value` is still `undefined` for switcher options.

## Merge Danger

Two-way door: revert the commit to drop a step.

Blast radius: every PR to `master` and `release/**`. Any PR that breaks an OpenSpec spec or the autotests type check or lint now fails CI, where before it passed. `openspec` uses the version pinned in the root `devDependencies` (`1.15.0`), with telemetry off (`OPENSPEC_TELEMETRY=0`). `check:autotests` runs last, after the build, so it can use the built packages.

Engineering workflow plan (#12512): Phase 3, tasks 3.5 and 3.10.

Memory bank: `.memory-bank/review-workflow.md` (Gates and the PR-type table). Also `.github/workflows/README.md`.

Part of #12512

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b300ace3e4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.