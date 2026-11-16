# Issue

**Title:** Match the double-bonded phosphorus row in TPSA

## Description

`TPSADescriptor` has a table row for phosphorus with one single and one double bond, `[P](-*)=*`, worth 34.14. Its key lists three neighbours, but that atom has two, so the row can never match. `CP=C` returns 0.0, and `CP=NC` returns 12.36, the nitrogen's share alone.

This changes the neighbour count in that key from 3 to 2 and nothing else. Open Babel's `psa.txt`, a transcription of Ertl's table, gives 34.14 for this fragment, and RDKit's `CalcTPSA(..., includeSandP=True)` returns 34.14 and 46.50 for these two molecules. I did not check the paper itself.

Only molecules with this fragment change: none of the 5,675 molecules in a sweep contain it, and the three dedicated phosphorus probes do.

`testPhosphorusDoubleBond` checks `CP=C` (34.14) and `CP=NC` (46.50), with `CP(C)C` (13.59) as a phosphorus control that already matched.

On Linux with JDK 21, `mvn -pl descriptor/qsarmolecular,tool/formula test` reported 1460 tests in `qsarmolecular` (54 skipped) and 273 in `formula`, with 0 failures. With the production file restored to the base and the new test kept, the test fails at the first molecule with `expected: <34.14> but was: <0.0>`.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08b12b2a156f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.