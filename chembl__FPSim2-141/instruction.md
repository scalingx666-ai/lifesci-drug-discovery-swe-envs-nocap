# Issue

**Title:** Fix fps refcount corruption in parallel in-memory search

## Description

The pybind11 search functions take their NumPy array arguments by value and are registered with py::call_guard<py::gil_scoped_release>(). pybind11 destroys the by-value argument copies while the GIL is released, so the Py_DECREF on the shared fingerprint array runs without the GIL held. With n_workers > 1 the ThreadPoolExecutor runs several chunks concurrently over the same fps array, and these unsynchronized refcount updates race and corrupt its reference count. The array can then be freed while still in use and its memory reused, causing "worker died" incompatible-argument errors or segfaults.

Take the array arguments by const reference instead, so no by-value copy is created in the callee and no refcount operation runs during GIL-released execution. pybind11's internal caster holds the borrowed reference and is destroyed after the GIL is re-acquired.

Add a regression test asserting fps refcount stability under multi-worker in-memory searches.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e03e66945614`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.