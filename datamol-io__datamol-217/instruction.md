# Issue

**Title:** Added function to get the number of stereoisomers

## Description

## Changelogs

- Added `datamol.isomers._enumerate.count_stereoisomers`
- Added unit tests to count stereoisomers for only undefined and all possible stereoisomers.
---

The step [`Chem.FindPotentialStereoBonds(mol, cleanIt=clean_it)`](https://github.com/datamol-io/datamol/blob/9e94d026534b2a534250dfbfab924ab6f089e477/datamol/isomers/_enumerate.py#L85),   the information on bond is cleared if `cleanit=True`.
Therefore,  `cleanit` should be disabled when performing enumeration or counting only on undefined stereochemistry when the molecules have defined stereo information on bonds.

See example below:
![image](https://github.com/datamol-io/datamol/assets/6717019/a857da07-e93a-4073-a1e7-eb131a477ace)

Reproduce the error
```
import datamol as dm
from rdkit import Chem

from rdkit.Chem.EnumerateStereoisomers import GetStereoisomerCount, StereoEnumerationOptions, EnumerateStereoisomers
n_variants= 20
undefined_only= True # <-
rationalise = True
timeout_seconds= None
clean_it= True
stereo_opts = StereoEnumerationOptions(
        tryEmbedding=rationalise,
        onlyUnassigned=undefined_only,
        unique=True,
    )
mol  = dm.to_mol('Br/C=C\Br')
Chem.AssignStereochemistry(mol, force=False, flagPossibleStereoCenters=True, cleanIt=clean_it)  # type: ignore
Chem.FindPotentialStereoBonds(mol, cleanIt=clean_it)  # type: ignore
dm.to_image(list(EnumerateStereoisomers(mol, options=stereo_opts)))
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e94d026534b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.