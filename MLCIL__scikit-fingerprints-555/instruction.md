# Issue

**Title:** Add Zagreb Index and Wiener Index to Mordred

## Description

**Descriptor Function Enhancements:**

* Refactored `zagreb_index_m1` and `zagreb_index_m2` in `skfp/descriptors/topological.py` to accept optional precomputed degree vectors and a `modified` flag, enabling calculation of both standard and modified Zagreb indices. The functions now return `np.nan` when the modified index is requested and the molecule contains atoms with zero degree, and raise fewer errors by handling floating point and division issues internally. [[1]](diffhunk://#diff-34f006d76fdb9cd89ef43d04be6e7be207811447a1da339973e1ff1557ae9bcbL614-R618) [[2]](diffhunk://#diff-34f006d76fdb9cd89ef43d04be6e7be207811447a1da339973e1ff1557ae9bcbR631-R643) [[3]](diffhunk://#diff-34f006d76fdb9cd89ef43d04be6e7be207811447a1da339973e1ff1557ae9bcbL642-R680) [[4]](diffhunk://#diff-34f006d76fdb9cd89ef43d04be6e7be207811447a1da339973e1ff1557ae9bcbR704-R716) [[5]](diffhunk://#diff-34f006d76fdb9cd89ef43d04be6e7be207811447a1da339973e1ff1557ae9bcbL684-R757)

**New Descriptor Modules:**

* Added new modules `skfp/fingerprints/_new_mordred/descriptors/wiener_index.py` and `skfp/fingerprints/_new_mordred/descriptors/zagreb_index.py` that provide functions to calculate the Wiener and both standard/modified Zagreb indices, integrating with the new matrix utilities and returning results in the expected Mordred-like format. [[1]](diffhunk://#diff-e6f4a21d732e5486d12682f276bfd16683e6c52e6b6561cb2c2b30e202e46e4bR1-R27) [[2]](diffhunk://#diff-2bc45b44edbcb03665e7bc0839a70eabb3078a4d9e2119de9cf122308d085f90R1-R37)

**Integration with Fingerprint Calculation:**

* Updated `skfp/fingerprints/_new_mordred/calculator.py` to import and use the new Wiener and Zagreb index descriptor functions. The calculator now computes and includes these descriptors using the appropriate distance and adjacency matrices. [[1]](diffhunk://#diff-9a19a59b9214faf497fc2bec2e687b649a8d7d3d5ca74b6a26f3fae8ff88f346L13-R25) [[2]](diffhunk://#diff-9a19a59b9214faf497fc2bec2e687b649a8d7d3d5ca74b6a26f3fae8ff88f346R50-R56)

**Matrix Utility Improvements:**

* Modified the `degree` property of `AdjacencyMatrix` in `skfp/fingerprints/_new_mordred/utils/graph_matrix.py` to always return a float array, ensuring compatibility with the updated descriptor functions.

**Testing:**

* Added tests in `tests/descriptors/topological.py` to verify that the modified Zagreb indices return `np.nan` for molecules containing atoms with zero valence, improving coverage of edge cases.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8028c9c36bca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.