# Issue

**Title:** Fix that BoFire is not working without cyipopt

## Description

@jkeupp reported that the current BoFire version on pypi is not working when cyipopt is not installed. The reason is that cyipopt is used in the instantiation of I-optimal criterion and that we do not guard the import there. This PR fixes it and adds a test where we just install the optimization package of BoFire to prevent it in the future.

After having this in, we should also make a release.

cc: @Osburg @dlinzner-bcs @bertiqwerty

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c91da4c8167`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.