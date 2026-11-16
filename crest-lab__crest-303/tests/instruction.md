# Issue

**Title:** Allow `tblite` parameter file read-in

## Description

Parameter files must be in toml format. Examples are located at  [assets/tblite/](https://github.com/crest-lab/crest/tree/master/assets/tblite/)
This is an update to #223 

The parameter file can be specified within the `[[calculation.level]]` block:
```
[[calculation.level]]
method='tblite'
tblite_param='gfn1.toml'
```
which formally replaces any other `tblite` method selection.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4eb649b6df1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.