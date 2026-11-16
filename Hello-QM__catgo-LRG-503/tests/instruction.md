# Issue

**Title:** feat(viewer): soften glossy material default lighting (az0/el5, dir 0.62, amb 0.5, hl 1.5)

## Description

Softens the default lighting for the **glossy** material to the values tuned live in the lighting panel:

| param | old | new |
|---|---|---|
| directional (平行光) | 2.2 | 0.62 |
| ambient (环境光) | 0.6 | 0.5 |
| highlight (高光强度) | 1.0 | 1.5 |

Azimuth (方位角 0) and elevation (仰角 5) unchanged. Less blown-out default glossy look; per-scene sliders still work. Values were user-verified live in the viewer before baking as defaults.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de6275dceaf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.