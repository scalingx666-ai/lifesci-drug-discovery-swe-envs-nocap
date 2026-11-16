# Issue

**Title:** Hessian parsing fixes for Turbomole Harness

## Description

## Description
Parsing Turbomole Hessian was faulty for bigger molecules. This was found . As the present code in QCEngine is derived from my own project [pysisyphus](https://github.com/eljost/pysisyphus) I want to provide my fix here.

I didn't add test for a big Hessian, but I have a 500 kb Hessian file at hand. If you tell me where I could put this file I could include a proper test. I refrained from including the file inline as a pytest.fixture ...

## Changelog description
Fixed Hessian-parsing for bigger molecules >= 60 atoms.

## Status
- [x] Code base linted
- [x] Ready to go

Regarding the linting ... i formatted the files I modified using Black, but there appear to be other "unlinted" files, which I did not modify here: 

```bash
make format
[...]
black qcengine
reformatted qcengine/config.py
reformatted qcengine/programs/cfour/runner.py
reformatted qcengine/programs/gamess/runner.py
reformatted qcengine/programs/nwchem/runner.py
reformatted qcengine/programs/molpro.py

All done! ✨ 🍰 ✨
5 files reformatted, 96 files left unchanged.
```
Locally, I ran all Turbomole tests and they passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd5eec6bfefa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.