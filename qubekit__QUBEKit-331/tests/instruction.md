# Issue

**Title:** Add virtual sites to offxmls

## Description

## Description
This PR will allow qubekit to write offxmls with virtual sites, these will use a plugin which allows for LocalCoordinateSites directly as not all of our site types can be directly converted to the currently available sites in openff. This should also make it easier as we derive and store our sites with the local coordinate positions. 

Note this will mean that the qubekit plugin is required to use the offxml to build an openmm system. 


## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] Write individual offxmls with sites
  - [x] Write combined offxmls with sites
  - [x] Check that two different v-site handlers are compatible

## Questions
~~- [ ] Does this mean we need to convert TIP4P vsites to local coordinate types or can we mix the two types of vsite handlers safely?~~

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27834216759f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.