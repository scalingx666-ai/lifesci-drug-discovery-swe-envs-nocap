# Issue

**Title:** yq: auto-generated tool wrapper (issue #1939)

## Description

Adds a new Galaxy tool wrapper for `yq` (v4.53.3), the portable command-line YAML/JSON/XML processor. The tool wraps `yq eval` and `yq eval-all` with support for input/output format selection, pretty printing, indent control, null-input mode, front-matter handling, and security flags. Expressions are passed via a configfile to avoid Galaxy sanitization issues with special characters. Includes macros, `.shed.yml`, and 6 passing tests covering read, identity, create, merge (multi-doc), and XML-to-YAML conversion workflows.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d2decedba49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.