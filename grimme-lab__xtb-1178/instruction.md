# Issue

**Title:** Speed-up hot path of GFN2 geometry optimization

## Description

This PR improves parallelization for GFN2 geometry optimization. It affects other types of calculations too.

Achieved speed-up is **30%**. Gradients are **2x** faster!

For 578 atom structure, before the patch:
```
 total:
 * wall-time:     0 d,  0 h,  1 min, 11.680 sec
 *  cpu-time:     0 d,  0 h,  3 min,  7.524 sec
 * ratio c/w:     2.616 speedup
 SCF:
 * wall-time:     0 d,  0 h,  0 min, 13.534 sec
 *  cpu-time:     0 d,  0 h,  0 min, 41.212 sec
 * ratio c/w:     3.045 speedup
 ANC optimizer:
 * wall-time:     0 d,  0 h,  0 min, 57.390 sec
 *  cpu-time:     0 d,  0 h,  2 min, 25.103 sec
 * ratio c/w:     2.528 speedup

normal termination of xtb

real 1m11.740s
user 3m5.985s
sys 0m1.572s
```

After the patch:
```
 total:
 * wall-time:     0 d,  0 h,  0 min, 48.779 sec
 *  cpu-time:     0 d,  0 h,  2 min, 51.122 sec
 * ratio c/w:     3.508 speedup
 SCF:
 * wall-time:     0 d,  0 h,  0 min, 11.737 sec
 *  cpu-time:     0 d,  0 h,  0 min, 42.249 sec
 * ratio c/w:     3.600 speedup
 ANC optimizer:
 * wall-time:     0 d,  0 h,  0 min, 36.377 sec
 *  cpu-time:     0 d,  0 h,  2 min,  8.025 sec
 * ratio c/w:     3.519 speedup

normal termination of xtb

real 0m48.971s
user 2m50.138s
sys 0m1.012s
```

Command for testing:
```
xtb --input model.xtb model.xyz -P 4 --gfn 2 --opt vtight --alpb water --cycles 5
```

model.xtb (nothing interesing, to be honest):
```
$opt
    engine=rf
$end
$alpb
    kernel=still
    grid=tight
$end
```

Build type: CMake, Release, gfortran-14, Intel MKL, no march (can get extra speed-up), enabled debug info.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04ad2f85c501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.