# Issue

**Title:** Modernise build system

## Description

Now that we have dropped some older Python versions: use pyproject.toml and a recent setuptools.

This supports other nice modern technologies:
- isolated builds with properly-specified dependencies
- uv
- configuring additional tools such as linters in one place

The selection/capability of metadata fields has also slightly improved over time.

I'd like to merge this before making a 2.4.0 release

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3635fb392802`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.