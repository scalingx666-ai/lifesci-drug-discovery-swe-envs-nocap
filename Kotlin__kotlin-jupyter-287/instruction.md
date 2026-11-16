# Issue

**Title:** Create specialized kernels w/ JDK, JVM args, and environment variables

## Description

.
.

I'd like to note this somewhere in the readme (and that it can be set per-kernel with `env` in the kernelspec), any preference on where?

I also thought about a few possible further features:
1. Creating kernels for each detected JDK version on install (presumably in `install_user`, although I can't find where it gets called on initial install).
2. Adding a `fix-kernelspec-location`-like task to create a kernel for a specific JDK.
3. Adding a `kotlin-jupyter` specific environment variable that overrides `JAVA_HOME`, i.e. `KOTLIN_JUPYTER_JAVA`, incase you want jupyter on a different JDK than say gradle (although that's doable via the kernelspec).

Thoughts on any of them?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `884f905387a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.