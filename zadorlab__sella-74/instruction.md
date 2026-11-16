# Issue

**Title:** Don't create a cache in home dir if another path is given

## Description

I'm trying out Sella at University of Toronto.

In our cluster (Trillium), it seems that the compute nodes don't have write access to the home directory, so I get this error:

```
Traceback (most recent call last):
  File "/scratch/alexlm/lit-xyz-sella/lit_uma_geom_pipeline.py", line 31, in <module>
    from bluephos.action import energy, geometry_energy
  File "/scratch/alexlm/lit-xyz-sella/bluephos/action.py", line 1, in <module>
    from sella import Sella
  File "/scratch/alexlm/lit-xyz-sella/.venv/lib/python3.11/site-packages/sella/__init__.py", line 7, in <module>
    os.makedirs(_cache_dir, exist_ok=True)
  File "<frozen os>", line 215, in makedirs
  File "<frozen os>", line 225, in makedirs
PermissionError: [Errno 13] Permission denied: '/home/alexlm/.cache/sella'
```

I tried adding this to my submit script:

```
export JAX_COMPILATION_CACHE_DIR=/scratch/alexlm/sella_cache
```

However, this results in the same error.

This is because of a bug in the code that sets the cache directory. If `JAX_COMPILATION_CACHE_DIR` is set, it does not change it. However, it ignores the value in favor of the generated default, including when it creates the cache directory, causing an error in my case.

Therefore, I have updated the code to use the value of `JAX_COMPILATION_CACHE_DIR` if present.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4626c96262`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.