# Issue

**Title:** Fix summary tables in westpa.analysis

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Due to our pretty messy history, it's difficult to trace back why we changed this, but whatever.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] make westpa.analysis summary tables work

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/analysis/core.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

```
import westpa.analysis as wa
run = wa.run('west.h5')
run.iteration(1).basis_state_summaries
```

```
# Before
                                                label  probability                                             auxref
0   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
1   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
2   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
3   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
4   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
5   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
6   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
7   <pandas.core.strings.accessor.StringMethods ob...     0.045455  <pandas.core.strings.accessor.StringMethods ob...
```



```
# After
   label  probability auxref
0   3129     0.045455   3129
1   3130     0.045455   3130
2   3131     0.045455   3131
3   3132     0.045455   3132
4   3133     0.045455   3133
5   3134     0.045455   3134
6   3135     0.045455   3135
7   3136     0.045455   3136
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3b3b4207e0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.