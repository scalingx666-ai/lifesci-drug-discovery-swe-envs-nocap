# Issue

**Title:** T008: Use GraphQL for PDB ligand search #248

## Description

## Description
We are searching for ligands in PDB files in T008. @BJWiley233 reported in #248 that our `pypdb`-based solution misses the ligand 92P in PDB ID 3ZLS and suggested a GraphQL-based query instead. 

## Todos
- [x] Replace `pypdb`-based with GraphQL-based ligand search in RCSB.
- [x] Move code bits in `get_ligands` to functions `_fetch_pdb_nonpolymer_info` and `_fetch_ligand_expo_info` for easier readability of the query.
- [x] Revert CI change 

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4399260ea61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.