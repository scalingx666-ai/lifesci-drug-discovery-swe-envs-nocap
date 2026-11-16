# Issue

**Title:** Expr ring primitives handle chain atoms and fused or spiro rings

## Description

Three ring primitives in `Expr` gave wrong matches:

- `RING_BOND_COUNT`, `RING_COUNT` and `RING_SMALLEST` with value 0 never matched a chain atom, so `[x<2]`, `[R<1]` and `[r{0-6}]` missed chain atoms. `QueryAtomContainer.create(.., RING_BOND_COUNT)` on 4-pyridone, the example in its Javadoc, did not match 4-pyridone.
- The smallest ring could close through a neighbouring smaller ring: in spiro[2.5]octane `[r5]` matched two atoms and `[r6]` three instead of five.
- `RING_SIZE` (`Z<n>`) stopped at the first closure, even one of the wrong length, so in norcarane `[Z7]` matched one atom instead of seven. It also wrote `VISITED` flags on the target.

A value of 0 now matches atoms outside rings, the smallest ring is the shortest path back to the atom, and `RING_SIZE` keeps searching and uses a local array instead of the atom flags. The change is limited to `Expr`.

Nine new tests in `ExprTest`, `SmartsPatternTest` and `MolToQueryTest` fail without the change. The isomorphism, SMARTS, fingerprint and descriptor tests pass.

Found while working on the MCS class in #1314.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df9ffdc42a9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.