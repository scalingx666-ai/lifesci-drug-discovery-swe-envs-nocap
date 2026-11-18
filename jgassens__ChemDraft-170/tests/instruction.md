# Issue

**Title:** Record every component bundled in the vendored OPSIN jar

## Description

The vendored OPSIN 2.9.0 jar bundles more than our licence record listed. This corrects NOTICE, `resources/opsin/BUILD.md` and `docs/architecture/dependency-inventory.md`:

- **jna-inchi 1.3.1**: LGPL-2.1-or-later. Added to NOTICE with a written source offer (upstream tag `jna-inchi-1.3.1`).
- **JNA 5.10.0**: LGPL-2.1+ or Apache-2.0; ChemDraft elects Apache-2.0.
- **InChI 1.07.2**, inside the jna-inchi native libraries: MIT (upstream LICENSE at tag v1.07.2).
- **opsin-inchi 2.9.0** and **commons-cli 1.11.0**: Apache-2.0.
- The "no copyleft / all permissive" claim is removed, and "Unmodified" now matches BUILD.md's record of the macOS code-signing change.

Each licence was read from the jar's POMs, Maven Central, or the upstream repository at the shipped tag. Docs only.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfd18fd2acc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.