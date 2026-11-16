# Issue

**Title:** Fix Processes Work Manager Shutdown SegFault

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->

Sometimes at the end of a task with the processes work manager (e.g., running `w_run --work-manager processes` or `w_ipa -ao`), there might be a partial/full Traceback message because one or more threads shutdown incorrectly (usually after the `WEST run complete.` or equivalent line). The full message is listed below (a very lucky attempt after 100s of attempts of reproducing it).

This is a race condition error, so the cause/error message output is pretty inconsistent. In this instance of the error message, I think the daemon `Threading.thread` (which is tasked to fetch results) attempts to pull from the queue but the `stderr` and/or `stdin` is closed because the queue is in the process of shutting down.  This causes a lot of trouble upstream in the `threading` module.

I setup a `threading.Event` flag, which will signal for thread to close at `shutdown()`. The new `if not self.result_queues.empty()` statement will prevent unwanted `self.result_queues.get()`.  The `while not self.shutdown_received.is_set():` line takes care of the false negatives because there will always be a subsequent loop (or if we're shutting down, then it won't matter).

This clean stackoverflow answer was very helpful...
https://stackoverflow.com/a/41139707

To test, just re-run a completed simulation with the processes work manager (i.e. run `w_run` on a simulation that reached `max_total_iterations`) for 10+ times. 

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Prevent Segfault when Processes Daemon Thread is terminated due to race condition 

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/work_managers/processes.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

Full Error Message:
```
Tue May  7 18:13:43 2024
WEST run complete.
Exception in thread receiver:
Traceback (most recent call last):
  File "/Users/user/miniconda3/envs/westpa-ambertools/lib/python3.11/threading.py", line 1045, in _bootstrap_inner
    self.run()
  File "/Users/user/miniconda3/envs/westpa-ambertools/lib/python3.11/threading.py", line 982, in run
    self._target(*self._args, **self._kwargs)
  File "/Users/user/miniconda3/envs/westpa-ambertools/lib/python3.11/site-packages/westpa/work_managers/processes.py", line 96, in results_loop
Fatal Python error: _enter_buffered_busy: could not acquire lock for <_io.BufferedWriter name='<stderr>'> at interpreter shutdown, possibly due to daemon threads
Python runtime state: finalizing (tstate=0x0000000102bbf2c8)

Current thread 0x00000001eaff7ac0 (most recent call first):
  <no Python frame>

Extension modules: numpy.core._multiarray_umath, numpy.core._multiarray_tests, numpy.linalg._umath_linalg, numpy.fft._pocketfft_internal, numpy.random._common, numpy.random.bit_generator, numpy.random._bounded_integers, numpy.random._mt19937, numpy.random.mtrand, numpy.random._philox, numpy.random._pcg64, numpy.random._sfc64, numpy.random._generator, westpa.core.binning._assign, h5py._errors, h5py.defs, h5py._objects, h5py.h5, h5py.utils, h5py.h5t, h5py.h5s, h5py.h5ac, h5py.h5p, h5py.h5r, h5py._proxy, h5py._conv, h5py.h5z, h5py.h5a, h5py.h5d, h5py.h5ds, h5py.h5g, h5py.h5i, h5py.h5f, h5py.h5fd, h5py.h5pl, h5py.h5o, h5py.h5l, h5py._selector, mdtraj.formats.dcd, mdtraj.formats.binpos, mdtraj.formats.xtc, mdtraj.formats.trr, mdtraj.formats.dtr, mdtraj.formats.tng, mdtraj._rmsd, scipy._lib._ccallback_c, scipy.sparse._sparsetools, _csparsetools, scipy.sparse._csparsetools, scipy.linalg._fblas, scipy.linalg._flapack, scipy.linalg.cython_lapack, scipy.linalg._cythonized_array_utils, scipy.linalg._solve_toeplitz, scipy.linalg._decomp_lu_cython, scipy.linalg._matfuncs_sqrtm_triu, scipy.linalg.cython_blas, scipy.linalg._matfuncs_expm, scipy.linalg._decomp_update, scipy.sparse.linalg._dsolve._superlu, scipy.sparse.linalg._eigen.arpack._arpack, scipy.sparse.linalg._propack._spropack, scipy.sparse.linalg._propack._dpropack, scipy.sparse.linalg._propack._cpropack, scipy.sparse.linalg._propack._zpropack, scipy.sparse.csgraph._tools, scipy.sparse.csgraph._shortest_path, scipy.sparse.csgraph._traversal, scipy.sparse.csgraph._min_spanning_tree, scipy.sparse.csgraph._flow, scipy.sparse.csgraph._matching, scipy.sparse.csgraph._reordering, scipy.spatial._ckdtree, scipy._lib.messagestream, scipy.spatial._qhull, scipy.spatial._voronoi, scipy.spatial._distance_wrap, scipy.spatial._hausdorff, scipy.special._ufuncs_cxx, scipy.special._cdflib, scipy.special._ufuncs, scipy.special._specfun, scipy.special._comb, scipy.special._ellip_harm_2, scipy.spatial.transform._rotation, mdtraj._lprmsd, mdtraj.geometry._geometry, mdtraj.geometry.drid, mdtraj.geometry.neighbors, mdtraj.geometry.neighborlist, psutil._psutil_osx, psutil._psutil_posix, yaml._yaml, zmq.backend.cython._zmq (total: 94)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43ed1b907ea9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.