# Issue

**Title:** Fix bad alignment of terminal vertices with one placer id.

## Description

Related Issues: #424 
Requested Reviewers: @lukasturcani

The user will experience no API change. The result is better alignment of terminal building blocks in linear polymers when the building blocks have one placer id. Ideally, the user should not have to set the placer ids to get good alignment.

This change avoids the use of the UnaligningVertex when a building block has one placer id but is also a terminal vertex.

The position matrices of the polymers must change in some cases - at least test `polymer_linear3` changes.

My process of fixing is described in the associated issue.

Update: currently, the tests will fail due to the structure of  `polymer_linear3`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb22d0ce59fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.