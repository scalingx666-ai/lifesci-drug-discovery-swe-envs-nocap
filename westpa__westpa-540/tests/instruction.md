# Issue

**Title:** Dask-based work manager

## Description

This PR adds a new work manager built on the [dask.distributed](https://github.com/dask/distributed) library.

Like the MPI work manager, the Dask work manager is not available by default. To enable it, install WESTPA with the `dask` extra:
```sh
$ python -m pip install westpa[dask]
```

## Usage

Run on the default local cluster:

```sh
$ w_run --work-manager dask
```

Run on a local cluster with 6 workers:
```sh
$ w_run --work_manager dask --n-workers 6
```

Start up a cluster and point WESTPA to the scheduler address:
```sh
$ dask scheduler
INFO -   Scheduler at:     tcp://10.0.0.164:8786
$ dask worker 10.0.0.164:8786
$ w_run --work-manager dask --dask-scheduler-address 10.0.0.164:8786
```

Start up a cluster and point WESTPA to the scheduler file:
```sh
$ dask scheduler --scheduler-file /path/to/scheduler.json
$ dask worker --scheduler-file /path/to/scheduler.json
$ w_run --work-manager dask --dask-scheduler-file /path/to/scheduler.json
```

## Status
<!--- Delete bullet points that are not relevant. --->
- [ ] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [ ] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e8a52b2355b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.