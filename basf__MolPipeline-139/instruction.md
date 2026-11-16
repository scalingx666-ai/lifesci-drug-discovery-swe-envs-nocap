# Issue

**Title:** Fix bug: ElementFilter: roundtrip from recursive_to_json to recursive_from_json messes up atom types

## Description

**Reason**
This PR solves the bug described in this .  

**Solution:**
Cast keys to int.

ToDos:
- [x] Create unittest to recreate bug
- [x] Fix bug

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84d09fdbdd2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.