# Issue

**Title:** adapt for QCSchema v2 and Python v3.14

## Description

Here's an adaptation for QCSchema v2 and Python 3.14. This and  are counterparts. Please let me know of any changes you'd like.

- [x] No change in compatibility with current (~v0.30) and recent QCElemental for Python <3.14 . These will continue to run QCSchema v1 only, and those QCElementals need Pydantic 1.10.17 or 2.x.
- [x] With QCElemental >= v0.50.0rc3 (current available through `-c conda-forge/label/qcelemental_dev`, dftd3-python can run QCSchema v1 or v2 for all Pythons, except 3.14, where Pydantic retired the v1 API. Pydantic >=2.11 will be required (2.12 for Py 3.14). This can be seen in the test_qcschema patterns where 312 runs QCSchema v1 and skips 2, 313 runs both, and 314 runs 2 and skips v1, as illustrated in the dftd4 PR.
- [x] The mac and windows wheel lanes were throwing errors like the below, so I updated to the latest cibuildwheel in the major series. Perhaps associated with 

```
+ Download https://github.com/pypa/get-virtualenv/blob/20.26.4/public/virtualenv.pyz?raw=true to /Users/runner/Library/Caches/cibuildwheel/virtualenv-20.26.4.pyz Traceback (most recent call last):
...
File "/Library/Frameworks/Python.framework/Versions/3.14/lib/python3.14/urllib/request.py", line 611, in http_error_default raise HTTPError(req.full_url, code, msg, hdrs, fp) urllib.error.HTTPError: HTTP Error 429: Too Many Requests Error: Process completed with exit code 1.
```

- [x] Sorry for hacking up the test file so extensively. Python 3.14 not being able to form QCSchema v1 models means I can't just take the v1 models and run `.convert_v(2)` on them to submit to `run_qcschema`. The diff is a little easier to read with whitespace tracking off.
- [x] Associated with  and has been tested locally with QCEngine and Psi4
- [x] I didn't try to impose qcel version constraints in pyproject.toml because qcel is optional, existing envs continue to work, and the new features will appear naturally when v0.50.0 moves beyond pre-release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9b90a0a11c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.