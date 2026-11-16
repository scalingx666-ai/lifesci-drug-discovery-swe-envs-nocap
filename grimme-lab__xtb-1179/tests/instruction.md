# Issue

**Title:** Enable hyphen separated range of atoms to modify mass

## Description

## Refers to the following [feature](https://xtb-docs.readthedocs.io/en/latest/hessian.html#advanced-options)

### Situation before 
before, only single entries like:
```
$hess
modify mass: 12, 2.0, 3, 4.0
scale mass: 2, 1.5, 5, 6.0
$end
```
were possible.

### Improvement
Hyphen-separated ranges of atoms can be read in, like:
```
$hess
scale mass: 12-50,2.0
modify mass: 1-3,400.0
$end
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f7a2e245de4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.