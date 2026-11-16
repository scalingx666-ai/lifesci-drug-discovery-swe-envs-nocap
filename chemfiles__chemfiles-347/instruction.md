# Issue

**Title:** Do not update Topology angles/dihedrals on bond access

## Description

This makes reading 3j3q.mmtf file 30% faster, and completely remove MMTFFormat::apply_symmetry from a callgrind profile.

There is no need to update the angles if we are only accessing the bonds (which are always up to date).

Thanks @sguionni for reporting that reading this was slow!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3ca7206059d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.