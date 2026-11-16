# Issue

**Title:** Fix ubuntu-latest CI and introduce Arm validation

## Description

Broken tests with CMake + Debug, so these build are currently disabled:
on x86_64:
```
The following tests FAILED:
	 57 - tblite/gfn1-xtb (NUMERICAL)
	 88 - xtb/docking (NUMERICAL)
	 90 - xtb/gfn0 (NUMERICAL)
	 91 - xtb/gfn1 (NUMERICAL)
	 94 - xtb/hessian (Failed)
	 95 - xtb/iff (NUMERICAL)
	101 - xtb/peeq (Failed)
	106 - xtb/vertical (Failed)
	116 - xtb/GFN0-xTB (NUMERICAL)
```
on Aarch64:
```
The following tests FAILED:
	 88 - xtb/docking (Failed)
	 93 - xtb/gfnff (Failed)
	 94 - xtb/hessian (Failed)
	106 - xtb/vertical (Failed)
	107 - xtb/wsc (Failed)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3cfd38d6753`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.