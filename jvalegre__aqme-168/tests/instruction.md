# Issue

**Title:** fixed --qm_end when using 'modifysph'

## Description

Huber, Truhlar,and Cramer recommend using different radius for bromine and iodine in the SMD18 (https://doi.org/10.1002/chem.201803652). The lines must be added after the gen/genecp info in g16, unlike freezing bonds etc. The proposed change will take care of that by looking for 'modifysph' in the --qm_end input. I tested it on mac with:
--qm_end "B 1 2 F"$'\n''B 1 5 F'$'\n''B 2 5 F' --> before genecp
--qm_end "modifysph"$'\n'$'\n'"I 2.74" --> after genecp
--qm_end "$nbo bndidx $end" --> before genecp

- changed config.yml file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1cd242a1664`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.