# Issue

**Title:** fix: Minimum Python version update + results folder .gitignore

## Description

Tiny fix/tidy commit

### Problem

I went to build this on Python 3.12, which failed due to some breaking change introduced in it compared to the dependency versions within pyproject.toml. Downgraded to 3.9 in accordance with the pyproject.toml requirement. Failed due to "numba==0.61.0" only being available on Python 3.10 and later: https://pypi.org/project/numba/0.61.0/

Slight tweak, while validating changes to the repo on the provided examples, the result outputs clutter the diff. Given they all follow the "boltz_results_..." format, might want to add that into the .gitignore.

### Solution

Downgrading the dependencies is usually more risky than just bumping the minimum Python version if they all are compatible with the newer Python version.

Added a new section for boltz outputs to the .gitignore "boltz_results_*/". Given this is just a tiny quality of life change, I can see an argument for/against it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f515995cfca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.