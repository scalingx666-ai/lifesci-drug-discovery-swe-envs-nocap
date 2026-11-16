# Issue

**Title:** Add node names instead of node IDs to networkx graph

## Description

**Problem:** Each node id (`x_id` and `y_id`) is node type specific. For example, a node ID of "1" for a disease node is different from a node ID of "1" for a gene/protein node. This is (likely) not an issue for training a GNN. However, it can be an issue if users want to do network analysis on PrimeKG because the current `to_nx()` function does not consider node type.

**Solution:** Instead of adding pairs of node IDs as edges, add pairs of node names because they are unique.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80acefc64d5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.