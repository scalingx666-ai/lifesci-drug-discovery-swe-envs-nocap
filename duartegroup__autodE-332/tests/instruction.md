# Issue

**Title:** Fix error in "atoms_to_xyz_file()" in "input_output.py"

## Description

Added explicit space to print xyz coordinates to account for occasional cases where there is no space printed between two numbers, for example, `H    13.56100 -35.93700-100.99000`, and thus the printed xyz file becomes invalid.

```
########################################################################

[ERROR] Program stopped due to fatal error
-2- reading geometry input 'test2_sp_xtb.xyz' failed
-1- Error: Could not parse coordinates from xyz file
  --> test2_sp_xtb.xyz:24:15-33
   |
24 | H    13.56100 -35.93700-100.99000
   |               ^^^^^^^^^^^^^^^^^^^ expected real value
   |
########################################################################
```

<!--
Please replace _#ISSUE_ with just e.g. #12 if this PR resolves issue 12.
## Resolves _#ISSUE_
-->


***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0c05f0ed04c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.