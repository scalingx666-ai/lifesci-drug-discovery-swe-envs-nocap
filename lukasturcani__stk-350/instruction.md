# Issue

**Title:** Add section for molecular writers to TOC

## Description

Related Issues: #299

This commit adds a new section to the TOC in the documentation for
the molecular writers. For the table of contents holding the
molecular writers, I added a new file, `docs/source/writers.rst`,
rather than adding the TOC into the
`src/stk/molecular/writers/__init__.py` because that file
automatically adds a second TOC, which contains a list of the
subpackages. I want the page to only show the single TOC I'm adding,
and having a separate file makes this easier to configure. Also, this
is what I did for `docs/source/mutation.rst` and
`docs/source/polymer.rst` so it's consistent.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f36347047ceb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.