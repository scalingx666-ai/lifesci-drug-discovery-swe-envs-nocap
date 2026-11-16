# Issue

**Title:** Improve performance of NWChem harvester

## Description

## Description
Reduces performance issues in the NWChem harness by using `atoms_map=True`. I had hit an edge-case (script to reproduce below) that caused memory usage to spike during molecular alignment.

## Changelog description
Improve performance of NWChem harness

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

```python
from qcengine import compute_procedure
from qcelemental.models import Molecule
import json

# Re-create the problematic task task
mol = Molecule.from_data('''17
1 2 CC(C)(C)C_oxidized
C                    -0.018590000703     1.534862999948     0.010398998953
C                     0.002102997861    -0.004137001598     0.001969999753
C                     0.746440000483    -0.513907998052     1.248875997535
C                    -1.441902000132    -0.536735999114     0.013115000987
C                     0.722350001733    -0.500496001647    -1.264456001221
H                     0.997769001867     1.944204999076     0.004355001441
H                    -0.541819000228     1.928414001853    -0.868198998732
H                    -0.527584000967     1.918884001840     0.901485002006
H                     0.255496002037    -0.176026999637     2.168331000349
H                     0.778153998185    -1.608924001759     1.270889002192
H                     1.779648000149    -0.149758002595     1.269439998571
H                    -1.998718999074    -0.188888000854    -0.864080999888
H                    -1.459568999361    -1.632271998808     0.006498999953
H                    -1.980888002537    -0.199795999491     0.905615997443
H                     1.754825001002    -0.135540000506    -1.301181000186
H                     0.753970001687    -1.595239997685    -1.298223000122
H                     0.213582002473    -0.153439001607    -2.170672000953
''', molecular_charge=1.0)
task = {
    "initial_molecule": mol,
    "input_specification": {
        "driver": "gradient", 
        "model": {"method": "b3lyp", "basis": "6-31g(2df,p)"},
    }, 
    "keywords": {"program": "nwchem"}
}

compute_procedure(task, 'geometric', raise_error=True)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f03ff5dcd9b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.