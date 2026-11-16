# Issue

**Title:** Fix get_resolution in data preprocessing

## Description

`get_resolution` was always returning `0.0`, due to incorrectly unwrapping the `gemmi` row:
```
ipdb> block.find([res_key])[0]
<gemmi.cif.Table.Row: 2.800>
ipdb> float(block.find([res_key])[0])
*** TypeError: float() argument must be a string or a real number, not 'gemmi.cif.Row'
ipdb> float(block.find([res_key])[0].str(0))
2.8
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3b5e1da6c9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.