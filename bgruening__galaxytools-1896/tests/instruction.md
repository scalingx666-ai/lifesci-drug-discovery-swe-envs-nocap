# Issue

**Title:** Update 3Dtrees standardization wrapper to 1.2.1

## Description

## Summary
- bump the 3Dtrees standardization wrapper container version from `1.2.0` to `1.2.1`
- increment the Galaxy wrapper suffix from `+galaxy0` to `+galaxy1`
- update metadata JSON assertions to match the scalar, pretty-printed metadata emitted by the new container

## Validation
- `xmllint --noout tools/3dtrees_standardization/standard.xml`
- `planemo lint tools/3dtrees_standardization/standard.xml`

This branch was reset to current `bgruening/galaxytools:master` before applying the wrapper change and contains one commit on top of upstream master.

Note: `planemo lint` completed successfully and reported `ToolVersionValid: 1.2.1+galaxy1`. The local environment printed an optional `h5py`/NumPy binary compatibility warning while importing Galaxy assertion modules before linting.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1462deb15898`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.