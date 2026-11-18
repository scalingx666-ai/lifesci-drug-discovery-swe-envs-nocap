# Issue

**Title:** Chain drag: linear longest-path search, no SMILES on free-chain frames

## Description

## Summary

Dragging a free carbon chain with the chain tool slowed to a crawl as the chain grew: **1.6 s per pointer move at 200 carbons** in the original measurement (2.4 s in the bench below, which ran on a loaded 3-vCPU VM), and about the same again on release. Two causes, both fixed. Neither changes chemistry: SMILES output is identical to `main`.

1. **The SMILES writer's longest-path search was O(n³)–O(n⁴).** `longestNativePath` (`packages/document-workflow-core/src/graph.ts`) ran a breadth-first search between every ordered pair of atoms, copied the path at every step, then sorted every path.
   - Now each start atom gets one breadth-first pass with parent pointers. Only paths of the winning length are rebuilt and handed to the **unchanged** comparator, in the same order as before.
   - In a forest, a longest path runs leaf to leaf, so only leaves start a search. A chain has two leaves, so the search is linear.
   - Any graph that isn't a verified closed forest still searches from every atom. That covers rings, adjacency reaching outside the atom list, duplicate or self bonds, and lists that don't mirror each other. It is O(n²) and exact on any graph: BFS with visited-on-enqueue processes atoms in the same order as the old visited-on-dequeue queue of paths.
2. **The free-chain branch of `applyNativeChainTool` ignored `options.preview`.** It wrote the whole chain's SMILES on every pointermove. Drag frames now carry the schema's "unavailable" empty `structure`, while `chemistry` (one linear pass) stays derived. The commit (`preview: false`, already passed by `MainWindow`) derives the SMILES once. The anchored branch already honoured the flag (674575c).
3. **Anchored drags re-resolved bond orders per added carbon** (`appendNativeCarbonVertices`). Each vertex re-ran the whole-molecule bond-order resolution, re-kekulizing every aromatic ring. Now the source atom is checked once against the molecule, and each new carbon in O(1); a new carbon holds exactly one plain single bond.

## Measurements (Windows 11, Node, median ms; "before" = `main` 02537eb)

Harness: `applyNativeChainTool` + `reconcileNativeChargeMarks` + `planPageSvgRender` + `createMoleculeInspectorModel` per move, with a sub-pixel pointer jitter per call so no identity cache hits. Each side ran from its own checkout, so `@chemdraft/*` resolves to that checkout. Calls over 1 s were measured once. The machine is a 3-vCPU VM shared with other sessions: read ratios, not absolute values.

| ms | n=25 | n=50 | n=100 | n=200 | n=500 |
|---|---|---|---|---|---|
| **free chain, per move** (before → after) | 4.19 → 1.67 | 31.3 → 1.18 | 293 → 2.45 | **2437 → 4.95** | (cap: 200 segments per drag) |
| free chain, release | 3.02 → 0.46 | 24.4 → 0.69 | 305 → 0.96 | **2136 → 1.48** | — |
| anchored drag, per move (molecule total n) | 0.89 → 0.60 | 2.04 → 1.14 | 4.29 → 2.23 | 14.8 → 3.42 | **107 → 14.4** |
| anchored drag, release | 3.41 → 0.37 | 25.4 → 0.49 | 312 → 1.05 | 2687 → 1.67 | **65988 → 4.25** |
| longestNativePath, chain | 2.11 → 0.03 | 23.5 → 0.04 | 252 → 0.10 | 2410 → 0.15 | 75575 → 0.42 |
| longestNativePath, random branched tree | 2.08 → 0.07 | 30.1 → 0.27 | 318 → 1.36 | 1631 → 3.9 | 34657 → 40.6 |
| longestNativePath, 6-ring + long tail (every-atom search) | 2.04 → 0.12 | 21.6 → 0.43 | 290 → 1.61 | 2095 → 6.85 | 86414 → 89.2 |
| SMILES writer, chain | 2.21 → 0.12 | 27.3 → 0.17 | 255 → 0.29 | 2172 → 0.61 | 65362 → 1.89 |
| SMILES writer, branched tree | 2.19 → 0.14 | 21.4 → 0.43 | 205 → 1.58 | 1516 → 4.82 | 32842 → 46.2 |
| SMILES writer, ring + tail (single-cycle writer, untouched) | 0.09 → 0.08 | 0.17 → 0.14 | 0.29 → 0.29 | 0.60 → 0.50 | 1.59 → 1.21 |
| 2D Clean Up, branched tree | 3.16 → 0.49 | 24.5 → 0.87 | 237 → 2.42 | 1792 → 7.67 | 30364 → 64.3 |

Where the every-atom search is reached: the SMILES writer calls `longestNativePath` only for forests (`isForestGraph`). 2D Clean Up calls it for acyclic components. A one-ring component reaches it only when its single-cycle layout fails (in practice, a doubled bond), and components with two or more rings are skipped entirely. So ring graphs are covered for exactness but rarely reach it. A branched tree with many leaves costs O(leaves × n), 40 ms at 500 atoms. That cost is paid only on release.

## Output identity vs main (§7)

Two dumps, each run from its own checkout (`main` 02537eb vs this branch), compared byte for byte:

| Inputs | Identical |
|---|---|
| `longestNativePath` + `nativeSingleBondGraphSmiles`, 300 random trees and forests (heteroatoms, double bonds, awkward ids) | 300/300 |
| same, 150 graphs with one ring | 150/150 |
| same, 150 graphs with 2–3 rings | 150/150 |
| 2D Clean Up atom coordinates, 120 molecules | 120/120 |
| chain-tool commits: 200-carbon free chain; chain anchored on an aromatic ring (structure, chemistry, atoms, bonds) | 3/3 |

Save → reopen of the committed 200-carbon chain on the branch: no warnings, same SMILES, same atoms and bonds.

## Tests

- `packages/document-workflow-core/tests/graph.test.ts` (new) keeps the old pairwise search verbatim as an oracle. The new search matches it on:
  - 208 random trees and forests, with ids built to stress the tie-break (mixed case, digits, `_`/`-`, `é`, and `.`, the join separator);
  - 48 tie-heavy shapes (stars, spiders, complete binary trees);
  - canonically equivalent ids where `localeCompare` returns 0, so stable order decides;
  - 72 graphs with rings;
  - malformed adjacency: atom subset, duplicate bond, self bond, and one-way lists whose counts add up to a tree. A leaf-only search gets the one-way case wrong; this was checked by mutation.

  Plus SMILES goldens captured from the unmodified writer, and a **work-count test** (`longestNativePathWorkForTesting`, served from the new `@chemdraft/document-workflow-core/testing` subpath, like `kekuleSearchWorkForTesting`): ≤ 4n steps on a 200-chain, linear growth to 400.
- `apps/desktop/src/documentWorkflow.test.ts`:
  - a free-chain preview frame does **zero** longest-path work, and draws the same atoms, bonds and formula as the commit, which carries the SMILES;
  - an anchored drag frame off an aromatic ring costs exactly one bond-order resolution of the ring, whether it adds 3 carbons or 22. Each frame seeds a fresh copy, so the resolution cache cannot hide the work (review nit, `f662fe5`).
  - Both tests fail on `main`: 783 path steps on a preview frame; 15 and 110 resolution units where the branch costs 5 and 5.

## Platforms

- **Windows 11.** AGENTS.md §14 gauntlet on `f662fe5`:
  - `pnpm lint` ✅.
  - `pnpm vitest run` ✅: 4418 passed, 0 failed, run alone in the machine's one-heavy-job-at-a-time slot.
  - `pnpm build` ✅: packaged Tauri release, `ChemDraft (dev)` MSI and NSIS bundles. Its only warning is the OPSIN runtime missing from this fresh worktree.
  - `git diff --check` ✅, `cargo fmt --check` ✅.
  - clippy `-D warnings` and `cargo test` ✅ in CI on this exact commit, on Windows and macOS (run 38065577327).
  - The headless bench and identity checks are above.
  - In-app on the web build, via the agent bridge: during a drag the stored SMILES is empty while the formula is still derived; release commits 201 × `C`; undo/redo restores the same SMILES.
  - Desktop pass by the Windows session, trusted CDP input, ms per move including the next-frame wait:

    | atoms | 50 | 100 | 150 | 200 | release at 201 |
    |---|---|---|---|---|---|
    | `main` | 65 | 179 | 457 | 997 | 991 |
    | this PR | 37 | 50 | 53 | 62 | 73 |

    No "unavailable" text anywhere on the page during the drag or after release.
- **macOS:** the master session is building `f662fe5` as a packaged Mac app for the owner's hands-on check, which doubles as the macOS check. Pending.

## Known limitations

- **Dragging a chain off an existing atom is broken in the app, on `main` too.** It adds one carbon on press and never grows. Pointer capture lands on the molecule element, and `handleObjectPointerMove` stops propagation without a placement-drag branch, so the drag preview never runs. The Windows session found this and reported it separately. This PR's anchored-drag speedup (one bond-order resolution per frame instead of one per added carbon) is correct and tested headlessly, but users only see it once that bug is fixed.
- A branched tree's path search costs O(leaves × atoms): 40 ms for a random 500-atom tree, paid only on release.

## Gates

- [x] Stress test: the full §14 gauntlet, bench, identity checks, and drag/undo/redo/save→reopen, all on `f662fe5` (see Platforms and the results comments)
- [ ] Owner hands-on check on a launched build of the final commit
- [x] Review: claude-fable `fable-pr81-20261010` APPROVE WITH NITS (no correctness findings); nits fixed in `f662fe5`; scoped re-review `fable-pr81-rereview-20261010` APPROVE
- [ ] macOS check: needed; the master session arranges it

## Squash-merge message

Use this instead of the default. It corrects the timing wording in the message of `e261f99`, which says 2.4 s without saying where that figure came from:

```
Chain drag: linear longest-path search, no SMILES on free-chain frames

Dragging a free carbon chain slowed to a crawl as it grew: 1.6 s per
pointer move at 200 carbons in the original measurement (2.4 s in this
PR's bench on a loaded VM), and about the same again on release.

- longestNativePath ran a breadth-first search between every ordered
  pair of atoms, copying the path at every step. Each start atom now gets
  one BFS with parent pointers; only paths of the winning length reach
  the unchanged comparator, in the old order. In a verified closed forest
  only leaves start a search, so a chain is linear; any other graph,
  rings included, starts from every atom and stays exact.
- The free-chain branch of applyNativeChainTool ignored options.preview.
  Frames now carry an empty (unavailable) structure; the commit derives
  the SMILES once.
- Anchored growth re-resolved bond orders per added carbon; now once per
  frame.

SMILES output is unchanged: identical to main on 723 outputs, and the
new search matches the old one, kept as a test oracle.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2365fdcb492a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.