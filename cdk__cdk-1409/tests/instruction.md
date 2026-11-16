# Issue

**Title:** Add lone pairs to the clone in PiElectronegativityDescriptor

## Description

With `lpeChecker=true`, `PiElectronegativityDescriptor` configured a clone but added lone pairs to the caller's container. For inputs initially lacking lone pairs, the first calculation used an unprepared clone while mutating the input, so later calls could return a different value.

Add lone pairs to the existing clone used for calculation. This changes the first-call value for affected inputs without lone pairs, including from zero for methyl fluoride, to match a pre-saturated input. The caller's container remains unchanged.

Add an explicit-hydrogen methyl-fluoride regression with perceived atom types, prepared aromatic/ring flags, no initial lone pairs, and `lpeChecker=true`. It checks input lone-pair counts after both calls, repeatability, and agreement with a separately saturated copy.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), 4ba6f6c805 against 19d89e4020:

- Module and dependency build passed.
- PiElectronegativityDescriptorTest: 24 passed, no failures, errors or skips.
- descriptor/qsaratomic: 382 passed, no failures, errors or skips.
- With the production file from 19d89e4020 and the new test kept, the test fails: the input gains three lone pairs, repeated calculations differ, and the first result disagrees with the pre-saturated copy.

Prepared with AI assistance (Claude Code and OpenAI Codex).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19d89e4020a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.