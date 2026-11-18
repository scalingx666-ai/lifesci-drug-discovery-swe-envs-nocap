# Issue

**Title:** Merge MC Rattling to Develop

## Description

This branch switches to using the `hiphive` Monte Carlo rattling functions. I have tested that it works similar to the original rattle function (see attached notebooks), with similar atomic displacements generated, but with some key benefits. 

[Defect_Distortion_Tests.zip](https://github.com/SMTG-UCL/defect-finder/files/8488888/Defect_Distortion_Tests.zip)

- Includes a penalty for small interatomic distances. At present, I have this setup to use 85% of the bulk bond length as the penalty threshold, where interatomic distances below this are heavily penalised (see https://hiphive.materialsmodeling.org/_modules/hiphive/structure_generation/rattle.html). This choice was motivated by looking at V_Cd and Cd_i as example cases. Note that I also set this to ignore the defect and the distorted neighbours, as these can have bond lengths smaller than this. 
- Includes the `active_atoms` tag, for selecting a subset of atoms to
 rattle (so now used to avoid rattling the defect and its distorted neighbours, which should give slightly improved consistency in results for distortion ranges (i.e. sometimes before had a -20% distortion + rattling giving overall bond lengths that were actually slightly expanded rather than contracted etc), while retaining the symmetry-breaking effect through the rattled distortion of the defect environment).
- Functions now setup to have the rattling method be fully customisable, through keyword arguments in all functions that use rattling.

I've included tests for these functions.

The penalty for small interatomic distances _should_ help reduce the cases where calculations crash/explode, due to too small initial interatomic distances, and the sporadic cases where the relaxations get stuck in a high-energy metastable minimum. 
More testing for this is required however, and so I am currently rerunning the V_Cd^0 rattling and nearest_neighbours tests to see how this new version compares.
It could also be a good idea to have a minimum interatomic distance for creating the distortions, to avoid certain interstitials where -60/50% gives structures that will explode. I have gathered data from Jiayi and Bodoo for these cases, to see if we can determine a reasonable default minimum interatomic distance to apply with distortions (but can optionally be changed)(note AIRSS typically uses 1.5 Angstrom for this https://airss-docs.github.io/tutorials/examples/)
Will also test the new rattling methods on this data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b795d533401f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.