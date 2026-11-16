# Issue

**Title:** adapt for QCSchema v2 and Python v3.14

## Description

Here's an adaptation for QCSchema v2 and to finally allow Python 3.14. It shouldn't break any existing working environments. Please let me know if you'd like any changes. (It's a little easier to read with whitespace diff suppressed.)

- [x] removed an old `pkg_resources` that was failing py312 and replaced with a setuptools call.
- [x] Like for dftd3, there's no change in deps for py<=312, but I added installing a pre-release QCElemental for 313 and 314. Tests are parametrized for QCSchema v1 and v2, and both the qcschema.py module and the tests are tolerant to whatever qcel is available. So, as shown below, py314 runs QCSchema v2 only (pydantic doesn't allow v1 to be instantiated) and skips v1, py313 runs both, and py312- runs only v1 and skips v2.

py312
```
test_qcschema.py::test_energy_r2scan_d4[1] <- ../../../../../opt/hostedtoolcache/Python/3.12.13/x64/lib/python3.12/site-packages/dftd4/test_qcschema.py PASSED [ 52%]
test_qcschema.py::test_energy_r2scan_d4[2] <- ../../../../../opt/hostedtoolcache/Python/3.12.13/x64/lib/python3.12/site-packages/dftd4/test_qcschema.py SKIPPED [ 54%]
test_qcschema.py::test_energy_r2scan_d4s[1] <- ../../../../../opt/hostedtoolcache/Python/3.12.13/x64/lib/python3.12/site-packages/dftd4/test_qcschema.py PASSED [ 56%]
test_qcschema.py::test_energy_r2scan_d4s[2] <- ../../../../../opt/hostedtoolcache/Python/3.12.13/x64/lib/python3.12/site-packages/dftd4/test_qcschema.py SKIPPED [ 58%]
```

py313
```
test_qcschema.py::test_energy_r2scan_d4[1] <- ../../../../../opt/hostedtoolcache/Python/3.13.12/x64/lib/python3.13/site-packages/dftd4/test_qcschema.py PASSED [ 52%]
test_qcschema.py::test_energy_r2scan_d4[2] <- ../../../../../opt/hostedtoolcache/Python/3.13.12/x64/lib/python3.13/site-packages/dftd4/test_qcschema.py PASSED [ 54%]
test_qcschema.py::test_energy_r2scan_d4s[1] <- ../../../../../opt/hostedtoolcache/Python/3.13.12/x64/lib/python3.13/site-packages/dftd4/test_qcschema.py PASSED [ 56%]
test_qcschema.py::test_energy_r2scan_d4s[2] <- ../../../../../opt/hostedtoolcache/Python/3.13.12/x64/lib/python3.13/site-packages/dftd4/test_qcschema.py PASSED [ 58%]
```

py314
```
test_qcschema.py::test_energy_r2scan_d4[1] <- ../../../../../opt/hostedtoolcache/Python/3.14.3/x64/lib/python3.14/site-packages/dftd4/test_qcschema.py SKIPPED [ 52%]
test_qcschema.py::test_energy_r2scan_d4[2] <- ../../../../../opt/hostedtoolcache/Python/3.14.3/x64/lib/python3.14/site-packages/dftd4/test_qcschema.py PASSED [ 54%]
test_qcschema.py::test_energy_r2scan_d4s[1] <- ../../../../../opt/hostedtoolcache/Python/3.14.3/x64/lib/python3.14/site-packages/dftd4/test_qcschema.py SKIPPED [ 56%]
test_qcschema.py::test_energy_r2scan_d4s[2] <- ../../../../../opt/hostedtoolcache/Python/3.14.3/x64/lib/python3.14/site-packages/dftd4/test_qcschema.py PASSED [ 58%]
```

- [x] There's a conda-forge PR () based on this branch to ensure packaging is working, and it's been tested locally with QCEngine and Psi4.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32933e61e68d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.