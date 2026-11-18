# Issue

**Title:** ERI grad cutoff fix

## Description

I performed a series of HF/DEF2-SVP gradient tests after fixing the the grad cutoff (after commit #53ebb725ea816f0fdde5676ab258c43423493e5d). Everything looks good (see below).  Note that the comparison is wrt. reference data taken from software X. 

```
2-AminoadipicAcid energy = 7.09e-07, Passed; grad = 5.54e-06, Passed 

AbscisicAcid energy = 7.16e-07, Passed; grad = 5.57e-06, Passed 

Anserine energy = 1.09e-06, Passed; grad = 7.49e-06, Passed 

Asparagine energy = 7.68e-07, Passed; grad = 5.69e-06, Passed 

Carnosine energy = 1.07e-06, Passed; grad = 6.71e-06, Passed 

Citrulline energy = 8.08e-07, Passed; grad = 5.69e-06, Passed 

Glutamine energy = 8.94e-07, Passed; grad = 5.73e-06, Passed 

GuanidinoaceticAcid energy = 6.56e-07, Passed; grad = 5.34e-06, Passed 

HippuricAcid energy = 8.61e-07, Passed; grad = 5.90e-06, Passed 

KynurenicAcid energy = 6.91e-07, Passed; grad = 6.17e-06, Passed 

Mimosine energy = 1.05e-06, Passed; grad = 6.46e-06, Passed 

Naproxen energy = 6.53e-07, Passed; grad = 8.79e-06, Passed 

NicotinicAcid energy = 5.73e-07, Passed; grad = 5.79e-06, Passed 

N-Methyl-L-glutamate energy = 9.41e-07, Passed; grad = 7.31e-06, Passed 

NN-Dimethylglycine energy = 5.91e-07, Passed; grad = 6.35e-06, Passed 

Ornithine energy = 5.15e-07, Passed; grad = 5.35e-06, Passed 

O-Succinyl-L-homoserine energy = 1.13e-06, Passed; grad = 8.74e-06, Passed 

QuinolinicAcid energy = 7.32e-07, Passed; grad = 5.93e-06, Passed 

SalicylicAcid energy = 6.56e-06, Passed; grad = 2.17e-05, Passed 

Serotonin energy = 4.35e-07, Passed; grad = 6.24e-06, Passed 

Tryptophan energy = 7.08e-07, Passed; grad = 8.56e-06, Passed 

Tyrosine energy = 6.43e-07, Passed; grad = 7.80e-06, Passed 

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b7720cece29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.