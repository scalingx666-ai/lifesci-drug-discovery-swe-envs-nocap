# Issue

**Title:** Bump SHAP to fix Audit

## Description

There seems to be a [dependency chain](https://github.com/emdgroup/baybe/actions/runs/21054885037/job/61283563193#step:4:203) involving `shap==0.46.0` causing that the `pip-audit` environment cannot be built in `Py3.12` and `Py3.13`.

This can be fixed by slightly bumping the requirement to `>=0.47.0`, which is fine since shap already has even higher versions.

This is not related to the audit fails that are caused by the vulnerability, which also crash `Py3.10` and `Py3.11`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `296a703a14a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.