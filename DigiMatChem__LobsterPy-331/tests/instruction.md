# Issue

**Title:** Update calc quality and fingerprints usage

## Description

# Changes

1. DosFingerprints usage has been adapted to accommodate latest pymatgen changes
2. pin `pymatgen>=2024.9.10`
3. Remove redundant namedtuple instance of `DosFingerprints` from Lobsterpy (Has been moved to pymatgen in recent changes. See )
4. Drop python 3.9 support > pymatgen dropped it in its latest release
5. Fix coverage not being uploaded. (issue : https://github.com/actions/upload-artifact?tab=readme-ov-file#breaking-changes , explicitly ignoring hidden files in uploads)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b722b1644ed3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.