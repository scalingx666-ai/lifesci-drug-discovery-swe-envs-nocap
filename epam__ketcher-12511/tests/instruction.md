# Issue

**Title:** ci: upgrade CodeQL actions from v2 to v4

## Description

## Summary

`codeql-analysis.yml` used `@v2` actions, which GitHub deprecated. This PR moves it to the current majors.

```diff
- actions/checkout@v2
+ actions/checkout@v7
- github/codeql-action/init@v2
+ github/codeql-action/init@v4
+   build-mode: none
- github/codeql-action/autobuild@v2      # step removed
- github/codeql-action/analyze@v2
+ github/codeql-action/analyze@v4
```

JavaScript needs no build for CodeQL, so `build-mode: none` replaces the Autobuild step, as in GitHub's current starter workflow (`actions/starter-workflows`, `code-scanning/codeql.yml`). The language stays `javascript`, so the analysis category and existing alerts stay the same.

## Evidence

The CodeQL check on this PR is the evidence: it runs the new workflow. `actions/checkout@v7` already runs in the other workflows (8 uses).

Verified in the app: n/a. CI config only.

## Merge Danger

Two-way door: revert the commit.

Blast radius: the CodeQL job on PRs, on pushes to `master` and `release/*`, and the weekly run. If v4 finds new alerts, they show in code scanning. They do not block merge unless a ruleset requires code scanning.

Engineering workflow plan (#12512): Phase 3, task 3.6.

Memory bank: not needed.

Part of #12512

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `612acf4847bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.