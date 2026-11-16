# Issue

**Title:** Make `allow_*` flags work with caching

## Description

. 

Improvements that are out of scope for this bugfix PR:
* Less strict cache invalidation: For several cases, the PR clears the cache too conservatively (see also comments added).  In particular, caching is not used at all / immediately cleared as soon as pending experiments enter the stage. By storing the previous recommendation context and using more fine-grained conditions, cache usage could be further extended.
* Instead of manually maintaining the caching logic and conditions, we might also consider switching to a built-in approach (e.g. using `@cached` directly on the recommender level), which would potentially simply the logic significantly and avoid future bugs due to not having to think about edge cases. However, the caching approach would then be even stricter as it is now, since it would only work based on the incoming objects.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57cadc176108`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.