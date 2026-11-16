# Issue

**Title:** Functionality to plot dielectric loss function

## Description

## Description of work

This PR adds a functionality to plot the loss function as determined from the dielectric function. It is heavily based on the optical absorption routines and reads in from a `vasprun.xml`

This addresses issue #22.

## To test

* Run `setup.py install` on this branch of `sumo`
* In `tests/data/Cs2SnBr6` run `sumo-loss` and `sumo-loss -a`; check that results are sensible
* Check that docstrings produce sensible documentation for the api

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d8a0406f277`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.