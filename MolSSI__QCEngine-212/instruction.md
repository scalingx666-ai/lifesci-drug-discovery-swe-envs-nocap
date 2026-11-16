# Issue

**Title:** CI for NWChem

## Description

## Description
try ubuntu's nwchem package, as recc by #211 

## Changelog description
- [x] Adds CI testing of NWChem 6.6 through Ubuntu xenial pkg

## Questions
- [ ] networkx is req'd for the NWChem interface for all but energies to align arrays, but at present it's only an optional requirement for qcel. There's a nice "install me" message, but in production users would probably like to know to install the pkg _before_ the QC job, not after. But I'm hesitant to put the check in `def found` because if ppl are only looking at the boolean, it'd be unintuitive for `which nwchem` to be present but nwchem harness not be available. Where to address this? require networkx? or have a distinction btwn nwchem-found and nwchem-ready?
- [ ] combine this CI lane with another?

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd086f628bf9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.