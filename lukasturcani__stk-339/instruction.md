# Issue

**Title:** Plug PeriodicInfo state leak

## Description

Related Issues: #307 
Requested Reviewers: @andrewtarzia 
*Note for Reviewers: If you accept the review request add a :+1: to this post*

When `PeriodicInfo` is being initialized it is not making a copy of
the arrays it is being given. This means thats if those arrays get
changed on the outside, the internal state of `PeriodicInfo` also gets
corrupted. Similarly, when the `get` methods are called, the internal
state is returned directly, rather than a copy of the arrays. If
someone calls `get` and then changes the value in the returned array,
they will also change the internal state of `PeriodicInfo`.

This commit just makes sure to make a copy of the arrays which are
received as input and returned as output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2814dda36b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.