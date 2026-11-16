# Issue

**Title:** Add benchmarks

## Description

Requested Reviewers: @andrewtarzia 
*Note for Reviewers: If you accept the review request add a :+1: to this post*

This commit adds a new folder for holding benchmarks, which can be
run with `pytest benchmarks`. The `pytest.ini` file has been updated
so that pytest is able to collect files and functions with the
`benchmark` prefix. This just means that benchmarks can be called
`benchmark_something` rather than having to call them `test_something`.

Currently I'm only adding a single benchmark for the kagome COF but
more can be added as the need arises.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d955e4c74ce7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.