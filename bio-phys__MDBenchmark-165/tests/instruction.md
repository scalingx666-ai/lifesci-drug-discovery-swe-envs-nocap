# Issue

**Title:** Add ranks and threads to templates

## Description

## Rationale

We want to allow users to change the number of MPI ranks and OpenMP threads in their benchmarks, because these settings affect the simulation performance.

## Limitations

### Validation of `--ranks`
The validity of the `--ranks` option is determined on the current machine. If the number of physical cores is different on the login and work nodes and the user specifies a number of ranks (`--ranks`) that would be valid on the work nodes we throw an error.

~We can probably solve this by adding another `--threads` option, in which we ignore all our own calculations and use user specified values? I would first go with this leaner implementation and see whether anyone complains.~

I added the `--physical-cores` and `--logical-cores` options to mitigate this issue. I don't like this solution, but there is probably no way around this.

### Backwards compatibility
We changed the folder structure from `cobra_gromacs/2019.6/5` to `cobra_gromacs/2019.6/n005_r40_t02_wht`. This is more explicit, but not backwards compatible in case users have written some bash scripts that assume a certain folder naming.

I am proposing to release this feature with MDBenchmark v3.0, where we also deprecate Python 3. We might also want to refactor other parts of the code, because there is some inconsistencies that could be improved.

## Changelog

Changes made in this pull request:
- Add `--ranks` option, with which the user can specify the number of MPI ranks to use. The number of OpenMP threads will be calculated accordingly. .
- Add `--hyperthreading` option to toggle usage of hyperthreading.
- Add `--physical-cores` and `--logical-cores` to specify the number of cores on the work nodes. If `--logical-cores` is not specified, will assume hyperthreading is possible (`logical-cores = 2 * physical-cores`). If `--physical-cores` is not specified, will retrieve information from the current machine.
- Update MPCDF cluster `cobra` template to include (not so) recent changes to the queuing system.
- Add ranks/threads/hyperthreading variables to `cobra` and `draco` templates.
- Add `-resethway` option to `mdrun` command. .

PR Checklist
------------
 - [ ] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?
 - [ ] Update documentation
 - [ ] Update examples in `README.md`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7940eeedf132`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.