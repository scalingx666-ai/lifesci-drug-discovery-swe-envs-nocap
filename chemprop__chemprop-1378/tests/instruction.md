# Issue

**Title:** Add --version CLI flag and version in help text

## Description

> [!NOTE]
> This PR was handled entirely by Qwen 3.6 27b running locally via `opencode` with @JacksonBurns' supervision

Add a `--version` flag that prints the package version and exits, and include the version in the `chemprop -h` usage line.

Previously, `chemprop --version` was not recognized (treated as a missing subcommand) and `chemprop -h` showed no version information. Now:

 - `chemprop --version` prints `chemprop 2.3.0rc1` and exits with code 0
 - `chemprop -h` displays `usage: chemprop 2.3.0rc1 [-h] [--version] ... `

Tests added to verify both behaviors.

 

## Checklist
- [x] linted with flake8?
- [x] unit tests added

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49b0938ae22e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.