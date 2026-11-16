# Issue

**Title:** Trim apt recommends and raise the development-version job timeout

## Description

### Summary

The development version tests fail intermittently but often enough to matter — of order one run in ten. The failure is a timeout, but the cause is outside this repository: for some fraction of runs the Azure Ubuntu mirror serving the runner's region is degraded, and the BLAS/MPI install step costs an extra half hour instead of finishing in seconds.

In one such run both `ubuntu-latest` jobs landed in the same region and both were slow, while the `macos-latest` job (Homebrew, different host) was unaffected. That rules out a single unhealthy VM. `apt-get update` was fast in the same run; only the package downloads crawled.

### Why there is nothing to configure

`Acquire::http::Timeout` governs *inactivity*. During a degraded run apt keeps receiving data the whole time, just some three orders of magnitude below the usual rate, so the timeout never fires. apt offers no throughput floor. The only lever available is headroom, so this raises `timeout-minutes` from 60 to 90 for the development-version job. A job in the affected run still finished within the hour under the degraded mirror, so the work fits when given room.

Only that one workflow gets the bump. It is the only job that also builds five development wheels before testing, which already put it near the old ceiling; the nightly prerelease job builds one wheel and has ample margin at 60.

### `--no-install-recommends`

Applied wherever these packages are installed. It drops a dozen packages nothing here uses, among them Fortran coarrays, `libjs-jquery-ui` and `manpages-dev`.

This is hygiene, not a fix for the timeout. It barely shrinks the download: the ROCm and OpenCL libraries that dominate it are hard dependencies of `libopenmpi40` via `libucx0`/`libucc1`, so they are installed either way.

Verified in an Ubuntu 26.04 container matching the runner image that the trimmed set still provides everything the builds need: `mpicc`/`mpicxx`/`mpirun` work, BLAS/LAPACK and OpenBLAS link and run, and the `pkg-config` files for BLAS, LAPACK and MPI are intact. `pandoc` declares no `Recommends:` at all, so the flag is a no-op in `docs.yml`.

### Not done

Caching the `.deb` files would actually prevent the slow download rather than tolerate it. I have left it out: it makes the workflow stateful, and `actions/cache` scoping is per-branch, so a new PR branch would still pay full price on its first run. Worth revisiting if 90 minutes proves insufficient.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a77c7449d77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.