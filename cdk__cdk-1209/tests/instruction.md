# Issue

**Title:** dependency updates 08-Aug-2025, use <release> instead of <source> and <target>

## Description

- bumped test dependencies junit, assertj, and mockito to latest versions
- `cdk-bundle.pom`: update maven-compiler-plugin configuration to use <release> instead of <source> and <target>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbfa6bdae330`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.