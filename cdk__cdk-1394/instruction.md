# Issue

**Title:** Accept V2000 Sgroup data lines longer than 80 columns

## Description

MDLV2000Reader clips SCD and SED data after 68 payload characters, dropping column 80 and the rest of longer lines.

Read the payload from column 12 to the end of the line, matching the behavior observed with BIOVIA. Preserve trailing spaces and empty SED terminators. MDLV2000Writer already writes at most 69 data characters per line.

Add dataSgroupReadsFullLines with exact-value assertions for the 100-character SED example, 68- and 69-character SED payloads, and a 138-character value continued over two SCD records and terminated by an empty SED.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), the branch head 1c4d88fb0 against d12b2fc991:

- Module and dependency build passed.
- MDLV2000ReaderTest: 133 passed, no failures, errors or skips.
- storage/ctab: 665 passed, no failures, errors or skips.
- With the production file from d12b2fc991 and the new test kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.