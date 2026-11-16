# Issue

**Title:** Skip unknown double-bond parity when reading InChI

## Description

`InChIToStructure` reads `InChI=1S/C4H8/c1-3-4-2/h3-4H,1-2H3/b4-3?` as a defined Z double bond and regenerates it with `/b4-3-`. The double-bond branch defaults to TOGETHER for every parity except EVEN.

The [InChI Technical Manual, section 3.2](https://www.inchi-trust.org/download/104/InChI_TechMan.pdf) identifies `?` as unknown or undefined stereo by default. Skip double-bond parities other than ODD/EVEN before rearranging bonds or creating a stereo element, following the existing tetrahedral parity handling. Bond orders are assigned before this step.

Add tests that unknown-parity butene retains one double bond without a stereo element, and that an unknown double bond beside a defined tetrahedral centre retains exactly that centre and its configuration. The existing E/Z controls remain unchanged. Literal `?` preservation on regeneration is outside this change.

Checked on Linux (JDK 21, Maven, JNA InChI 1.3.1): with production code at `6e51f7b458` the new tests fail (a stereo element is created: `expected: <false> but was: <true>`); with the change, `InChIToStructureTest` (34 run, 1 skipped) and the `storage/inchi` module (152 run, 2 skipped) pass. The guard also covers extended cis/trans records; that path is not exercised by the new tests.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84ff2d7c4aa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.