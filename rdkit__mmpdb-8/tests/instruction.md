# Issue

**Title:** update setup.py and copyright dates

## Description

I want to update PyPI, the Python Package Index, for version 2.2. This lets people install or update mmpdb using "pip install mmpdb".

I added some changes to the setup.py so that Christian is listed as the maintainer, with the maintainer email as the RDKit mailing list.

I added the content of README.md for the "long description", which PyPI uses for its display.

I extended the copyright date from 2017 to 2019.

You can see the result on the test PyPI server, at https://test.pypi.org/project/mmpdb/ .

Compare it with https://pypi.org/project/mmpdb/

Let me know if there's anything else to update.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `441a3087ca68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.