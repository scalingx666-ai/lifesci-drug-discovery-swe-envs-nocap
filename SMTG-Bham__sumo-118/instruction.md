# Issue

**Title:** Fix band structure plotting for latest versions of pymatgen

## Description

This PR fixes plotting for versions of pymatgen >= 2020.10.9.1.

A recent pull request to pymatgen (materialsproject/pymatgen#1968) changed the internal behaviour of `BSPlotter` and broke `sumo-bandplot`. Specially, the `BSPlotter` base class now supports plotting multiple band structures, provided they are calculated on the same path (it automatically handles scaling the distance between high symmetry points). This is definitely something we should support in sumo but for now this PR just allows a single band structure to be plotted again.

I also fixed another bug due to the requirement that band structures contain branches.

Tagging @ajjackson in case he can think of any reasons not to merge this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e72fbbfe72c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.