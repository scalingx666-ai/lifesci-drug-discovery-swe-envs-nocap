# Issue

**Title:** Faster `to_df` for mols to dataframe conversion

## Description

Checklist:

- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [x] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

*Background Information*:

`dm.read_sdf(..., as_df=True)` is very slow on large dataset. It turns out that the bottleneck is not the SDF reading but the conversion from a list of molecule to a dataframe. 

```python
In [1]: import datamol as dm
   ...: import numpy as np
   ...: data_path = "tests/data/TUBB3-observations.sdf"
   ...: mols = dm.read_sdf(data_path)
   ...: large_mol_set = np.random.choice(mols, 10000)
   ...: with dm.utils.perf.watch_duration(log=True) as w:
   ...:     df_sequential = dm.to_df(large_mol_set, n_jobs=1)

2022-11-04 22:27:43.474 | INFO     | datamol.utils.perf:__exit__:80 - Duration 5min.

   ...: 
   ...: with w:
   ...:     df_parallel = dm.to_df(large_mol_set, n_jobs=-1)
   ...: parallel_time = w.duration
2022-11-04 22:29:36.527 | INFO     | datamol.utils.perf:__exit__:80 - Duration 1min.
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce9e6ef5d924`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.