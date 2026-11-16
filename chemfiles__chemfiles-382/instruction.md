# Issue

**Title:** fix(mmtf): chain and group indices are consecutive

## Description

I have not read the full spec but these examples [[1]](https://github.com/rcsb/mmtf/blob/master/spec.md#chainspermodel) [[2]](https://github.com/rcsb/mmtf/blob/master/spec.md#groupsperchain) indicate that chains and groups are indexed consecutively. This is also aparent when looking at [`StructureData::print`](https://github.com/rcsb/mmtf-cpp/blob/ee4b855cf53b4a3ee7a40cc62d57195875fe84a5/include/mmtf/structure_data.hpp#L1028). When skipping, chemfiles wrongfully starts at 0 again for every model.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d536387aa33c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.