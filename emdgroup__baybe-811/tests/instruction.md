# Issue

**Title:** Fix Dependabot Config

## Description

- Remove unsupported `semver-major/minor/patch-days` sub-keys, which are not applicable to the github-actions ecosystem (actions don't use SemVer)
- Increase default-days from 7 to 14 to provide a longer stabilization window against potential supply chain attacks
- Group updates into a single PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `964157ffe0ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.