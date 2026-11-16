# Issue

**Title:** fix for brianQC and fix CI

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] fix for BrianQC in #3185 as suggested by @wszs

## CI Fixes
- [x] mac eco: with cmake v3.30.0, FindPython got seemingly unrelated updates, and now it `Could NOT find Python (missing: Python_NumPy_INCLUDE_DIRS NumPy)` as tested with longstanding np v1. I suspect an interaction with pb11 (hasn't greenlit 3.30 yet). so codedeps is restraining cmake to <=3.29
- [x] win eco, Part 1: so after the GHA win image issue (`Unexpected compiler version, expected Clang`) got fixed, we started seeing `error: capturing a structured binding is not yet supported in OpenMP`. That seems to be  where a syntax warning in clang v18 collides with a MSVC header that L2 includes. That warning was shifted in clang v19 to only fire within OMP loops rather than generically, but v19 isn't released and the fix hasn't ported back to v18, so the only sol'n is to use v17, which we're now requesting from conda. Note that the Azure Win is asking for v17 directly from Chocolatey, so that's why it was ok.
- [x] win eco, Part 2: so we have clang v17 from conda and can get past libmints, then we hit `error: use of undeclared identifier 'omp_set_max_active_levels'` in sapt.cc . This is the only use of this in the code, and the error probably has to do with limited omp support by windows. Fortunately, it seems that passing the path to the `intel-openmp`-provided `omp.h` which is in the weird dir `${PREFIX}\opt\compiler\include` rather than letting it find the clang-provided omp.h did the trick. Moreover, at long last the `intel-openmp` package provides the libiomp5md.lib (import library) and libiomp5md.dll (runtime library) _pair_ needed at buildtime rather than just the latter. So we no longer need to link against the random lib stashed on GH, and the build can be far more self-contained. hooray!
- [x] linux azure (two bottom lanes with new enough py for np v2): np v2 needs qcel v0.28 _and_ it needs pb11 >=2.12 to compile against or you'll get "atoms too close". pb11 had been constrained to <2.12 (see below), so that was lifted. bumped qcng to 0.30 for internal builds, too.
- [x] docs: a PR snuck adding a citation to the bibliography w/o citing it, so the strict check failed. commented out for now
- [x] docs: once pb11 no longer restrained to <2.12 (see above), the "FixedSize" issue appears (see nitpick-exceptions), and the exceptions formerly emitted as `List` needed `list` counterparts added.
- [x] win azure: headers in np v2 are at `numpy/_core/include` not `numpy/core/include`. We were setting the latter explicitly for this lane, so removed that. Also added `${Python_NumPy_VERSION}` printing for feedback.
- [x] linux eco: dftd4-python now available for py312 (except on windows), so added that back to the package testing.
- [x] cmake: squashed a few warnings by setting policies. it looks like find_package(Boost) for L2 is still needing FindBoost rather than BoostConfig, so that one needs to be OLD for now.
- [x] conda: threading tests weren't running at the conda recipe b/c the trial job hit the block we put in on MemDF in Disk mode. Increased the memory in test_threading so it could run.
- [x] gha: bumped all the actions to the latest version to get rid of node deprecation warnings.

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f920122cb5d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.