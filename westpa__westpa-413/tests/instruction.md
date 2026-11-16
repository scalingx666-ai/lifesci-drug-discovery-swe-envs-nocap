# Issue

**Title:** Verify max_run_wallclock value

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->

PyYAML typically converts time specified under `max_run_wallclock` into seconds. However, there are certain formats that PyYAML does not convert, leading to errors.

PyYAML will deal with it implicitly, but if it decides to return a string, the string must be of format: `Days:Hours:Minutes:Seconds`. You can omit values (and colons) from the left, which will make those values default to 0. so 'Hours:Minutes:Seconds' work, but 'Hours:Minutes' would **not** work.

So `'00:72:00:00'`  == `'03:00:00:00'` all work. 

Test Code:
```
import westpa
rc = westpa.rc
rc.config = westpa.core.yamlcfg.YAMLConfig()
rc.config._data = {'west': {'propagation': {'max_run_wallclock': '00:72:00:00'}}} 
rc.time_config()
print(rc.config)
```

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Allow non-standard max_time_wallclock values

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/_rc.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43ed1b907ea9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.