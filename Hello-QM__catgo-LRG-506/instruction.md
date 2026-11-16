# Issue

**Title:** feat(viewer): reduced-motion preference (gate viewer animations + honor OS setting)

## Description

Ported from pretty-lattice. Adds a **Reduce motion** viewer setting (default off) that, when on — OR when the OS `prefers-reduced-motion: reduce` matches — suppresses the viewer's continuous animations.

## What it gates
- Pulsing selection highlight (rAF)
- Vibration-mode auto-play atom oscillation (rAF)
- Camera auto-rotate (rAF)
- Trackball inertia/damping (forces `staticMoving`)
- Trajectory auto-play (won't auto-start)

## Design
- Pure helper `should_reduce_motion(setting, mediaMatches)` = `setting || mediaMatches`; `os_prefers_reduced_motion()` is SSR-safe. Each rAF `$effect` early-returns when reduced (mirrors the existing phase-diagram pattern), so toggling on mid-animation cancels the running loop via effect cleanup.
- New `reduced_motion` boolean setting (config + types + i18n en/zh + checkbox in the camera settings section). Flows to StructureScene via the existing `{...scene_props}` spread.
- **Off + OS pref unset ⇒ byte-identical to today** (every gate is an early-return/OR that only fires when reduced).

Trajectory auto-start guard landed at the real auto-start `$effect` (Trajectory.svelte:436), not the setInterval driver.

Tests: 6/6 in `tests/vitest/reduced-motion.test.ts`; `pnpm check` 0 errors.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de6275dceaf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.