# Issue

**Title:** fix: slience annoying print outs in ip fitting jobs

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Running ip_tunning clogs stdout by emitting non-silenced printouts, and red-herring warnings.
`ip_tune` does set charge/multiplicity via `set_molecular_charge` and `set_multiplicity`:
* https://github.com/psi4/psi4/blob/master/psi4/driver/frac.py#L609
* https://github.com/psi4/psi4/blob/master/psi4/driver/frac.py#L610C5-L610C37

so it should be safe to keep them out.

An example:
```log
...
c: [1.0, 0]
fc: [0.0]
m: [2]
fm: [3]
Following warning is harmless if you've altered chgmult through `set_molecular_change` or `set_multiplicity`. Such alterations are an expert feature. Specifying in the original molecule string is preferred. Nonphysical masses may also trigger the warning.


c: [1.0, 0]
fc: [0.0]
m: [2]
fm: [3]
Following warning is harmless if you've altered chgmult through `set_molecular_change` or `set_multiplicity`. Such alterations are an expert feature. Specifying in the original molecule string is preferred. Nonphysical masses may also trigger the warning.


c: [1.0, 0]
fc: [0.0]
m: [2]
fm: [3]
Following warning is harmless if you've altered chgmult through `set_molecular_change` or `set_multiplicity`. Such alterations are an expert feature. Specifying in the original molecule string is preferred. Nonphysical masses may also trigger the warning.


c: [1.0, 0]
fc: [0.0]
m: [2]
fm: [3]
Following warning is harmless if you've altered chgmult through `set_molecular_change` or `set_multiplicity`. Such alterations are an expert feature. Specifying in the original molecule string is preferred. Nonphysical masses may also trigger the warning.
...
```

```
c: [1.0, 0]
fc: [0.0]
m: [2]
fm: [3]
```
steems from https://github.com/psi4/psi4/blob/master/psi4/driver/qcdb/molecule.py#L1646

and can be silenced by setting `verbose=-1`,
the other is 4 lines below:

https://github.com/psi4/psi4/blob/master/psi4/driver/qcdb/molecule.py#L1650


This PR, adds `quiet` param to `to_dict` in Molecule and `energy` in Driver, and uses that in `ip_fitting` not to post both of them out.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] removed noise from stdout while running `ip_tunning`

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] silences plain `print` from `Molecule.to_dict()` - `qcel.molparse.from_arrays` and warning around setting charge/multiplicity when running `ip_fitting`. This shouldn't change other code paths.

## Questions
- [x] Do psi have any tests that test stdout with pytest?

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab7aaca8dd96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.