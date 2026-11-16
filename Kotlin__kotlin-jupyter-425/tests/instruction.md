# Issue

**Title:** Add API for handling result field with a type converter API

## Description

Result field doesn't have Kotlin property representation. To handle it, information about corresponding Java field was added to the low-level API. So, low-level API is broken, but seemingly no one uses it. High-level API was left semantically unchanged (it still doesn't process java fields without corresponding Kotlin properties). `ResultFieldUpdateHandler` class was added to handle this particular use case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `687ac7b05eb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.