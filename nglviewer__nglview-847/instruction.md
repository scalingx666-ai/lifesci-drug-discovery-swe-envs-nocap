# Issue

**Title:** contrib.movie.MovieMaker.make() should call perframe_hook if specified

## Description

I noticed that `nglview.contrib.movie.MovieMaker.make()` does not call the user-specified `perframe_hook` if one is specified. This appears to be an accidental omission, since it appears in `.make_old_impl()`. This PR ensures this is called, with `view.frame` updated to the appropriate frame number before it is passed to the hook.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `632de79a22e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.