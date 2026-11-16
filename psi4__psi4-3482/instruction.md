# Issue

**Title:** Don't let a broken optional mpi4py abort `import psi4`

## Description

Currently psi4 doesn't work if mpi4py is installed on my system, since the MPI stack in Fedora is behind environment modules due to the ABI incompatibility of OpenMPI and MPICH. This PR fixes the import exception to the case where mpi4py is available but the MPI library doesn't resolve.

# AI summary

## Problem

`psi4/driver/mdi_engine.py` imports `mpi4py` only for MDI (MolSSI Driver Interface) runs, and already guards the import as optional:

```python
try:
    from mpi4py import MPI
    use_mpi4py = True
except ImportError:
    use_mpi4py = False
```

But it catches only `ImportError`. **mpi4py ≥ 4** `dlopen`s `libmpi` *at import time* to probe the MPI ABI, and raises **`RuntimeError`** (not `ImportError`) when no MPI runtime library is present. That escapes the guard and aborts `import psi4` entirely — for any user who has mpi4py installed without a loadable MPI library, even though nothing outside MDI uses mpi4py.

Observed traceback:
```
  File ".../psi4/driver/mdi_engine.py", line 63, in <module>
    from mpi4py import MPI
  ...
  File ".../mpi4py/_mpiabi.py", line 210, in _dlopen_libmpi
RuntimeError: cannot load MPI library
```

## Fix

Catch `Exception` instead of `ImportError`, so *any* failure to bring in the optional MPI support simply disables it (`use_mpi4py = False`) — the intended behavior for an optional dependency.

## Verification

A stand-in `mpi4py` that raises `RuntimeError` at import (mimicking the 4.x ABI probe) confirms the behavior change:

```
old guard (except ImportError): UNCAUGHT RuntimeError: cannot load MPI library  <-- aborts 'import psi4'
new guard (except Exception):   use_mpi4py=False (caught)
```

Only the MDI code path reads `use_mpi4py`, so nothing else is affected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5119521a774f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.