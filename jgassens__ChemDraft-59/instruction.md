# Issue

**Title:** Ship stable builds without a worktree label

## Description

## What changes

Stable package builds no longer carry the worktree label. v0.3.7 (built on `release/0.3.7` in the `chemdraw` folder) shipped titled **"ChemDraft — chemdraw [release/0.3.7]"**, with the branch in its build stamp too.

A build counts as **stable** when it goes through `scripts/desktop-tauri.mjs` as a `build` and is either on `main` or has `CHEMDRAFT_STABLE_BUILD=1`. For those:

- window title: plain **"ChemDraft"**
- build stamp: version stamp + date + short SHA, without the `<dir> [<branch>] · ` prefix

Dev and branch builds keep their label exactly as AGENTS.md §21.1 requires. `run-app` calls the Tauri CLI directly, so it isn't affected.

## How

- `scripts/worktree-identity.mjs`: new `isStableBuild` and `worktreeLabelFor`. A stable build gets `""`, even when the shell already exports a label, so a stale label can't leak into a release.
- `scripts/desktop-tauri.mjs`: the label is decided **before** the macOS branch, and that env is now passed to the macOS child. Before this, macOS never set the variable at all, so `vite.config.ts` fell back to asking git. The branch-build check uses the same helper.
- `apps/desktop/vite.config.ts`: a label that is set but empty now means "no label", with no git fallback. The Rust title (`main_window_title`) already treats an empty label as plain "ChemDraft", and `build.rs` re-emits the empty value, so no Rust change was needed.
- `AGENTS.md` §21.1: documents the stable-build exception.
- `CURRENT_BUILD_STAMP` → `10.1.18.41-opus`.

## Verification

- `pnpm vitest run scripts/worktree-identity.test.ts`: 5 passed. `scripts/**/*.test.ts` was added to the vitest include list, since nothing under `scripts/` was tested before.
- `pnpm lint`: passes.
- `git diff --check`: clean.
- `CHEMDRAFT_WORKTREE_LABEL= pnpm --filter @chemdraft/desktop build:web`: the bundled stamp is `2026-10-02 09:24:41 2144a86`, with no worktree name.
- **Not run:** a full signed macOS or Windows `tauri build`, and the full `pnpm test`. The native title comes from code that already handled an empty label, but no packaged release was built to confirm it end to end.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a36af9b5b56f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.