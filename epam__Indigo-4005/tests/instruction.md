# Issue

**Title:** #3990: Draw an S-group without a label as one with the default label

## Description

A superatom read without a label (no M  SMT, no LABEL=, no "name" in KET) keeps an empty label array whose ptr() is null, and the renderer passed it on: a collapsed superatom failed with "string pool: Internal error: size == -1 && str == 0", in a query molecule it ended the process, and an expanded one was captioned "(null)". Indigo writes such files itself: a superatom with an empty name saved to MOL loses its label line.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "In Review"
- [x] code follows product standards
- [x] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f37b835f709a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.