# Issue

**Title:** Mordred Lipinski

## Description

## Changes

Add Mordred Lipinski descriptors

Adding `Lipinski` / `GhoseFilter` needed LogP, molar refractivity, exact MW, atom
count and the H-bond donor/acceptor counts — all of which `calc_rdkit_2d` already
computed for `SLogP`, `SMR`, `MW`, `AMW`, `nHBAcc` and `nHBDon`.

Rather than recompute them (`Crippen.MolLogP`/`MolMR` and `CalcNumHBA`/`CalcNumHBD`
are SMARTS-matching passes over the whole molecule), they moved into
`MolecularProperties`, a shared dependency built once per molecule in
`calculator.compute()` and passed to both modules — the same pattern as
`AtomicProperties`, `DistanceMatrix` and `RingSets`.

So `calc_rdkit_2d` takes a third argument and reads those six values off it instead
of calling RDKit itself; `_average_exact_mol_wt` reduces to a division, still wrapped
in `safe_value` for the empty-molecule case. No descriptor values change — verified
against mordred-community.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d5290dc1e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.