# Issue

**Title:** Badges, Dependencies, and Py27 (oh my)

## Description

Second wave of cleanups from initial feedback:

* Drops support for Python 2.7 with links and reasons on primary README ()
* Makes the Dependency selection much more friendly ()
  ```
  Select dependency_source:
  1 - Prefer conda-forge over the default anaconda channel with pip fallback
  2 - Prefer default anaconda channel with pip fallback
  3 - Dependencies from pip only (no conda)
  Choose from 1, 2, 3 [1]:
  ```
* Fills in more instructions on what to do next (Progress on #9)
* Adds Windows support toggle and deletes files if not chosen (Based on suggestion in #19)
* Adds badges, more badges, MORE BADGES okay stop badges ()
* Fixed a bug where the hidden files (`.*`) where not added by `git` 

Feedback welcome!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `843d19474e73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.