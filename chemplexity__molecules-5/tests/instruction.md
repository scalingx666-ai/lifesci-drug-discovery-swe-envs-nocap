# Issue

**Title:** Preserve `fixedCoords` through layout cleanup passes

## Description

The "Lint, Unit Test, And Build" job failed in `peptide-paired-routing.test.js` (bond length 0.75 and 3). With `fixedCoords` supplied, `generateCoords` returned different coordinates for the fixed atoms. The tests expect them back unchanged.

Three cleanup paths ignored fixed atoms.

- **Symmetry tidy** (`cleanup/symmetry-tidy.js`)
  - The fused-junction snap rotated an entire component, and the axis snap moved single atoms.
  - Fixed atoms are now skipped.
  - Components containing a fixed atom are excluded from junction rotation.
- **Stage runner** (`cleanup/stage-runner.js`)
  - A stage result that moves any atom in `layoutGraph.fixedCoords` is no longer accepted as the best stage. This covers stages that don't check frozen atoms themselves, such as the terminal-leaf and collateral-root retouches.
  - It applies only when `preserveFixed !== false`.
- **Large-molecule residual retouch** (`pipeline.js`)
  - `runLargeMoleculeResidualRetouch` already accepts `frozenAtomIds`, but none of its four call sites passed it.
  - All four now pass `placement.frozenAtomIds`.

Review notes:
- The stage-runner check compares against `layoutGraph.fixedCoords` only. Atoms frozen because their component was preserved from `existingCoords` are not covered.
- The runner rejects a whole stage result rather than repairing it, so a stage that moved a fixed atom loses its other improvements too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91763694ffcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.