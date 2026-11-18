# Issue

**Title:** Layout: a page with many overlapping rings no longer freezes the app

## Description

## Summary

A page of 256 overlapping benzene rings (made by Select All, Copy, Paste eight times) froze the canvas for minutes. Profiling put 96% of the time in `warnForDepthCycles` in `packages/layout-engine`: it compared every pair of bond crossings, then scanned all crossings again for a closing edge, which is effectively cubic. With 22,880 crossings it took 112 seconds on every render, and found nothing.

It now builds an adjacency map and a set of edges and checks each chained pair with a set lookup: the same three-edge cycles, the same warning, near-linear cost. The crossing sweep also rejects invalid or zero-length segments once instead of for every pair. Output is unchanged: every layout-engine and export-engine snapshot passes. The same page now plans in about 0.3 seconds, and a new test fails if it ever takes more than three.

**For the owner:** the check only detects cycles of three crossings (A over B, B over C, C over A). Longer cycles are possible (a four-edge fixture shows one) and would also prevent a consistent depth order; whether to warn for them too is a decision, not part of this fix.

## Files changed

- `packages/layout-engine/src/index.ts`: `warnForDepthCycles`, crossing sweep.
- `packages/layout-engine/src/index.test.ts`: three-cycle warning, acyclic case, 256-ring timing.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 306 files, 6118 tests pass; 256 rings plan in 321 ms

## Platforms

- macOS and Windows: paste a benzene 256 times (Select All, Copy, Paste ×8); the app stays responsive

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `881ad9b98930`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.