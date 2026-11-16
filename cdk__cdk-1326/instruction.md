# Issue

**Title:** Preserve smallest atom ring sizes in fused and spiro systems

## Description

`Cycles.smallRingSize(atom)` can return zero for an atom in a fused or spiro ring system, depending on bond iteration order. For example, `C1C2CCC12` contains a triangle fused to a four-membered ring, but the single-atom API reports zero for a shared atom while `smallRingSizes()` correctly reports three.

After finding a small ring, the method uses that size as the bound for subsequent bond searches. A search that finds no ring within that bound returns zero; taking the minimum with zero discards the valid result. Keep the previous minimum when a bounded search returns zero.

Regression tests cover fused and spiro rings of different sizes, two serialisations of the fused graph, and inclusive/exclusive size bounds. Both new tests fail before the fix.

Validation: `mvn -o -q -pl base/test-core -am test` passes, including all 721 core tests and dependency suites. An independent temporary harness also checked ring flags, smallest atom/bond ring sizes and shortest-path distances against a separate BFS implementation on all 33,867 simple graphs with up to six vertices. Compiled with the project's `--release 8` configuration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `178127aa9634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.