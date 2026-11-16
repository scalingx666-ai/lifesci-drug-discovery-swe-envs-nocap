# Issue

**Title:** Mordred: add the molecular framework ratio descriptor

## Description

## Changes

Ports mordred's `Framework`: `fMF`, the share of the molecule made up of its ring
atoms plus the linkers joining them. The feature name was already in
`feature_names.py` and returned NaN until now.

Every input is already computed and shared, so the descriptor adds no new
per-molecule work of its own: the SSSR rings come from `RingSets`, the bonds from
`AtomicProperties`, and the denominator is `props_hydrogens.num_atoms`.

## Approach

Each ring is contracted to a single node, so a route between two rings is a path
in that quotient graph, and the non-ring atoms on it are the linkers. Three
changes make this **18–43× faster** than mordred:

- **one search per ring instead of one per pair.** A breadth-first search from a
  ring reaches every other ring at once; mordred makes a separate
  `nx.shortest_path` call for each of the `NR·(NR−1)/2` pairs. Digoxin: 8
  searches instead of 28.
- **no networkx** — flat adjacency lists and a `deque`.
- **hydrogens stay out of the graph.** Mordred iterates the bonds of the
  hydrogen-explicit molecule, which adds dozens of leaves. A hydrogen has one
  bond, so it can only ever be a dead end, never an interior atom of a path
  between two rings.

Median of repeated runs after warm-up:

| molecule | rings | mordred | this | |
|---|---|---|---|---|
| Digoxin | 8 | 1331.7 µs | 71.9 µs | 18.5× |
| Epicatechin | 3 | 343.4 µs | 14.8 µs | 23.2× |
| Caffeine | 2 | 238.8 µs | 9.9 µs | 24.1× |
| fused pentacyclic | 5 | 852.8 µs | 19.9 µs | 42.9× |
| two rings + linker | 2 | 445.7 µs | 10.7 µs | 41.6× |

## Why picking one shortest path is safe

Mordred takes a single shortest path per pair, so in principle the linker set
could depend on which one networkx happens to return. It cannot: a second,
different route between two rings would close a cycle, and ring perception turns
that cycle into a ring, so its atoms stop being linkers in the first place. I
checked every ring pair in the reference set and in four deliberately bridged
structures ([2.2]paracyclophane and friends) — zero ambiguous pairs, and in the
bridged cases every atom ends up a ring atom, leaving nothing to disambiguate.
The reasoning is recorded in `_linker_atoms`'s docstring.

## Correctness

Verified against mordred end-to-end through `NewMordredFingerprint` on 37
molecules: worst relative difference **5.02e-08**, below float32 resolution.

Reference values come from mordred-community's own
`tests/references/Framework.yaml`; Cyanidin is commented out there and is left
out here too. Thirteen further cases were computed with mordred-community and
cover the parts the reference set does not exercise: no rings at all, a lone ring
with a dangling chain (**not** a linker — a linker needs two rings), fused and
directly bonded rings (no linkers), one- and four-atom linkers, a disconnected
molecule whose two rings have no path between them, and the empty molecule.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d490ae5660c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.