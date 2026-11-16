# Issue

**Title:** Containerize mofid package

## Description

Hello @arosen93 I finished the Docker and singularity experiments! Our setup requirements are now much shorter (though there might be cluster-specific instructions users need to follow to get set up with singularity on their HPC environment).

The link to the .sif file in the README points to the future location for a tagged GitHub release. In the meantime, I've published a [pre-release](https://github.com/snurr-group/mofid/releases/tag/draft-docker) file (and will delete and rerelease once we finalize the PR).

I've only been able to test out the code on my laptop so far. Would you be able to test on HPC? Any other feedback would be appreciated, too! Thanks for your help.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc53fe784006`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.