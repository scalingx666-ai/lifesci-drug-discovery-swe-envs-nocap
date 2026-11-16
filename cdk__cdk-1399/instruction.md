# Issue

**Title:** Preserve SD property values containing angle brackets

## Description

SD property values such as `p < 0.05 and q > 0.1` can be mistaken for data headers, losing the value and creating an extra property. SD data header lines must begin with `>`.

Require that marker before extracting a field name. Keep the existing extraction logic for headers beginning with `>`, including spacing after the marker, registry numbers and trailing text. Add direct header assertions and an SDFWriter round trip through MDLV2000Reader and IteratingSDFReader that checks both original properties and the exact property map.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), e7adaabfc against d12b2fc991:

- Module and dependency build passed.
- MDLV2000ReaderTest: 135 passed, no failures, errors or skips.
- storage/ctab: 667 passed, no failures, errors or skips.
- With the production file from d12b2fc991 and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.