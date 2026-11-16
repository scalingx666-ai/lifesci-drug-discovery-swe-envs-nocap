# Issue

**Title:** Avoid 0-indexed access in search_nci.f90

## Description

Fixes `xtb/docking` test of CMake debug Aarch64 build. 


Stacktrace:
```
   Starting stack search
   Grid points: 14000
At line 603 of file /home/runner/work/xtb/xtb/src/docking/search_nci.f90
Fortran runtime error: Index '0' of dimension 1 of array 'mvec' below lower bound of 1

Error termination. Backtrace:
#0  0xff6faad0d44b in ???
#1  0xff6faad0e277 in ???
#2  0xff6faad0e7cb in ???
#3  0xab162411c01f in __xtb_docking_search_nci_MOD_docking_search
	at /home/runner/work/xtb/xtb/src/docking/search_nci.f90:603
#4  0xab1623f31467 in test_dock_eth_wat_gfn2
	at /home/runner/work/xtb/xtb/test/unit/test_docking.f90:180
#5  0xab1623ec9d4f in run_unittest
	at /home/runner/work/xtb/xtb/test/unit/main.f90:169
#6  0xab1623eca1e7 in run_testsuite
	at /home/runner/work/xtb/xtb/test/unit/main.f90:149
#7  0xab1623ec8c27 in tester
	at /home/runner/work/xtb/xtb/test/unit/main.f90:103
#8  0xab1623eca2cf in main
	at /home/runner/work/xtb/xtb/test/unit/main.f90:20
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ae3b5568795`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.