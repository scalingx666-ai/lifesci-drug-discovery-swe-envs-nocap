# Issue

**Title:** Oxo handling

## Description

This branch adds additional handling for OXO-bound complexes. 

OXO ligand compounds are particularly relevant for actinides and catalytic water-based systems.

This change adds 4 basic functionalities: 

1. Change logic of handling oxos to force trans oxos by default for only actinide systems with the option to turn this off.
2. Add tabulated experimental metal-oxo distances and enable setting of average experimental distance for oxos.
3. Enable 'ff_preopt' for oxos and keywords options allowing for cleaning more crowded ligands around metal-oxo centers. 
4. Allow (though not recommended) for 'override_oxo_opt' to still perform XTB or UFF optimization of fully build molecules with oxos.

If you are running actinides with oxos - the following parameters are suggested for MOST cases:
parameters = { 'force_trans_oxos':True,
                          'ff_preopt':True,
                          'override_oxo_opt':False}

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6fdcfba6173`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.