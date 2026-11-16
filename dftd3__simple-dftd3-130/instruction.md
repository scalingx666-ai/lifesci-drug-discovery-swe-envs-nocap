# Issue

**Title:** Add LibXC alias xc names in param.f90

## Description

I noticed that some of the functionals defined in `get_method_id` inside `param.f90` have an alternative name in [LibXC](https://libxc.gitlab.io/functionals/).

In particular, these are:

- b1b95 = HYB_MGGA_XC_B88B95
- bhlyp = HYB_GGA_XC_BHANDHLYP (assuming that bhlyp refers to the implementation with Becke 88 exchange instead of LDA exchage - see J. Chem. Phys. 159, 114116 (2023), DOI: 10.1063/5.0167763. But please correct me if I am wrong, if it is the other way around then it would instead be HYB_GGA_XC_BHANDH)
- pbe0 = HYB_GGA_XC_PBEH

I therefore added the aliases "b88b95", "bhandhlyp", and "pbeh" for "b1b95", "bhlyp", and "pbe0", respectively, so that the D3 automatic parameter recognition based on functional name could be used with LibXC for these functionals.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f45fe8a19b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.