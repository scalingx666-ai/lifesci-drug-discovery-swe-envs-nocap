# Issue

**Title:** Improve string parsing in reaction.delta method

## Description

Previously the `reaction.delta` method would return the potential energy of the transition state when supplying `"G ddagger" ` or `"G double dagger"`. This behavior was unexpected.

After the change synonyms "ddagger" and "double dagger" can also be used with free energy. 


- Improved string parsing that all synonyms for double dagger can be used
- Added tests that determine if right energy is returned

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67ed012fc350`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.