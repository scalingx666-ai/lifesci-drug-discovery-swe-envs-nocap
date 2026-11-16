# Issue

**Title:** test(e2e): retry smoke suite in CI to absorb cold-start canvas flake

## Description

## Problem
Every open PR (#489, #490, …) shows a red **e2e** check even when the code is fine. The failure is always the **first** smoke test — `launcher renders the sample structure preview` — timing out on `canvas` visible, while the other two smoke tests pass in the same run.

## Root cause
That first test renders a live WebGL canvas. On a **cold** CI worker (SwiftShader software GL + WASM build + `pnpm desktop:dev` warm-up) the first-ever canvas can exceed the 20s visibility wait; by the time the later tests run, everything is warm and they pass. `playwright.config.ts` never set `retries`, so it defaults to **0** — one cold-start flake fails the whole job.

e2e is `continue-on-error` (non-gating), so this never blocked merges, but it painted a red X on every PR and eroded signal.

Proof it's infra, not code: unrelated PRs with no rendering changes (e.g. #490, a pure revert) hit the identical failure.

## Fix
`retries: CI ? 2 : 0`. A cold-start flake self-heals on a warm retry; a genuine breakage still fails all three attempts, so this narrows flakiness without masking real bugs. No change locally (retries 0).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d47e23fb4ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.