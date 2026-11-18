# Issue

**Title:** Combined: RDKit startup rule, warm-up engine choice, analyzer refusal notice

## Description

One PR for all in-flight work from the macOS and Windows sessions on 2026-10-04, reviewed once and merged once. Supersedes #68.

## What's in it

| Commit | What | From |
|---|---|---|
| a68e4af | rdkit-adapter README rewritten from the real package | macOS: "Update stale rdkit-adapter README" |
| 2d0d2f8 | AGENTS.md §13 and §6: restore "do not load heavy engines at startup unless required; prefer lazy loading" | macOS: "Reconcile RDKit idle warm-up" |
| 184cb7e, 2200943 | ocl-adapter header and dependency inventory: say when and where OpenChemLib actually loads | Kimi and Fable review findings |
| 72ec2f8 | Spin 3D idle warm-up passes the user's engine preference end to end; OpenChemLib users no longer load RDKit at startup | macOS: warm-up follow-up |
| 5656118, ccd65d9 (merged in 19e6fb8, d9e0e07) | Visible, dismissible `role="alert"` notice when an analyzer plugin refuses its input (the cause of false report #57); stays up for reading time, held while hovered or focused | Windows: "Fix Analyze Mass report not reopening after relaunch" |
| 244e2fb | Integration tests for the notice's throw, success-clears, and superseded-run paths | Fable review finding |
| 14f3f9a | The single `CURRENT_BUILD_STAMP` bump (`10.4.11.10-opus`) | integrator |

Notes on history: `c784dec` wrote `analyzerNoticeDurationMs` in parallel with `ccd65d9` and is superseded by it (d9e0e07 takes `ccd65d9`'s file verbatim). `ccd65d9`'s message says the hover-under-pointer edge is "not fixed here", but its code fixes it (`AnalyzerNoticeBody` keyed by `notice.id`, with a regression test). `5656118` is a WIP commit that does not typecheck on its own.

Sessions that reported nothing to push: "ChemDraft Windows port" and "Fix report window stealing focus after macOS unhide" (merged earlier as #56).

## Review

- Whole range `main...d9e0e07`: Claude Fable, run `run-20261004-115018-72aae4` (Kimi hit its 5-hour limit; agentctl fell back). No blocking findings. Accepted: the OCL wording (fixed in 2200943) and the missing dispatch tests (added in 244e2fb). Declined, with reasons in the PR comments: notice clears per plugin, not per analyzer; overlap with the proposals popover in the web build; `auto`/`rdkit` warm-ups deduped separately.
- Fixes `d9e0e07..244e2fb`: Claude Fable, run `run-20261004-120023-086afa`. No findings.
- Earlier: Kimi K3 reviewed 2d0d2f8's wording (`kimi-startup-rule-20261004`); a68e4af had two Kimi passes and one Fable pass before it was folded in.

## Tests (macOS, at 244e2fb)

`pnpm lint` pass · `pnpm vitest run` 4242 passed, 17 skipped, 0 failed · `git diff --check` clean · build-stamp check pass · `pnpm build` pass at 14f3f9a (only test and comment files changed after it) · no Rust changes.

## Platforms

- **macOS:** full suite and build passed here.
- **Windows:** shared React, CSS and worker code only. CI's Windows job covers types, tests and Rust. "ChemDraft Windows port" is running a hands-on check of the analyzer notice on a Windows 11 VM at `d9e0e07`; its result will be posted in the comments.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c23b7216f36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.