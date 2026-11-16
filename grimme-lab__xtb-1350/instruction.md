# Issue

**Title:** Reduce OpenMP stack usage for GFN2 optimizations

## Description

Now, GFN1 and GFN2 can be run with `OMP_STACKSIZE=36kb` for systems with 300+ atoms.

Tested on input from #1338.
Tested commands:
```
OMP_STACKSIZE=36k OMP_NUM_THREADS=4 OMP_PLACES=24-27 ../xtb -P 4 --gfn 2 test.xyz  --opt --alpb water
OMP_STACKSIZE=36k OMP_NUM_THREADS=4 OMP_PLACES=24-27 ../xtb -P 4 --gfn 1 test.xyz  --opt --alpb water
OMP_STACKSIZE=36k OMP_NUM_THREADS=4 OMP_PLACES=24-27 ../xtb -P 4 --gfn 2 test.xyz  --opt
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37f2bd10ef22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.