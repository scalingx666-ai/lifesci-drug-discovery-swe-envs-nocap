# Issue

**Title:** Release 0.1.8

## Description

This release allows users to submit multiple SMILES strings (i.e. list of strings) to the "from_smiles" function:

```python
from padelpy import from_smiles

# obtain descriptors for propane and butane
descriptors = from_smiles(['CCC', 'CCCC'])
```

 In issue  it was pointed out that multiprocessing/multithreading could not be utilized for the "from_smiles" function. The updated implementation allows for this. If your code/pipeline currently supplies one SMILES string to the "from_smiles" function, it will continue to operate as expected.

Additionally, error handling/reporting has been updated to ensure proper feedback, and the default maximum runtimes for the "from_smiles" and "from_mdl" functions has been increased from 12 seconds to 60 seconds.

Unit tests for submitting multiple SMILES strings and proper exception handling/reporting have been included.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd09a3c29786`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.