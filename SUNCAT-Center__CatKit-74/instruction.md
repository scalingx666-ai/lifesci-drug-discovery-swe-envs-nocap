# Issue

**Title:** Cathub update

## Description

* general cleanup 
* cli: better print of tables + better help strings
* postgresql: methods for updating and deleting reactions on the server.
* postgresql: make row limits optional + write pub_id directly to systems table. 
* query: small query changes + faster writing of structures

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ac0779b0f1c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.