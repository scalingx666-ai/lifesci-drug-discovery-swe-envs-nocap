# Issue

**Title:** Write PDB element symbols in columns 77-78

## Description

`PDBWriter` previously placed two-letter element symbols in columns 78-79. For chlorine, this left `l+` in the charge field, which `PDBReader` cannot parse.

The [wwPDB v3.3 ATOM/HETATM format](https://www.wwpdb.org/documentation/file-format-content/format33/sect9.html) requires element symbols to be right-justified in columns 77-78. This change removes one preceding space and writes the symbol in a two-character field. It also converts the element field to upper case with `Locale.ROOT`, matching the specification's `MG` and `FE` examples. One-letter output, charge text, residue-name formatting and coordinate handling are unchanged.

The regression test checks the exact fields `CL`, ` C` and `BR`, then reads Cl-C-Br back with the same elements, both bonds and x coordinates.

Checked on Linux (JDK 21, Maven) at `b852c2b2b`: the module/dependency build, all 20 `PDBWriterTest` tests and the 55-test `storage/pdb` suite pass. With the production file restored to `733fd7f04` and the updated test retained, the first field assertion fails with `expected: <CL> but was: <Cl>`, confirming coverage of the uppercase follow-up.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e51f7b45816`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.