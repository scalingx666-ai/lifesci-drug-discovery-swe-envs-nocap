# Issue

**Title:** implementation of option align_method

## Description

Hi @GHeinzelmann,
This pull request contains my latest implementation of option `align_method` which defaults to mustang, thus BAT.py should behave the same as before unless `align_method = vmd` is written in the input file.
I tested my commits with `align_method = vmd` on my CDK2 system of multiple protein chains, and was able to successfully finish ABFE calculations. To my surprise, BAT.py already works for this multi chain protein, without me committing any changes about differentiating different protein chains in pdb files: although pdb4amber prints warning when there is no `TER` line between the two protein chains in the pdb file, tleap seems to be smart enough to know (perhaps from 3d coordinates) that there are two chains, and not draw a chemical bond between the two chains.

One small change about pdb4amber below, solves histidine residue naming problem that could arise from some programs (such as Maestro) exporting pdb files with residue names incompatible with Amber conventions. Currently I put this change under `align_method == 'vmd'`, but you may consider incorporating this change about pdb4amber, even when using mustang for alignment.
```
      # Call pdb4amber twice, because pdb4amber can only correct residue names of histidines before removing H (-y option).
      # Maybe we should call pdb4amber twice like this, when align_method == 'mustang' too.
      sp.call('pdb4amber -i complex.pdb -o temp.pdb', shell=True)
      sp.call('pdb4amber -i temp.pdb -o aligned_amber.pdb -y', shell=True)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05e60489a749`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.