# Issue

**Title:** Separate environment for T018

## Description

A separate environment is added to T018:
- all dependencies are pinned exactly (i.e., `major.minor.patch`) to their latest working versions.
- For all dependencies except `pandas`, this version is the latest version resolved by `conda`.
- `pandas` is pinned to `2.1.4` (i.e., the latest `2.1.x` version) instead of `2.2.0` (i.e., the latest resolvable version) because the latest `RDKit` version (i.e., `2023.09.5`) does not work with `pandas 2.2.0`. I fixed the issue in `RDKit` and submitted a . Once a new `RDKit` release with this fix is released, we can update the `pandas` dependency to the latest version.

In addition, the following changes are applied to the `utils` subpackage in T018 (i.e., the backend of T018):
- `DeprecationWarning` and `FutureWarning` notifications are suppressed to not show up in notebook outputs. These are all due to our dependencies not having updated their codes to adopt to newer versions of their own dependencies.
- The `opencadd` dependency is removed, and replaced with `MDAnalysis`: The utility we used in OpenCADD (i.e. `opencadd.structure.core.Structure`) is just a wrapper around `MDAnalysis.Universe` with no added functionalities. Therefore, the `opencadd` dependency was removed and `MDAnalysis` was used directly instead, in order to avoid version pinning problems in `opencadd`.

Lastly the notebook is rerun:
- This caused some slight (numerical) changes (e.g. calculated binding affinities by `smina`, calculated interactions by `plip`) in the outputs, which were mentioned in the text. Therefore, the text was also edited to reflect the new results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4aacca53f172`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.