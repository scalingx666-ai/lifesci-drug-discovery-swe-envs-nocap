# Issue

**Title:** Add `latimer_munro` path option

## Description

Code to add CLI option to `sumo-kgen` to use the Latimer & Munro method for generating high-symmetry k-point paths (paper here: https://www.nature.com/articles/s41524-020-00383-7, and pymatgen docs here: https://pymatgen.org/pymatgen.symmetry.kpath.html#pymatgen.symmetry.kpath.KPathLatimerMunro).

Tested and seems to work fine (tested with zero-weighted hybrid kpoints method, and with purposefully-incorrect (conventional) `POSCAR`). Label conventions slightly odd as per their paper. 

`sumo-kgen -y --latimer_munro` gives:
```bash
Structure information:
	Space group number: 36
	International symbol: Cmc2_1
	Lattice type: orthorhombic

k-point path:
	q -> e -> c -> q_{1} -> Γ -> f -> q -> c -> f -> b -> q | b -> d_{1} -> Γ -> c | Γ -> b | Γ -> d -> q_{1} | d -> a -> e | a -> Γ

k-points:
	d: 0.2724618722651559 0.2724618722651558 0.0
	d_{1}: -0.27246187226515584 0.7275381277348444 0.0
	a: 2.7755575615628914e-17 0.5000000000000001 0.0
	b: -0.5 0.5000000000000001 1.3877787807814457e-17
	Γ: 0 0 0
	f: -0.5 0.5000000000000001 0.4999999999999992
	q: -0.27246187226515584 0.7275381277348444 0.5
	e: 0.0 0.5000000000000001 0.5
	q_{1}: 0.27246187226515584 0.27246187226515584 0.5
	c: 5.551115123125783e-17 7.401486830834377e-17 0.4999999999999993

k-point label indices:
	q: 1
	e: 26
	c: 40
	q_{1}: 65
	Γ: 93
	f: 141
	q: 162
	c: 193
	f: 239
	b: 251
	q: 275
	b: 276
	d_{1}: 297
	Γ: 328
	c: 340
	Γ: 341
	b: 387
	Γ: 388
	d: 413
	q_{1}: 425
	d: 426
	a: 451
	e: 463
	a: 464
	Γ: 478

WARNING: The input structure does not match the expected standard
primitive symmetry, the path may be incorrect! Use at your own risk.

The correct symmetry primitive structure has been saved as POSCAR_prim.```
as expected (with correct primitive structure in `POSCAR_prim`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e885844de07e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.