# Issue

**Title:** Add evaluate_many to Benchmark

## Description

Right now there is a way to evaluate a single random seed for a Benchmark group but no way to actually run the calculations needed to submit an entry here https://docs.google.com/forms/d/e/1FAIpQLSeAs_PhRyT9iqPc4WX0HOUFI3WdQNATKt7kZ7ztzf5DKaolkA/viewform.  This PR adds that functionality.  It is not currently tested with multi-class classification methods.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15e272a64423`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.