# Issue

**Title:** Pybind options

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR moves optking's type and value validation for options from Psi4 to pydantic.

Allowed options are detected at compile time. Removes need to sync options. (REVERTED)

Some tests needed to be updated after changes to the IRC code. 

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] This PR accompanies the 0.4 optking release which includes additional linear coordinate handling and IRC fixes. 
- [x] Alphabetical keywords list has now moved into optking docs page.
- [x] irc_forward and irc_backward were not being written since 1.7. `irc_traj.<pid>.xyz` file will now be written for irc jobs and `opt_traj.<pid>.xyz` file can also be requested for non irc jobs.
- [x] Setting a coordinate constraint to a whitespace containing string (i.e. `set frozen_bend (" ")`) no long works. Please use `set frozen_bend ""` to erase a previously set value.
- [x] Adds 'opt' to allowed cli test groups 

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] An embedded python interpreter is used to check optking's pydantic model for fields and the types 
of those fields to be added to the options object. (REVERTED)
- [x] Some Psi4 specific options are left as module options.
- [x]  Had to replace sphinx substitutions for optking with explicit links.
- [x] A sign error was hiding the fact that the current forward / backward direction doesn't always match old optking.
- [x] Addition of linear coordinates during IRC affects termination for HCN. Test updated.
- [x] Optking is pydantic v1 and v2 ready. optking.op is assigned to v1/optparams or v2/optparams as appropriate given detected pydantic version so updating Psi4's environment shouldn't break anything on optking's end. (Still true but since read_options no longer references optparams, less relevant to Psi devs)
- [x] Removes `python setup.py` from optking/Cmakelists.txt. Prepares for removal of `setup.py`. I'm delaying optkings move to pyproject.toml until after this PR so there'll be a deprecation notice for the time being.

## Checklist
- [x] Tests added for any new features (All relevant optking options explicitly tested in `test_optking.py`)
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d50ba83c44e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.