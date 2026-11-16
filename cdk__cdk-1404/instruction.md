# Issue

**Title:** Return the configured tolerance in IsotopePatternRule

## Description

IsotopePatternRule.getParameters() always returns 0.001 for the tolerance, even after setParameters() changes the value used for validation. Return the configured value through IsotopePatternSimilarity.getTolerance().

Check the configured tolerance and matching validation scores after rebuilding a rule from getParameters(), using the existing C5H13N2O2 spectrum.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), 052852293 against 5118b85c0:

- Module and dependency build passed.
- IsotopePatternRuleTest: 7 passed, no failures, errors or skips.
- tool/formula: 284 passed, no failures, errors or skips.
- With the production file from 5118b85c0 and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5118b85c0875`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.