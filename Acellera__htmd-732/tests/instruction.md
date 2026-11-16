# Issue

**Title:** New small implementation.

## Description

Periodic Table:
 - listHybridization and listBondTypes: These will just show the pair index:value. Index is
                                        used from the code; value is chemist readable
 - getHybridization and getBondType: Convert index to value

SmallMol:
 - modified listPropsAtoms and listProp: These will not show anymore properties that starts
                                         with "_".
 - implemented 'all' selection in the "get" method

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17069a37cfea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.