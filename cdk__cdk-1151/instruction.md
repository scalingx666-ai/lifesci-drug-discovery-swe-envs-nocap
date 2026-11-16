# Issue

**Title:** Copy charges of original atoms when creating functional group atoms and add test subroutine for correct charges

## Description

I noticed that charges were disappearing when extracting functional groups. A bit of digging made me realise that were are not correctly testing for it, the Vento-Foggia isomorphism check is not enough. This PR adds the copying of atomic charges and also a test subroutine for asserting that charges are not lost anymore.

@johnmay and @egonw what is the interplay of charge and formal charge? Setting the formal charge seems to also set the charge but not vice-versa. Is this observation/behaviour correct and should I therefore copy both as I am currently doing?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0750f7b09a8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.