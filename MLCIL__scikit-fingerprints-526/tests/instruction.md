# Issue

**Title:** Add multithreading to MolFromSDFTransformer [Issue 467]

## Description

This PR adds parallel SDF reading support in MolFromSDFTransformer when n_jobs > 1, using RDKit's MultithreadedSDMolSupplier (requires RDKit >= 2025.09.1).

Molecules loaded in parallel are sorted by record_id to preserve the original file order, and None results are filtered out to guard against nondeterministic duplicates from the multithreaded supplier.

When the installed RDKit version is too old or raw SDF text is passed instead of a file path, a warning is issued and loading falls back to sequential SDMolSupplier.

Additional changes:
- explicit RDKit version check via _get_rdkit_version() utility,
- parallel logic extracted into _read_sdf_file_parallel() for readability,
- tests covering parallel loading, order preservation, and version fallback.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70bcf92dfb5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.