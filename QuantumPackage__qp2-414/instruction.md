# Issue

**Title:** ci: install simple_gpu before the hard configure check

## Description

## What

`configuration.yml` ends with the hard check

```
./configure -c config/gfortran_debug.cfg
```

and since `9186ab21` `configure` fails when `simple_gpu` is missing:

```
configure: SimpleGPU (simple_gpu) is not installed.
##[error]Process completed with exit code 2.
```

That workflow's dependency list never installs it, so every `master`-targeted
PR now fails the Dependencies job — for example
[run 43218728038](https://github.com/QuantumPackage/qp2/actions/runs/43218728038)
on #411, while the Compilation job's *own* Configuration step passed, because
`compilation.yml` does install `simple_gpu`. The two workflows disagree about
the same hard check.

## Change

Two lines, nothing else:

- `configuration.yml`: add a `simple_gpu` step after `qmckl`, in the style of
  its neighbours (`|| echo OK`).
- `compilation.yml`: add `./configure -i simple_gpu || :` too. It is missing
  on `master` (`dev-stable` already has it), so without this line the next
  merge of the `simple_gpu` change breaks `master`'s own Compilation job as
  well.

## Notes

- `./configure -i simple_gpu` installs from a tarball (not a submodule) and
  is already used by `compilation.yml` in this repository on
  `ubuntu-24.04`, successfully — so the step works on the runner image.
- On today's `master` the `configure` check is not present yet
  (`9186ab21` is in `dev-stable`, not in `master`), so this patch is
  preventive there and becomes mandatory the moment that work lands.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d93ca7c2aa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.