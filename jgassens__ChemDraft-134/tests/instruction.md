# Issue

**Title:** Status hints name Alt on Windows, Option on macOS

## Description

On Windows, the Lasso status hint said "Option subtracts" and the Eyedropper hints said "⌥ click copies all"; on Windows that key is Alt. This was seen in #131's Windows run.

- New pure helper `apps/desktop/src/modifierLabels.ts` takes the platform, defaulting to `detectDesktopShortcutPlatform()`, and gives each modifier's name: Option/⌥ on macOS, Alt on Windows.
- The drawing-tool status labels and both Eyedropper target hints go through it. macOS text is unchanged.
- `modifierLabels.test.ts` covers both platforms by passing the platform in.

**Review in progress:** other status-line hints may still show Mac symbols on Windows, for example "⌥: subtract from selection", "⌘ + wheel: zoom" and "release ⇧". The reviewer is asked to list every one.

**Platforms:** Windows hands-on check of the Lasso and Eyedropper hints requested; the macOS text is unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `673554d61bff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.