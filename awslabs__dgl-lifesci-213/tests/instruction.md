# Issue

**Title:** Remove np.long which is no longer supported in latest numpy

## Description

### Problem repro
```
cd examples/binding_affinity_prediction
python3 main.py  -m PotentialNet -d PDBBind_core_pocket_random
...
FutureWarning: In the future `np.long` will be defined as the corresponding NumPy scalar.
  ]).astype(np.long)
multiprocessing.pool.RemoteTraceback: 
"""
Traceback (most recent call last):
  File "/usr/local/lib/python3.9/multiprocessing/pool.py", line 125, in worker
    result = (True, func(*args, **kwds))
  File "/usr/local/lib/python3.9/multiprocessing/pool.py", line 51, in starmapstar
    return list(itertools.starmap(args[0], args[1]))
  File "venv/lib/python3.9/site-packages/dgllife/utils/complex_to_graph.py", line 193, in PN_graph_construction_and_featurization
    ]).astype(np.long)
  File "venv/lib/python3.9/site-packages/numpy/__init__.py", line 320, in __getattr__
    raise AttributeError("module {!r} has no attribute "
AttributeError: module 'numpy' has no attribute 'long'
```

```
$ pip show numpy
Name: numpy
Version: 1.24.2
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90061b1fc890`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.