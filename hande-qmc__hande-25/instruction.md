# Issue

**Title:** First-order sanity check that qmc_state aren't being reused multiple …

## Description

…times

Consider the input file

```
sys = ueg {
    electrons = 6,
    ms = 0,
    sym = 15,
    dim = 3,
    cutoff = 2,
    rs = 2.0,
}

qmc = {
    tau = 0.02,
    init_pop = 10,
    mc_cycles = 10,
    nreports = 10,
    target_population = 50000,
    state_size = 50000,
    spawned_state_size = 5000,
    initiator = true,
}
ref = {
    det = {1, 2, 3, 10, 11, 14},
}

qs = fciqmc {
    sys = sys,
    qmc = qmc,
    reference = ref,
}

fciqmc {
    sys = sys,
    qmc = qmc,
    reference = ref,
    qmc_state = qs,
}

fciqmc {
    sys = sys,
    qmc = qmc,
    reference = ref,
    qmc_state = qs,
}
```

The third FCIQMC calculation previously caused a segmentation fault
because we initialise its qmc_state_t object from the one passed in,
except we already moved that memory to the qmc_state_t object used in
the second calculation, so we end up accessing invalid memory. The
correct thing is to either use restart files (if you genuinely want to
restart from the first calculation twice) or to pass the qmc_state
returned by the second calculation to the third (if you want to chain
the three calculations together).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `671f87b13415`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.