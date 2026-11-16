# Issue

**Title:** Fix Cholesky decomposition crash when rank_max is reached

## Description

This PR fixes the crash that occurs when the Cholesky decomposition algorithm reaches the maximum rank limit (`rank_max`) in QP2.

## Problem

The Cholesky decomposition was crashing with exit code 134 (SIGABRT) when `rank_max` was reached:

```
cholesky: rank_max reached
       5120              3,385E-12
Program exited with code 134.
```

The issue was that when the rank limit was hit, the code only exited the inner loop but continued the outer loop, causing the algorithm to run in an inconsistent state and eventually crash.

## Root Cause

The algorithm has nested loops:
- **Outer loop**: `do while ( (Dmax > tau).and.(np > 0) )` - continues until convergence
- **Inner loop**: `do j=1,nq` - processes Cholesky vectors

When `rank >= rank_max`, the code printed the message and exited only the inner loop, but the outer loop continued since the convergence criterion `Dmax > tau` was still true. This led to undefined behavior and crashes.

## Solution

Added proper control flow to terminate both loops when `rank_max` is reached:

1. **Added a flag**: `rank_max_reached` to track when the limit is hit
2. **Modified outer loop condition**: `do while ( (Dmax > tau).and.(np > 0).and.(.not.rank_max_reached) )`
3. **Set flag when limit reached**: Prevents further iterations and ensures graceful termination

## Technical Details

The fix allows the algorithm to complete gracefully with the computed Cholesky vectors up to the rank limit, rather than crashing. The threshold adjustment from the previous commit (`1.e-12` to `1.e-10`) reduces the likelihood of hitting the rank limit, while this fix ensures robust handling when the limit is encountered.

This addresses the crash behavior reported in issue #370 while maintaining the mathematical correctness of the Cholesky decomposition.

<!-- START COPILOT CODING AGENT TIPS -->
---

💬 Share your feedback on Copilot coding agent for the chance to win a $200 gift card! Click [here](https://survey.alchemer.com/s3/8343779/Copilot-Coding-agent) to start the survey.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64e5ab272fd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.