# Issue

**Title:** Hotfix/test command

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**
Improve test command behavior, add exit conditions, and update docs

- [x] Exception handling in test command now warns and generates report instead of failing.
- [x] Added exit conditions:
  - [x] Stop if simple run fails (after partial report generation).
  - [x] Stop deep check if inconsistency fails in shallow check.
- [x] Added docs on parsing Dockerfile and YAML in test command.
- [x] Simplified test usage: `--inspect` replaces basic test.
- [x] Updated parser.py to raise error if conda packages lack version.
- [x] I added type checking from run.sh and ersilia
- [x] I fixed slight but problem for some models Dockerfile/install.yml parsing issue
- [x] I think now we can handle all possible cases of packge specs from test command including this forms [syba=1.0.2.alpha]


Related to #1633

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b63a9b1c931`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.