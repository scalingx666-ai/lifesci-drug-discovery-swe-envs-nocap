# Issue

**Title:** put() should update all matching entries.

## Description

This PR does two things. First it does the same thing as the previous PR but for `ConstrcutedMoleculeMongoDb`.

Second it introduces a separate collection for position matrices of building blocks in the MongoDB database. This is necessary because usually a collection of position matrices holds position matrices acquired through some specific method. For example, you would have a collection of position matrices collected from XTB and another collection for position matrices collected from macromodel.

```python

xtb_db = stk.ConstructedMoleculeMongoDb(
    position_matrix_collection='xtb_matrices',
)
macromodel_db = stk.ConstructedMoleculeMongoDb(
    position_matrix_collection='macromodel_matrices',
)

molecule = stk.ConstructedMolecule(...)
xtb_molecule = molecule.with_position_matrix(
    position_matrix=get_xtb_position_matrix(molecule),
)
macromodel_molecule = molecule.with_position_matrix(
    position_matrix=get_macromodel_position_matrix(molecule),
)

xtb_db.put(xtb_molecule)
macromodel_db.put(macromodel_molecule)

```

Note the issue in the last two lines of code 

```python

# Currently, the position matrices of building blocks of xtb_molecule
# are also deposited into the xtb_matrices collection.
xtb_db.put(xtb_molecule)
# Currently the position matrices of building blocks of macromodel_molecule
# are also deposited into the macromodel_matrices collection.
macromodel_db.put(macromodel_molecule)

# This makes no sense because the building blocks of xtb_molecule and
# macromodel_molecule are the exact same BuildingBlock instances, which
# may not have been optimized with either of the two mehods!

```

Therefore a separate argument is needed, which allows the user to specify where the position matrices of building blocks should be deposited.

```python

db = stk.ConstructedMoleculeMongoDb(
    position_matrix_collection='xtb_matrices',
    building_block_position_matrix_collection='etkdg_matrices'
)

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2164cad20594`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.