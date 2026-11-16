# Issue

**Title:** Higher Precision Gradients from NWChem

## Description

## Description
NWChem only prints gradients to an accuracy of 6 decimal places to stdout. I explored getting more accurate gradients from NWChem as a hope for allowing NWChem to work better with geoMETRIC. Reading gradients with higher accuracies did not seem to be the (only) issue with NWChem+geometric, but here is the result of that line of testing!

The full-accuracy versions of gradients are stored in checkpoint file of NWChem. The new code accesses and prints them using a Python script that runs during the NWChem execution.

See discussion here:
http://www.nwchem-sw.org/index.php/Special:AWCforum/st/id2155

I also implemented Hessian support while I was at it

## Changelog description
Improved gradient output and added Hessian support for NWChem

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55c1b6de605c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.