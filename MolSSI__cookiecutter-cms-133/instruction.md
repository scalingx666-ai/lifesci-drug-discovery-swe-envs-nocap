# Issue

**Title:** Explicitly use cookiecutter.description as short_description.

## Description

Supersedes PR #132 

* Advise users on brevity.
* Assume (but check) for one-line short description
  for Python package metadata.
* Use short description for package docstring.

The long description was already derived from the README file
for the package metadata, so PR #132 was conceptually divergent.

On review of issue #130, the consensus was that it would be annoying
to require users to enter a long description during `cookiecutter`
execution and that we shouldn't assume users will (or will want to)
update a stub in their `__init__.py` docstring. Instead, this change
generates a PEP-257 compliant docstring for the package, which the user
can edit or extend at their option at some point after the initial
project generation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d52e1e569006`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.