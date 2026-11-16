# Issue

**Title:** fix: correct Gaussian outputfile frame counting and IRC trajectories

## Description

## Summary

Fix duplicate Gaussian frame counting and make bidirectional IRC trajectories physically continuous without losing geometry/energy alignment.

## Problems

### Duplicate Gaussian trajectory frames

Gaussian output may contain both `Standard orientation` and `Input orientation`. Treating both as independent frames double-counts a physical geometry.

### Misaligned IRC point data

Gaussian writes each `Point Number` / `Path Number` marker after the work that completes that point. A point can contain multiple correction iterations, so independently collecting all markers, geometries, and SCF energies and joining them by array index can select an intermediate correction, shift later frames, and drop the real endpoint.

## Changes

### Gaussian frame counting

- Prefer `Standard orientation` when available.
- Fall back to `Input orientation` only when no standard-orientation blocks exist.
- Apply the same behavior to the Python and TypeScript parsers.

### IRC trajectory parsing

- Treat each point marker as the boundary that closes the preceding output interval.
- Build one aligned record per completed point: `{ point, path, geometry, energy }`.
- Select the final preferred orientation and final `SCF Done` energy inside that point's interval.
- Use checkpoint geometry and `Energy From Chk` only to fill missing point-zero data.
- Ignore correction/orientation output after the last completed point marker.
- Order the physical trajectory as Path 2 endpoint → transition state → Path 1 endpoint.
- Keep TypeScript and Python behavior in parity.
- Preserve IRC path, point, transition-state, and reaction-coordinate metadata.

## Implementation plan and completion

[Detailed implementation plan](https://github.com/AmonB/catgo-LRG/blob/fix/gaussian-frame-count-irc/docs/superpowers/plans/2026-07-24-gaussian-irc-point-alignment.md)

| Task | Status |
|---|---|
| Rebase onto current `main` (including #531) | ✅ Complete |
| TypeScript interval-record regression and implementation | ✅ Complete |
| Python parity regression and implementation | ✅ Complete |
| Gaussian-specific verification | ✅ Complete |
| Adjacent trajectory parser verification | ✅ Complete |
| Type checking and repository hygiene | ✅ Complete |

## Validation

- `python -m pytest tests/test_parse_gaussian.py -q` — 5 passed
- `pnpm vitest run tests/vitest/trajectory/gaussian.test.ts` — 5 passed
- `pnpm vitest run tests/vitest/trajectory tests/vitest/vasprun-trajectory.test.ts` — 515 passed, 1 skipped
- `pnpm check` — 0 errors
- Targeted ESLint and `git diff --check` — passed

The correction-iteration regression verifies exact ordered X coordinates `[-2, -1, 0, 1, 2]`, aligned Hartree energies `[-10.4, -10.3, -10.0, -10.1, -10.2]`, exclusion of the intermediate `1.1` geometry, and exclusion of fake post-summary data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08267a603b40`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.