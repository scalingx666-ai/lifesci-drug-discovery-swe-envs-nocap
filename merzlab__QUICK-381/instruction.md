# Issue

**Title:** Github CI Workflow Optimizations

## Description

This PR speeds up the serial CPU tests in the Github CI workflow by running those tests in parallel using GNU parallel (`parallel`) in the `runtest` script -- set the variable `PARALLEL_TEST_COUNT` before running `runtest`.  Specifically, use 2 cores for running the serial CPU tests for Github workflow runners.

Furthermore, the ability to run tests is parallel is supported for MPI, single GPU, and MPI+GPU QUICK versions. For MPI and MPI+X versions, set both `PARALLEL_TEST_COUNT` and `DO_PARALLEL`. For GPU versions, set both `PARALLEL_TEST_COUNT` and `CUDA_VISIBLE_DEVICES`/`HIP_VISIBLE_DEVICES`, where the number of available GPUs must be at least the number of parallel tests (i.e., at least 1 GPU per each GNU parallel job).

Additional notes/limitations:
- Exporting shell functions for parallel execution with `parallel` required using `bash`-style function exporting.  As such, the default shell used in `runtest` was changed to `bash`.  This should not be a problem with QUICK integration with Amber as many of the test scripts in Amber use `bash`.
-  `parallel`l has the ability to manage the output to STDOUT (see, e.g., `--group`, `--keep-order`).  This is used to keep the test output to STDOUT in-order by test ID.  However, `runtest` also duplicates output to `runtest.log`, which `parallel` cannot manage; as such, simple file locking with spin locks was used to avoid race conditions on writes to this file.  However, while the test outpus are grouped correctly by output per job, the order of job output is not enforced.  As such, the test output order will vary from run to run.  If this becomes problematic for functional reasons, this can be improved in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47eb00b625f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.