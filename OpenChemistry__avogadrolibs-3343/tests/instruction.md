# Issue

**Title:** Handle optional dependencies in macOS packaging fixups

## Description

Run install-name fixups only for binaries that are present. This lets packaging proceed when optional Open Babel helpers or libraries are missing, while still failing if a fixup fails. Run the mocked fixup tests in the macOS workflow.

Extracted from #2868. Local validation: python3 .github/scripts/test_fix_macos_plugins.py (4 passed). Actual macOS packaging is pending CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55ecd967dfa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.