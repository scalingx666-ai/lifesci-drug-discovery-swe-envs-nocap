# Issue

**Title:** Tests: give five heavy tests room on busy machines

## Description

Five tests pass but crossed vitest's 5 s default on a loaded machine or on the Windows CI runner. They failed CI runs that had nothing to do with them; seen several times on 2026-10-12, and re-runs passed. Each now has an explicit 20 s timeout and a one-line comment. No assertion, fixture or config changes.

| File | Test | Seen |
|---|---|---|
| `apps/desktop/src/MainWindow.dragPerf.dom.test.ts` | does not search the document or recompute unchanged modifier hints on drag frames | 5.5 s on Windows CI (#109's first run) |
| `apps/desktop/src/toolsetBridge.dom.test.ts` | centers every double bond of a whole selected molecule as one undo entry; stress-routes repeated Art commands across a multi-ring selection | 5.5 s, 7.8 s locally under load |
| `apps/desktop/src/documentWorkflow.test.ts` | keeps a dative-bridged polymer's dendrons where they were drawn | 5.9 s locally under load |
| `packages/rdkit-adapter/src/analysis.real.test.ts` | composition is source-preserving (describe) | 5.2 s, 7.7 s locally under load |
| `tools/plugin-extract/extract.test.ts` | refuses a committed symlink… | timed out at 5 s on Windows CI (#130's run) |

Not changed: `ocl-adapter/src/stereo.test.ts` already sets 20 s for the whole file, and `tools/agent-skill/ringStyle.test.ts` already gives its command-line tests 120–180 s.

**Platforms:** test-only; CI covers Linux, macOS and Windows.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2c48f483bd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.