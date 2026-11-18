# Issue

**Title:** Version 1.1.0

## Description

## Summary

Version 1.1.0 for the joint macOS and Windows release. Five lines change:

- `apps/desktop/package.json`, `apps/desktop/src-tauri/tauri.conf.json`, `apps/desktop/src-tauri/Cargo.toml` and ChemDraft's entry in `Cargo.lock`: 1.0.0 → 1.1.0
- `CURRENT_BUILD_STAMP`: `11.02.09.30-codex`

Left alone on purpose:

- `site/index.html` still says 1.0.0: its release notes and links describe 1.0.0, and the site is updated and deployed after the release.
- `appcast.xml` and `latest.json` are written from the published release assets.
- The 1.0.0 values in `tools/release/verify-windows-updater.test.ts` and the problem-report tests in `problem_reports.rs` are test fixtures, not the app version.

## Tests run

Static change only; CI runs lint, tests and both platforms' builds. Review: Astra, low (run-20261102-092824-3a8812): no findings; installers, updater configuration, bundle settings, release workflows and tests checked for missed version pins.

## Platforms

Same commit and version for macOS and Windows (AGENTS.md §1).

Build stamp: `11.02.09.30-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2e724878e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.