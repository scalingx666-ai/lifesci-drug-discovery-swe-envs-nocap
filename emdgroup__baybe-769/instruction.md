# Issue

**Title:** Add AGENTS.md

## Description

`AGENTS.md` files contain content intended for agentic operators. They are recognized by most coding frameworks (most importantly `claude` and `opencode`) and are injected into the context whenever an agent reads a folder where such a file is contained. They lead to more consistent code being generated and generally more in line with what has already been done without explicitly having to state this over and over again.

The content here is meant as a start and not as complete. We can continue to add rules as we evolve.

The content has been produced in the following manner:
- Analyze the entire code base and the last 200 PRs including comments
- Extract from this rules and conventions that apply to this repo
- The resulting files have then been compressed
- I then did one coarse round of human review and curation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `250cb75c0832`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.