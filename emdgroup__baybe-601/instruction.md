# Issue

**Title:** Enable Scalable FPS via optional `fpsample` package

## Description

opened as a new PR due to fork permissions, based on #547

- Added `fpsample` as optional dependency
- If `fpsample` is available, the `fps_sampling` is used as utility instead our own `farthest_point_sampling`

**Notes**
`fpsample` offers more variants of fps-like algorithms, see [README](https://github.com/leonardodalinky/fpsample?tab=readme-ov-file#performance). Ti find out whether its worth to use any of those or even a custom kdtree implementation I did some tests, finding 50 fps points out of N points with D dimensions.
<img width="1784" height="1360" alt="image" src="https://github.com/user-attachments/assets/78100c6e-9ad5-45bf-a801-95930aca3b16" />
- fpsample npdu is the clear winner but according to the README it is the only one that can provide suboptimal results
- the vanilla fpsample implementation (used in this PR) seems to be the second winner
- custom kdtree FPS implementations, usign kdtree from sklean are soemtimes better sometimes wore than the brute force variant (out fall back). A heuristic for the number of leaves (in square brackets) could provide reasonably robust results, but they will also be quite a bit worse than anything in fpsample

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4f946d29d9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.