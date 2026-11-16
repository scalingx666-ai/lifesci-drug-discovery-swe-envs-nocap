# Issue

**Title:** Debug Mode Fix for w_ipa

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
https://groups.google.com/g/westpa-users/c/y9mzfeh935E

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
`w_ipa`'s debug mode doesn't work. This fixes it. Probably due to how Python3 defaults to byte strings. I've rolled back to westpa 2022.03 and the bug still existed.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Allow w_ipa debug mode to run properly 
- [x] reorganize relevant lines to be clearer

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/cli/tools/w_ipa.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

```
(westpa2) User:test-hdf5-amber2 User$ w_ipa -ao -d

Welcome to w_ipa (WESTPA Interactive Python Analysis) v. 1.0B!
Run w.introduction for a more thorough introduction, or w.help to see a list of options.
Running analysis & loading files.
arg 00 -- --output            
arg 01 -- assign.h5           
arg 02 -- --config-from-file  
arg 03 -- --scheme-name       
arg 04 -- TEST                
arg 05 -- 1                   
Traceback (most recent call last):
  File "/Users/User/anaconda3/envs/westpa2/bin/w_ipa", line 8, in <module>
    sys.exit(entry_point())
  File "/Users/User/Documents/Important/Pitt/git/westpa/src/westpa/cli/tools/w_ipa.py", line 814, in entry_point
    w.main()
  File "/Users/User/Documents/Important/Pitt/git/westpa/src/westpa/tools/core.py", line 171, in main
    self.go()
  File "/Users/User/Documents/Important/Pitt/git/westpa/src/westpa/cli/tools/w_ipa.py", line 732, in go
    self.analysis_structure()
  File "/Users/User/Documents/Important/Pitt/git/westpa/src/westpa/cli/tools/w_ipa.py", line 301, in analysis_structure
    new_hash = self.hash_args(
  File "/Users/User/Documents/Important/Pitt/git/westpa/src/westpa/cli/tools/w_ipa.py", line 164, in hash_args
    print('arg {num:02d} -- {arg:<20}'.format(num=il + iarg, arg=l))
TypeError: unsupported format string passed to bytes.__format__
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21d00b338132`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.