# Issue

**Title:** fix: frontend CSP font-src, MOL format conversion, and molblock heade…

## Description

…r parsing

- Add data: to CSP font-src directive for inline data fonts
- Wire up generate2DCoordinates for MOL Block output format in FormatConversionView
- Fix formatMolblockForBackend to detect name line presence before prepending blank line
- Add baseUrl to useMemo dependency in HighlightedMoleculeCard

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca0a9ee1df61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.