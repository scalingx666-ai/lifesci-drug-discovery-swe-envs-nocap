# Issue

**Title:** Add --vib-frames for smoother TS vibration GIFs

## Description

Adds \`--vib-frames N\` to \`--gif-ts\` mode, passed through to graphRC's \`n_frames\` parameter so the vibration trajectory can be generated with more frames.
**Requires:** aligfellow/graphRC#35

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15cd3624ca62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.