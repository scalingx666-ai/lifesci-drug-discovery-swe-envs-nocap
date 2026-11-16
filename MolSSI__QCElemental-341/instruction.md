# Issue

**Title:** Add dependency on `packaging` for version parsing

## Description

## Description
Running
```bash
python -m venv ./venv
source ./venv/bin/activate
python -m pip install -e .
```
inside of QCEngine, followed by
```python
"""qcengine_example.py: Example of running a Q-Chem calculation through QCEngine."""

import qcengine as qcng
import qcelemental as qcel

mol = qcel.models.Molecule.from_data("""
O  0.0  0.000  -0.129
H  0.0 -1.494  1.027
H  0.0  1.494  1.027
""")

inp = qcel.models.AtomicInput(
    molecule=mol,
    driver="energy",
    model={"method": "hf", "basis": "sto-3g"},
)
ret = qcng.compute(
    inp,
    "qchem",
    local_options={"ncores": 1},
)

with open("qcengine_example.json", "w", encoding="utf-8") as handle:
    handle.write(ret.json())
```
produces an output with the error
```
QCEngine Execution Error:
Traceback (most recent call last):
  File "/home/eric/development/forks/MolSSI/QCEngine/qcengine/util.py", line 117, in compute_wrapper
    yield metadata
  File "/home/eric/development/forks/MolSSI/QCEngine/qcengine/compute.py", line 108, in compute
    output_data = executor.compute(input_data, config)
                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/eric/development/forks/MolSSI/QCEngine/qcen
gine/programs/qchem.py", line 106, in compute
    if parse_version(self.get_version()) < parse_version(qceng_ver):
                     ^^^^^^^^^^^^^^^^^^
  File "/home/eric/development/forks/MolSSI/QCEngine/qcengine/programs/qchem.py", line 89, in get_version
    self.version_cache[which_prog] = safe_version(mobj.group(1))
                                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/eric/development/forks/MolSSI/QCEngine/venv/lib/python3.12/site
-packages/qcelemental/util/importing.py", line 134, in safe_version
    import pkg_resources
ModuleNotFoundError: No module named 'pkg_resources'
```
which means setuptools needs to be a runtime dependency.  This bit of setuptools has been transitioned to `packaging` long ago and isn't even the build backend for qcel.

QCEngine tests against NWChem look clean.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Use `packaging` instead of `setuptools` to provide version parsing

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4c3bd369cb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.