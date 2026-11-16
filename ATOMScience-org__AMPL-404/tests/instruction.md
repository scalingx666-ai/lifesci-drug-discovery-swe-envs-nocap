# Issue

**Title:** Update ci pipeline

## Description

- Changed to pin a specific ubuntu version rather than ubuntu:latest to avoid buggy release(s)
- Updated requirements, to use `--find-links` instead of `--extra-index-ur`l to avoid Dependabot think it’s a PyPI-style index and cause the authentication failure (the link doesn't require authentication when access) to avoid the dependabot issue like [this](https://github.com/ATOMScience-org/AMPL/actions/runs/15353946434). Will need to test, verify in master branch.
⁠
```
Dependabot encountered '1' error(s) during execution, please check the logs for more details.
+----------------------------------------------------------------------------------------------------------+
|                                      Dependencies failed to update                                       |
+------------+---------------------------------------+-----------------------------------------------------+
| Dependency | Error Type                            | Error Details                                       |
+------------+---------------------------------------+-----------------------------------------------------+
| torch      | private_source_authentication_failure | {                                                   |
|            |                                       |   "source": "https://data.dgl.ai/wheels/repo.html/" |
|            |                                       | }                                                   |
+------------+---------------------------------------+-----------------------------------------------------+
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0e8f39420b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.