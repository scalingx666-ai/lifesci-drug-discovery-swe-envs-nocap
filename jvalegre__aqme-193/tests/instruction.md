# Issue

**Title:** Adding checks for available functionals and basis sets

## Description

I've added two CSV files (in templates dir) that contain available density functionals for orca and gaussian, and available basis sets for orca. The spelling is such that it matches what is required by each program (ignoring upper or lower case).

There is also a new function in qprep that will use these files to lookup and compare against the current request, which can be called by:

qprep.check_level_of_theory(functional, basis_set, program)

that returns True/False. This doesn't get called automatically, but can be added to workflows as required:

### example usage in a script:
```
import sys
from aqme.qprep import qprep

# user-defined
sdf_file = sys.argv[1]
functional = sys.argv[2]
basis_set = sys.argv[3]

# calculation options
program = 'orca' 

# check whether the functional and basis set make sense!
if qprep.check_level_of_theory(functional, basis_set, program):
        
        qm_input = functional + ' ' + basis_set
        qprep(destination='.', files=sdf_file, program=program, qm_input=qm_input) 
        
else: pass
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bedec930d7c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.