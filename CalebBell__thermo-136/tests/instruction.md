# Issue

**Title:** Very minor clean-up and improvements

## Description

@CalebBell,

As I was going through the `phases` submodule, I found a couple of places where I could make some minor improvements:
* Make `T`, `P`, `zs` properties
* Remove `CEOSPhase.force_phase` attribute (I could not find anywhere where it is used; it seems like the `is_gas` and `is_liquid` is used instead)
* Specify no additional slots for CEOSPhase subclasses to avoid python from adding __dict__ when parent class slots is specified.

Please let me know if there is any issue with any of these and I can undo them. These are all very minor, but I'll slowly get into the groove into contributing to this library again. For more significant contributions, I would also consult with you beforehand to make sure the direction is OK. 

I have a couple of other places I would like to make moderate changes, but I'll post them as a separate issue in case you have any comments before I proceed with a pull request.

Thank you!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1bcc94d76707`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.