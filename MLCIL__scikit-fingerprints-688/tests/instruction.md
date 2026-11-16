# Issue

**Title:** Mordred: add the molecular ID descriptors

## Description

## Changes

Ports mordred's `MolecularId`: `MID` and `AMID` over all atoms, heteroatoms,
carbons, nitrogens, oxygens and halogens. The feature names were already in
`feature_names.py` and returned NaN until now.

Three commits: the descriptor, a follow-up trimming its fixed per-molecule
cost, and a docstring explaining the algorithmic cost for future readers.

## Why this one is expensive

An atomic ID sums the inverse square root of the edge weight product over every
simple path starting at that atom. The search is a backtracking walk, not a
plain DFS — the visited mark means "on the current path" and is undone on the
way out — so it runs once per simple path rather than once per atom.

The cost is therefore exponential in the number of **rings**, not in molecule
size. For an acyclic molecule there is exactly one path per ordered pair of
atoms, so the walk degenerates to a plain traversal; each independent cycle
multiplies the number of routes:

| molecule | atoms | rings | calls from one atom |
|---|---|---|---|
| octane | 8 | 0 | 8 (same as a plain DFS) |
| benzene | 6 | 1 | 11 |
| naphthalene | 10 | 2 | 32 |
| pentacene | 22 | 5 | 359 |
| cubane cage | 9 | 5 | 151 |

There is no value-preserving shortcut: the sum needs one term per path, and the
paths must be simple, so the state is the whole visited set rather than the
current atom — no per-atom dynamic programming can stand in for walking them.
This makes it the most expensive descriptor in the package.

## Performance

The arithmetic matches mordred exactly. The speedup comes from constants: the
graph is nested lists of plain ints instead of a networkx graph (which cost two
dict lookups per edge), visited atoms live in a `bytearray` instead of a `set`,
and partial sums are returned rather than accumulated on an object.

Best of N runs after warm-up:

| molecule | atoms | mordred | this | |
|---|---|---|---|---|
| Digoxin | 55 | 120.2 ms | 26.6 ms | 4.6× |
| pentacene | 22 | 12.8 ms | 2.5 ms | 5.4× |
| EllagicAcid | 22 | 9.6 ms | 2.0 ms | 5.7× |
| Lycopene | 40 | 3.6 ms | 0.59 ms | 6.2× |
| Caffeine | 14 | 1.6 ms | 0.26 ms | 6.2× |
| Benzene | 6 | 0.41 ms | 0.05 ms | 8.8× |

The second commit targets small molecules, where a size-independent ~35 µs of
mask building dominated everything else. Selecting halogens with `np.isin` alone
took 17.9 µs on a 12-atom molecule — sorting its handful of needles costs more
than the lookup — against 0.33 µs for a boolean table indexed by atomic number.
That, plus dropping the all-true mask for the first feature pair, takes the
fixed part from ~35 µs to ~15 µs: ethane goes from 43.6 µs to 24.3 µs, benzene
from 60.8 µs to 46.6 µs. Larger molecules are unaffected, being dominated by
the path search.

## Correctness

Verified against mordred on 35 molecules (the bundled reference set plus an
aminoglycoside, a fused polycyclic and inositol): worst relative difference
**5.77e-08**, below float32 resolution, and unchanged by the optimisation
commit. Disconnected molecules give NaN on both sides, matching mordred's
`require_connected`.

## Notes for reviewers

A heteroatom here is anything but carbon **and hydrogen**, unlike
`AtomicProperties.is_hetero`, which is carbon-only. This differs only for the
hydrogens `RemoveHs` keeps — `[H][H]` has `MID_h == 0`, where the shared
predicate would give 3.0 — and two tests pin it.

Reference values for `MID`/`AMID` are converted from mordred-community's own
`tests/references/MolecularId.yaml`. The element-filtered features are not
covered there, so those values were computed with mordred-community; the test
module's docstring records both provenances.


## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `822c2c9f55f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.