# Issue

**Title:** v4.1.0: replace pose "search" with a real conformational search

## Description

## Summary

The docking algorithms did not search. `_generate_crystal_guided_pose` placed the input conformer within ~1 Å of the box centre with a rotation drawn from N(0, 10°) about whatever orientation the ligand file happened to have, and ligand torsions were never varied.

Compounding this, all three scoring call sites passed `(coords, receptor)` without the ligand, and `VinaScoring.calculate_binding_energy` returns `0.0` when `ligand_mol is None` — so with the default `--scoring vina`, **every pose scored exactly 0.0** and ranking was driven entirely by a bonus for proximity to a reference point. That reference defaulted to a hardcoded ligand coordinate, `[129.249, 120.21, 145.249]`, which captured any docking box placed within 10 Å of it.

Net effect: poses were ranked by distance from the box centre. This reproduces the published failure signature exactly — centroid roughly correct, orientation random, so RMSD scales with ligand size (glycosidases 4.4 Å, proteases 15.3 Å) and % within 2 Å is ~0 for every protein family.

## New search (`pandadock/docking/search/`)

- **torsion_tree** — articulated ligand model; every rotatable bond is a search DOF, rooted on the largest rigid fragment, amides and conjugated bonds frozen
- **grid_maps** — per-atom-type Vina affinity grids, so pose scoring is a trilinear lookup rather than a full pairwise sum
- **objective** — fully analytic gradients. Translation is the atom-gradient sum, torsions come from the rotational velocity of each moving subtree, and orientation maps the accumulated torque through the derivative of the SO(3) exponential map. Verified against finite differences at 2e-10 relative error.
- **monte_carlo** — independent runs, uniform SO(3) and uniform box initialisation, L-BFGS relaxation each step, Metropolis acceptance, RMSD clustering
- **rotations** — numpy Rodrigues and cross products. scipy's `Rotation` objects and `np.cross` were 67% of runtime; replacing them gave a 2.5× speedup.

Sampling scales with ligand flexibility. On a 13-DOF ligand, 8 runs converged 11 kcal/mol above the global minimum (12.7 Å) while 24 runs found it (1.0 Å), so a flat default is not defensible.

## Removed rather than patched

- `CrystalGuidedDocker` raises on construction. It restricted sampling to the neighbourhood of a reference pose and rewarded proximity to it, which invalidates any benchmark it appears in.
- `MonteCarloDocker`, `GeneticAlgorithmDocker` and `EnhancedHierarchicalDocker` are now aliases of `PandaCoreDocker`. Their distinctive code was unreachable (the 3-stage pipeline sat after an unconditional `return`) or non-functional (the GA never encoded torsions as genes).

## Benchmarking

`.gitignore` previously ignored `benchmarking/` wholesale, which is why every script its README documents was absent from the repository.

- `preprocessing/complex_splitter.py` resolves HETATM codes against the PDB Chemical Component Dictionary. Selecting the largest non-water HETATM picks modified residues (MSE, SEP, TPO), N-glycans (NAG) and membrane lipids (CLR, PCW).
- `redock_benchmark.py` reports symmetry-corrected RMSD without superposition, separating top-1 from best-of-N.
- `validate_prepared.py` checks for ligand leakage into the receptor before compute is spent.
- `analyze_redock.py` / `make_report.py` split search failures from ranking failures and emit publication tables.

Default box padding is 5 Å. On 12 confirmed search failures this reduced median best-of-N RMSD from 5.11 to 2.48 Å, beating exhaustiveness 48 at 8 Å padding (4.74 Å) while running faster.

## Interim results

A 815-complex redocking run over 14 protein families is in progress. First 179 complexes: median top-1 2.54 Å, top-1 ≤2 Å 43%, **best-of-N ≤2 Å 93%**, with 50% of complexes misranked — the search finds a sub-2 Å pose nine times in ten and the empirical scoring function ranks it below a wrong one half the time. Full tables to follow.

## Release and CI

- Version bumped to 4.1.0 and single-sourced from `pandadock.__version__`. Four places declared versions independently and three had drifted (`pandadock.docking` 3.0.0, `pandadock.gnn` 1.0.0, Sphinx conf 4.0.0).
- Packaging metadata moved to `pyproject.toml` (PEP 621); `setup.py` is a shim. Both artifacts pass `twine check`.
- Publish workflow: triggered on both `created` and `published`, so the job ran twice and the second upload failed the release; added a tag/version consistency guard and `twine check`.
- CI installs RDKit and BioPython. It previously did not, and `test_search.py`'s module-level import aborted collection so the 14 unrelated tests never ran.

## Note on comparability

Pose-accuracy figures from v4.0.2 and earlier measure the proximity bias and should not be compared against this branch. Affinity results from PandaDock-GNN are unaffected: the GNN was trained and evaluated on crystal poses, independently of this code path.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `adfa6d6b3d1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.