# Issue

**Title:** Docs: re-point AGENTS.md citations to the renumbered sections

## Description

## Summary

AGENTS.md was renumbered on 2026-10-04 (#66), and its old and new section numbers overlap. A Fable review of that PR found comments that cite a section which does not hold the rule, even through the old-to-new map in AGENTS.md §17. Each of those now names the **new number and the section title**, so it cannot be misread:

| Where | Was | Now |
|---|---|---|
| `apps/desktop/src/plugins/selectionSnapshot.ts` | §10 (no fake chemistry) | §12 UI |
| `packages/rdkit-adapter/src/identifiers.ts` | §8 | §8 Analysis and prediction claims |
| `apps/desktop/src/documentWorkflow.test.ts` (malformed paste) | section 16 | §13 Security, errors, and performance |
| `packages/cdx-compat/src/index.test.ts` (silently lost arrow) | section 16 | §7 Chemistry invariants |
| `packages/chemdraft-cli/src/commands/export.test.ts` | §5.26 | reworded; §7 Chemistry invariants |
| keybinding-scheme doc in `docs/shipped/` | §6.9 | §12 UI |
| `packages/analysis-core/src/provenance.ts` | §14, §8a | §13 Security, errors, and performance; §8 Analysis and prediction claims |
| `PLAN.md` permissions paragraph | AGENTS §7 | `PluginPermission` in `packages/plugin-api`; AGENTS §4.1 Contract and permissions |

Three stale doc lines are also fixed:
- `README.md`: `./run-app` builds `ChemDraft (dev)` with identifier `org.chemdraft.desktop.dev.<worktree-slug>` in `<worktree>/app/`, never the stable app's identity.
- `PLAN.md` §20: the root license is Apache-2.0, so it moves from "Still open" to "Answered by shipped work".
- `PLAN.md` §20: `rdkit-adapter` is a real, lazily loaded RDKit WASM engine (app Web Workers and the CLI), not a placeholder.

Comments and docs only, plus the CI-required `CURRENT_BUILD_STAMP` bump (`10.4.08.30-codex`). No behavior changes.

Every other AGENTS.md citation in the repo was checked against the §17 map and still reaches the right rule, so it was left alone. Dated reviews and reports keep their old numbers on purpose.

## Review

- Written by openai-luna via agentctl (`run-20261004-083015-1d38c2`, fixes in `run-20261004-091407-91e7c9`).
- Kimi k3 reviewed the citation commit (`run-20261004-085349-ec413c`). It confirmed every citation and doc claim, and found a dropped word and an unsupported claim about `NOTICE` in the new PLAN.md text. Both are fixed.
- Fable reviewed the fix commit and the merge of main (`run-20261004-091513-9f3d28`): no findings. The merge's only conflict was the build stamp.

## Tests

- `pnpm lint` passes.
- `pnpm vitest run` over apps/desktop, analysis-core, cdx-compat, chemdraft-cli and rdkit-adapter: 189 files and 3,266 tests passed (2 files and 7 tests skipped).
- `git diff --check` is clean.

## Platforms

These are comment and doc edits only, with nothing platform-specific. I checked them on macOS; Windows CI covers the same type check and tests.

## Known limitations

- AGENTS.md §4.7 says `NOTICE` ships with every distribution, but the Tauri bundle configuration does not package it. That gap predates this PR and is not fixed here.
- `packages/rdkit-adapter/README.md` still describes the package as a future placeholder.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `723645778645`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.