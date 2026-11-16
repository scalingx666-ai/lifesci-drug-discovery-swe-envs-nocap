# Issue

**Title:** w_direct/w_kinetics outputfile inheritance + w_assign output folder creation

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->

`w_direct` is a wrapper around various older kinetics tools (e.g. `w_kinetics`), but it is not coded in a way such that the `self.output_filename` is correctly passed to those kinetic tools as `self.kinetics_filename`. This will lead to a `FileNotFoundError` when not using the default output_filename (i.e. not `direct.h5`) via variations of the following command: `w_direct [any subtool]  -o [NOT-DEFAULT-FILE-NAME].h5`. 

In other words, I'm fixing what this inline comment is pointing out:
```
# One minor issue; as this stands now, since it's inheriting from all the other classes, it needs
# a kinetics file to instantiate the other attributes.  We'll need to modify how the loading works, there.
```
https://github.com/jeremyleung521/westpa/blob/develop/src/westpa/cli/tools/w_direct.py#L501-L502

Also bundled in a fix to cases where `w_assign` will error out with `FileNotFoundError` when the `ANALYSIS` folder is made but the specific scheme folder is not.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Have `w_direct` respect user-provided output file name

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/cli/tools/w_direct.py
- [x] src/westpa/tools/kinetics_tool.py
- [x] src/westpa/cli/tools/w_assign.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

Try running:
`w_direct all -o NON-DEFAULT-FILE.h5`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3afe209fcff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.