# Issue

**Title:** Layout: crossing checks look up overrides once and skip impossible cycle searches

## Description

. Crossing resolution on a page with many overlapping rings does less work per render.

**What changed** (`packages/layout-engine/src/index.ts`)
- Crossing overrides are read into a map once per page. Before, each crossing pair built its key twice and scanned every override twice.
- The depth-cycle warning skips work it can prove is unnecessary. Without an override, the default depth order is strict, so a cycle must pass through at least one override. With no overrides the check returns at once; otherwise it starts only from override edges.
- Both shortcuts apply only when every bond key on the page is unique. Duplicate object ids, or ids that join to the same key, fall back to the full search, so every page warns exactly as before.

**Measured** on the 256-overlapping-rings page, macOS, median of nine renders: 93.7 ms before, 51.5 ms after.

**Tests**
- A seeded test compares the result with an independent reference (its own depth rule and a brute-force cycle search) on random pages. The pages cover overrides, override cycles, duplicate object ids, colliding keys and overrides whose front matches neither bond.
- The two colliding pages found in review are explicit tests that must warn.

**Reviews:** Astra blocked round 1 (key collisions); round 2 APPROVE.

**Platforms:** macOS: tests and benchmark; in the combined Mac build checked on 2026-10-12. Windows: in the drag-transform run on the combined branch (256-ring drag 13.2 → 1.9 s with the transform change); CI.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd03f05ec716`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.