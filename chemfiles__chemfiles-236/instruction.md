# Issue

**Title:** Add a cache for sub-selections

## Description

Sub selections (the `name O` in `is_bonded(#1, name O)` where evaluated at every call to is_match, which is once by atom/bond/pairs in the system depending on the selection context.

This PR adds a way for selection element to cache data (more specifically a way to know when to clear the cached data), and uses it for sub selections.

On a test locally using [cfiles](https://github.com/chemfiles/cfiles), this makes the time for hydrogen bonds detection in a small trajectory go from 172s to 60s (almost three time faster!!) for the `name O and is_bonded (#1, name C) and is_bonded (#1, name H)` selection.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d23dd6ff3e8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.