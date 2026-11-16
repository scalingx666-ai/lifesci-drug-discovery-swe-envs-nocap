# Issue

**Title:** Feature/isolate repair

## Description

## Motivation

The current repair function from the GA uses QP-optimization to find feasible input space points (considering linear and N-choose-k constraints).
This would be beneficial to use also in other areas. This PR isolates the linear projection (QP-optimization) from the GA code. 

## Test Plan

Mostly, the old tests can be used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1976058db708`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.