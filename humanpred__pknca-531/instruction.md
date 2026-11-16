# Issue

**Title:** docs: add CLAUDE.md guide for AI assistants

## Description

## Summary

- Adds a comprehensive `CLAUDE.md` file documenting the PKNCA codebase for AI assistants, covering: project overview, quick-reference commands, repository structure, core workflow (PKNCAconc, PKNCAdose, PKNCAdata, units system), S3 class architecture, naming conventions, code style, testing patterns, CI/CD, and contributing guidelines
- Adds `^CLAUDE\.md$` to `.Rbuildignore` so the file is excluded from CRAN package builds

## Test plan

- [ ] Verify `CLAUDE.md` renders correctly as markdown
- [ ] Verify `.Rbuildignore` correctly excludes `CLAUDE.md` from R CMD build
- [ ] Confirm R CMD check still passes cleanly

https://claude.ai/code/session_01NxLqCpfvaEd7iuuDA9njiz

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e89763315fce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.