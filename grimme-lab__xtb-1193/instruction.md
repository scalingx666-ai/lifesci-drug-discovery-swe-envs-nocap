# Issue

**Title:** Remove symbol length variable

## Description

Alternative approach to #1172 

This PR removes symbolLength variable from xtb_mctc_symbols module and changes behaviour to use dynamically sized strings.

Fixed the following error for CMake debug build on Aarch64 (as well as #1172):
```
At line 243 of file /home/runner/work/xtb/xtb/src/mctc/symbols.f90
Fortran runtime error: Actual string length does not match the declared one for dummy argument 'symbol' (1/4)

Error termination. Backtrace:
#0  0xff0d6362d44b in ???
#1  0xff0d6362e277 in ???
#2  0xff0d6362e7cb in ???
#3  0xab6d17e20527 in __xtb_mctc_symbols_MOD_getidentitysymbol
	at /home/runner/work/xtb/xtb/src/mctc/symbols.f90:243
#4  0xab6d17fb8c17 in __xtb_type_molecule_MOD_initmolecule
	at /home/runner/work/xtb/xtb/src/type/molecule.f90:263
#5  0xab6d17fb5bf7 in __xtb_type_molecule_MOD_initmoleculesymbols
	at /home/runner/work/xtb/xtb/src/type/molecule.f90:330
#6  0xab6d17ab537f in test_gfn1_hessian
	at /home/runner/work/xtb/xtb/test/unit/test_hessian.f90:116
#7  0xab6d179c9d4f in run_unittest
	at /home/runner/work/xtb/xtb/test/unit/main.f90:169
#8  0xab6d179ca1e7 in run_testsuite
	at /home/runner/work/xtb/xtb/test/unit/main.f90:149
#9  0xab6d179c8c27 in tester
	at /home/runner/work/xtb/xtb/test/unit/main.f90:103
#10  0xab6d179ca2cf in main
	at /home/runner/work/xtb/xtb/test/unit/main.f90:20
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a93fd869a7be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.