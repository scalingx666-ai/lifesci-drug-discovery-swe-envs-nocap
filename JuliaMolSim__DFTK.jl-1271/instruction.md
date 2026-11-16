# Issue

**Title:** Derivative support in mgga and mggal potential computations

## Description

This is derivative hell. The tests pass but they also don't seem super robust (e.g. swapping a few cross-derivatives still makes them pass... this of course also depends on the exact used xc functional). So I triple-checked the order of derivatives, and it seems correct. We could maybe use macros/generated functions but it will reduce readability.

As a side-note, it's weird that mggal is seen as something more general than mgga; usually it's more of a bandaid when tau is not available? (E.g. `mgga_x_r2scanl`). In principle nothing stops us from doing DFPT with $\nabla^2 \rho$-dependent functionals such as r2scanl, but this interface requiring `tau` does...

It might be better to rethink this whole interface such that the evaluation of a functional is done with maximum flexibility and only considers the relevant contributions to the potential and the kernel.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29c63808cf0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.