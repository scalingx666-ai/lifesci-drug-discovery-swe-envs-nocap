# Issue

**Title:** AutoBool allow_* flags

## Description

.

The drawback of the previous approach was that the flag attributes had a union `bool | UnspecifiedType` type, which meant that they could not be safely accessed without additional conversion logic, resulting in the bug reported in #733.

To fix this, the user-facing value of the flags should always be a simple `bool` at query time, while still offering a clever "auto-determine" mechanism that does not require the user to explicitly set them depending on the search space type. 

There are two options to achieve this:
1. Using a context-specific conversion at attribute setting time. While possible, it has the disadvantage that it complicates validation, which usually happens only after conversion.
2. For this reason, we use an `AutoBool` approach, where the user-specified value is stored as a private attribute and the public value is resolved lazily at query time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `001e40afe7ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.