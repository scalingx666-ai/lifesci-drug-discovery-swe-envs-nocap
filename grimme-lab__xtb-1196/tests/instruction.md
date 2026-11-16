# Issue

**Title:** Avoid division by zero in `xtb/gfn0` and `xtb/GFN0-xTB` tests

## Description

This PR fixes `xtb/gfn0` and `xtb/GFN0-xTB` tests which fails with the following stacktrace:

```
Program received signal SIGFPE: Floating-point exception - erroneous arithmetic operation.

Backtrace for this error:
#0  0x7f866aa23e59 in ???
#1  0x7f866aa22e75 in ???
#2  0x7f866804532f in ???
#3  0x5580b9190c2b in __xtb_pbc_MOD_get_realspace_cutoff
	at /home/runner/work/xtb/xtb/src/pbc.f90:62
#4  0x5580b919ea51 in drep_grad
	at /home/runner/work/xtb/xtb/src/peeq_module.f90:675
#5  0x5580b91aad0a in __xtb_peeq_MOD_peeq
	at /home/runner/work/xtb/xtb/src/peeq_module.f90:528
#6  0x5580b8f7ed56 in __xtb_xtb_calculator_MOD_singlepoint
	at /home/runner/work/xtb/xtb/src/xtb/calculator.f90:269
#7  0x5580b8ab8811 in __xtb_prog_main_MOD_xtbmain
	at /home/runner/work/xtb/xtb/src/prog/main.F90:698
#8  0x5580b8abfeec in xtb_prog_primary
	at /home/runner/work/xtb/xtb/src/prog/primary.f90:57
#9  0x5580b8abffc7 in main
	at /home/runner/work/xtb/xtb/src/prog/primary.f90:20
```

Result of `get_realspace_cutoff` is not used in peeq_module and therefore I just deleted this call and problem is gone.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8964b4f21a6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.