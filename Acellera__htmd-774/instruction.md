# Issue

**Title:** Fftype fixing

## Description

This is an incomplete PR as per @raimis request. I'll add a comment for when's it's ready. It's basically needing htmd-data changes (a lot).

Resume of changes:
- parmchk2 now does GAFF2
- elements are now guessed by which masses were assigned during fftype
- unittests added to fftype, which include: ethanolamine, three more
  molecules that have all elements recognizable in GAFF(2)
- get ride of Enum in FFTypeMethods (and fixing code accordingly)
- new data to match the changes (still incomplete)

This will fail CI while I do not fix the data.

List of currently failing files:
```
AssertionError: Tests failed for the following files:
/shared/joao/test_parameterize/htmd/htmd/builder/amber.py
/shared/joao/test_parameterize/htmd/htmd/parameterization/esp.py
/shared/joao/test_parameterize/htmd/htmd/parameterization/test.py
/shared/joao/test_parameterize/htmd/htmd/qm/test.py
/shared/joao/test_parameterize/htmd/htmd/qm/psi4.py
/shared/joao/test_parameterize/htmd/htmd/qm/fake.py
```

All make sense. `amber.py` fails because benzamidine was changed to GAFF2 and now the prmtop (the parameters) is obviously different.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75952e05bb42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.