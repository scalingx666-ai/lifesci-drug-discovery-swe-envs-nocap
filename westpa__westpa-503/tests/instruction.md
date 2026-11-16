# Issue

**Title:** Add w_timings CLI tool

## Description

## Issue Number

This PR is a revision of #499, itself a revision of #466.

 


## Describe the changes made

Add a new CLI tool that displays timing information for a WESTPA simulation.

The default output includes the wall-clock time and, if per-segment CPU times were recorded by the propagator, the total CPU time:
```console
$ w_timings -W west.h5
Iterations:                100
Total segments:            7775
Wall-clock time:           2 days, 4:35:11.749094
Total CPU time:            17 days, 9:09:00.556985
```
When a resampling interval (`-t/--tau`) is specified, output also includes the maximum trajectory length ("molecular time") and aggregate simulation time:
```console
$ w_timings -W west.h5 -t 50_ps
Iterations:                100
Total segments:            7775
Wall-clock time:           2 days, 4:35:11.749094
Total CPU time:            17 days, 9:09:00.556985
Maximum trajectory length: 5.0 ns
Aggregate simulation time: 388.75 ns
```


## Files changed
- `src/westpa/cli/tools/w_timings.py` (new file)
- `setup.py` (added entry point)
- `tests/test_tools/test_w_timings.py` (new file)
- `doc/documentation/cli.rst` (added toctree item)
- `doc/documentation/cli/w_timings.rst` (new file)

## Status
<!--- Delete bullet points that are not relevant. --->
- [ ] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7955b4e236a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.