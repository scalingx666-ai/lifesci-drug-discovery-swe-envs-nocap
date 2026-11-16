# Issue

**Title:** Add SAIR dataset for GNN training

## Description

Reads SAIR ModelCIF directly rather than converting to MOL2. The graph builder consumes ParsedMolecule objects, not files, so converting ~900k complexes to 2.7M MOL2 files would cost days of Open Babel subprocess time and buy nothing. Protein typing uses the residue-aware SYBYL table; ligand bond orders come from the parquet SMILES, which is more reliable than perceiving them from a predicted geometry.

Validated on entry 1000: the 28 CIF ligand atoms match the SMILES template, and typing resolves to C.ar/C.2/N.2/O.2 rather than the all-C.3 an element-only fallback produces. That distinction is what separated r = 0.82 from r = 0.17 when the same model was fed PDB-derived input.

Three properties of the data drive the design. SAIR CIFs carry no hydrogens, so models trained here are heavy-atom models and are not interchangeable with the ULVSH and PDBbind models. There are ~8.4 measurements per structure, aggregated to a median per entry_id, since one geometry cannot carry several labels. Measurements sitting exactly on the assay floor (pIC50 4.0) are dropped by default: they are censored rather than observed, and ULVSH showed what happens when a censored floor is trained on as a point value.

Splitting is by protein sequence. A random split over a million complexes drawn from far fewer targets puts the same protein in train and test, and the reported correlation then largely measures memorised targets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e9d4498d166`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.