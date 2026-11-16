# Issue

**Title:** Add CandidatesProtocol

## Description

Prepares #796 

- Adds narwhals as a hard dependency for backend-agnostic dataframe operations
- Introduces `CandidatesProtocol` along with `ProductCandidates` and `TableCandidates` classes for representing discrete candidate sets, backed by narwhals lazy frames
- Adds `DiscreteParameter.is_finite` property and `InfiniteSpaceError` exception
- Enables validation for extra columns in candidate tables

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b00b8c34efdb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.