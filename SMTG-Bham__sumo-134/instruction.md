# Issue

**Title:** Add option to plot absorption data as a function of wavelength

## Description

Add option to `sumo-optplot` to plot the absorption data as a function of wavelength in nanometres, as is commonly done experimentally.

Tested and all seems to behave as expected.

EG: `sumo-optplot --ymax 1.2e6 --units nm --xmax 2000 --xmin 300 -g 0.1 --bandgap 1.4` gives:
![image](https://user-images.githubusercontent.com/51478689/115076009-de5fe480-9ef3-11eb-9bfe-c8880610dd0d.png)

while `sumo-optplot --ymax 1.2e6 --xmax 4.13 --xmin 0.62 -g 0.1 -b 1.4` (same energy range) gives:
![image](https://user-images.githubusercontent.com/51478689/115077042-51b62600-9ef5-11eb-9d6f-0884d82ecbcb.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `703d232d7096`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.