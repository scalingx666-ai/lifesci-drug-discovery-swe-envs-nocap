# Issue

**Title:** Switch to Maven dependencies resolver

## Description

PRs that need to be merged in Kotlin for this one:

- [x] 
- [x] 

, because mavenLocal is used as cache.
Also .
Also adds repository authorization, cc @belovrv 
```kotlin
@file:Repository("https://url", "<username>", "<password>")
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6257af893a3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.