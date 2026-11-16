# Issue

**Title:** Allow custom binning through haMSM restarting plugin

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  
https://groups.google.com/g/westpa-users/c/zlNzsigUttw

**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
`msm_we` already allows us to build a haMSM with a rectilinear binning scheme that's different from the bins used during simulation. This is especially useful when the simulations are done with MAB. However, this is option is not accessible using the hamsm restarting plugin. This change allows us to specify a Rectilinear Binning using the same syntax as how we specify binning in regular WE.

```
we:
  plugins:
    - plugin: westpa.westext.hamsm_restarting.restart_driver.RestartDriver
      user_bin_mapper:
        type: RectilinearBinMapper
        # The edges of the bins
        boundaries:
          - ['-inf', 1., 1.1,  1.2, 1.3, 1.4, 1.5,1.6, 1.7, 1.8, 1.9,
             2.0, 2.1, 2.2, 2.3, 2.4, 2.5, 2.6, 2.7, 2.8, 2.9, 
             3.0, 3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 3.7, 3.8, 3.9,
             4.0, 4.1, 4.2, 4.3, 4.4, 4.5, 
             4.6, 4.8, 5.0, 5.2, 5.4, 5.6, 5.8, 6.0, 6.2, 6.4,
             6.6, 7.2, 7.8, 8.4, 9.0, 9.6, 12.5, 'inf']
```

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] allow use of custom binning in haMSM restarting plugin

**Major files changed.**  
- [x] src/westpa/westext/hamsm_restarting/restart_driver.py

**Status.**
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43ed1b907ea9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.