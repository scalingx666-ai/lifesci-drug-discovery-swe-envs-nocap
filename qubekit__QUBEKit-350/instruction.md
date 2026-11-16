# Issue

**Title:** Fix tip4p v-site weights in openmm

## Description

## Description
This PR fixes the plugin local coordinate site handler to use the correct v-site weights for water models. This hard codes the weights to give a divalent lone pair type site and is only suitable for 4 point models. 

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] Check normal sites are correctly placed
  - [x] Check water sites are correctly placed

## Questions
- [x] Do we want a more general interface to support any combination of weights? 

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d422575dfdd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.