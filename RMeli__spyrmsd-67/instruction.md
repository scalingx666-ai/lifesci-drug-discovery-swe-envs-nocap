# Issue

**Title:** Try to install package before deployment

## Description

## Description

This PR is an attempt to fix issue #54 . The same error described in #54 was obtained locally with `flit==3.0.0`, which is a version that used to work. The `unknown+0` version was picked up at first, after fetching the new tag from the repository. However, installing `spyrmsd` with
```bash
pip install -e .
``` 
seemed to fix the issue.

This PR adds installation of `spyrmsd` before `flit build`, which hopefully will allow `flit` to pick up the correct version from the tag.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb121aff9fcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.