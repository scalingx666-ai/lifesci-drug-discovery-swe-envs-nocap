# Issue

**Title:** Add maximum common substructure search to cdk-isomorphism

## Description

Adds `MCS` to cdk-isomorphism in three classes: `MCS` (the public API), `MCSGraph` (the two molecules with their compatibility tables, rings and stereochemistry) and `MCSSearch` (the search). It keeps the API of the class from #1314, so callers only change the import, and adds `matchAll(target, limit)` and the opt-in `withCompleteRings()`, `withStereochemistry()` and `withDisconnected(minBonds)`. The class from #1314 was never released, so it is removed; the `Isomorphism` note points to the new one.

Connected search maximises atoms, then common bonds. Disconnected search maximises common bonds, then atoms, with at least `minBonds` bonds in each fragment. Every compatible bond between mapped atoms counts as common. Stereochemistry, when asked for, is a hard constraint. SMARTS queries use their own expressions; top-level SMARTS stereochemistry is not checked. A search of more than 2^30 atom pairs (about 32,000 atoms in each molecule) throws `IllegalArgumentException`; `match()` and `matchAll()` throw `Intractable` only when the time limit or an interrupt stops the search.

The search keeps one small `Level` object per depth on an explicit stack rather than recursing, so large molecules don't run out of stack. On molecules of 64 atoms or more, a bound on each pair of chain atoms, from pairing off their branches, cuts the connected search short, so glucagon against GLP-1 finds a best match in about 17 ms instead of several seconds.

On the 47 pairs from #1314 and 36 explicit-hydrogen pairs, both classes found the same optimum scores, and the same mapping sets wherever there were fewer than 1,000.

The default tool/smarts tests take about 1.1 s in all. The heavier MCS tests are tagged `SlowTest` and run with `-Pslow-tests`. `MCSCasesTest` is a table of rows run with `@ParameterizedTest`, so tool/smarts now has the `junit-jupiter-params` test dependency. The isomorphism and legacy suites pass. Compiled with `--release 8`.

The `Pattern.findSubstructure` Javadoc fix is in #1324.

The later commits simplify and document the search and add `search()` and `searchAll()`, which return the best mappings found, with a flag, when the time limit stops the search.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05ca676d5be2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.