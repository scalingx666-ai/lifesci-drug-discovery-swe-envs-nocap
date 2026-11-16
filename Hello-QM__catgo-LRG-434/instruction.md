# Issue

**Title:** fix(structure): default toon lighting to az 25 / el 20

## Description

Lower the **toon** (cel/cartoon) render style's default headlamp direction to **azimuth 25°, elevation 20°** (was 35° / 45°). `glossy` and `matte` profiles are unchanged.

One-line change in `LIGHTING_PROFILE_DEFAULTS` (`src/lib/settings/config.ts`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8983f92ec57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.