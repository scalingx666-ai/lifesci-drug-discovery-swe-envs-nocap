# Issue

**Title:** use thread safe collection in RoundRobinFormulaGenerator

## Description

Hi all,

thanks for providing the CDK first of all 👍. 

We use it in mzmine to generate molecular formulas and noticed, that we cannot parallelise the generation for the RoundRobinFormulaGenerator (line 170). The issue was that the cache in there was not thread safe and iteration caused a concurrent modification exception.

I replaced the current cache with a thread-safe ConcurrentLinkedQueque.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `834d1ebbd3cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.