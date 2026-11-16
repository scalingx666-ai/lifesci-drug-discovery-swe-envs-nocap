# Issue

**Title:** add 2D Pharmacophore fingerprints

## Description

fixes 

This PR adds a MolToPharmacophore2DFP pipeline element for computing 2D pharmacophore fingerprints. The elements has the following features:
- Fully configurable feature definitions and fingerprint defintion, like binning through the constructor
- Preconfiguration can be used, like `"gobbi"`
- Follows MolPipelines interface conventions   
- JSON/joblib serializable
- Supports various return types: `np.ndarray`, `sparse.csr_matrix`, `ExplicitBitVect` and `IntSparseIntVect`

In addition, there were inconsistencies with the `return_as` argument of `MolToFingerprintPipelineElement`. The option `"explicit_bit_vect"` was removed in favor of `"rdkit"` since given the configuration options of the different fingerprints a concrete return type like `ExplicitBitVect` can't be garantueed, e.g. because of counted/binary fingerprints. Instead, now with `"rdkit"` the native RDKit represenation of the fingerprint is returned, which depends on the fingerprint method and whether it's a counted or binary fingerprint, for example  `ExplicitBitVect` vs `IntSparseIntVect`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30c2a33421bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.