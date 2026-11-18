# Issue

**Title:** Longer time limits for slow tests that flake on busy machines

## Description

Some heavy tests pass on a re-run but hit vitest's time limit on a busy CI runner or laptop: the Windows runner on #130, and twice on Oct 12 while workers were running. Each now has an explicit, longer per-test or per-suite limit. No assertion, input, test logic or global vitest setting changed.

| File | Test or suite | Limit |
|---|---|---|
| `tools/plugin-extract/extract.test.ts` | refuses a committed symlink… | 20 → 30 s |
| `packages/rdkit-adapter/src/analysis.real.test.ts` | composition is source-preserving (real RDKit corpus) | 20 → 60 s |
| `packages/ocl-adapter/src/stereo.test.ts` | 2D→3D stereo fidelity (absolute and relative) | 5 → 30 s |
| `tools/agent-skill/ringStyle.test.ts` | ring-style.mjs suite | 5 → 30 s |
| `apps/desktop/src/MainWindow.dragPerf.dom.test.ts` | does not search the document… | 20 → 30 s |
| `apps/desktop/src/toolsetBridge.dom.test.ts` | ring-effects stress test | 20 → 30 s |

**Tests:** `pnpm lint` ✓; the six files: 153 tests ✓ (macOS).
**Platforms:** test-only change. CI runs it on Linux, macOS and Windows; no hands-on check applies.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d8376f32bd0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.