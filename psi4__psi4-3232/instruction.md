# Issue

**Title:** SAPT(DFT) auto compute GRAC

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
I have added an option to compute the necessary GRAC shifts for SAPT(DFT) automatically. I added a little extra logic to "try harder" at converging cations to hopefully fail less often if this option is specified. These changes will enable more users to call SAPT(DFT) more routinely in their workflows without having to consider acquiring GRAC shifts externally through their own logic or tabulated sources. 

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [X] User can now specify -99 for GRAC shifts (A and/or B) to automatically compute the shift required for SAPT(DFT) to make the code more accessible to users. Here is the example usage: 
```python
    psi4.set_options(
        {        
            "sapt_dft_grac_shift_a": -99,
            "sapt_dft_grac_shift_b": -99,
        }
    )
    psi4.energy("SAPT(DFT)", molecule=mol_dimer)
```

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Automatically computes SAPT(DFT) GRAC shifts for monomer A and/or B
- [x] Logic for trying extra options with level shifts to attempt to converge more cations in approximating the ionization potential

## Questions

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `767105dc4d3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.