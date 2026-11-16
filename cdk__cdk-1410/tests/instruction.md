# Issue

**Title:** Reject proton removal beyond the available hydrogen count

## Description

`adjustProtonation` returns `true` when asked to remove two protons from HCl, removes its only hydrogen, and applies the full charge change.

Check each hydrogen isotope's count against the requested removal before selecting it. If no eligible isotope can supply enough hydrogen, the existing `false` return leaves the formula and charge unchanged.

Add a regression for HCl with a change of -2, checking the return value and unchanged formula string and charge. Existing tests cover single removal, addition, and isotope preference.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), e79914fbc0 against 19d89e4020:

- Module and dependency build passed.
- MolecularFormulaManipulatorTest: 97 passed, no failures, errors or skips.
- tool/formula: 285 passed, no failures, errors or skips.
- With the production file from 19d89e4020 and the new test kept, the test run fails (`expected: <false> but was: <true>`).

Prepared with AI assistance (Claude Code and OpenAI Codex).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41b6dbe0d9c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.