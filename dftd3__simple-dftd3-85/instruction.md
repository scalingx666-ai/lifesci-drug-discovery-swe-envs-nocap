# Issue

**Title:** Do not override grad_output at the end of arguments parsing

## Description

Now, it works as expected:
```
$ ./s-dftd3 CO.xyz --bj tpss --grad hdfgd
<...>
Virial:
--------------------------------------------------
      component           x          y          z
--------------------------------------------------
          x       0.000E+00  0.000E+00  0.000E+00
          y       0.000E+00  0.000E+00  0.000E+00
          z       0.000E+00  0.000E+00  1.711E-06
--------------------------------------------------

[Info] Dispersion energy written to .EDISP
[Info] Dispersion results written to 'hdfgd'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `150f0cf674c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.