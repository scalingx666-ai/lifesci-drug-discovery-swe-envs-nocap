# Issue

**Title:** fix gpusim_search.py

## Description

fixed gpusim_search.py to work with the example in README.md

Version tested:
PyQt5              5.12.1     
Python             3.7.1

Commands to reproduce error:

    cd build/
    ./gpusimserver test/small.fsim &
    python python/gpusim_search.py small
    Smiles: CCCc1c2c(n(n1)C)n(c(n2)N)c3ccccc3

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `775a7f8d5dc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.