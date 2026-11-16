# Issue

**Title:** User methods (for pure chemicals)

## Description

Hi Caleb,

I would like to propose a new API for setting user methods. I do realize that one is already in place (https://thermo.readthedocs.io/property_objects.html#adding-new-methods), but it's still incomplete and untested enough that I think a new implementation may work better. 

I'll first note a few minor issues with the current implementation for user or "local" methods:
* It allows users to add methods multiple times, but I don't think anyone is actually dependent on this feature because it has a bug that doesn't let it run twice. Perhaps this feature made sense when thermo would loop through methods to find one that works, but with extrapolation implemented, just one method should be enough. From my own experience with biosteam users, no user has ever tried to add multiple "methods".
* The derivative and integration functions passed by the user are not actually used (code still incomplete).
* `add_method` is not tested in CI (I checked the coverage).
* Having a tuple of all the functions would make it a bit hard to read and write (maybe an object with slots would be better?).

With this pull request, I propose a "set_user_method" method which allows for only one user method. All the derivatives and integrals are working as they should (tests have been added with full coverage and all tests passing). I made this function with biosteam users in mind, so there are a few convenience features you might take notice of.  It would be straight forward to add a similar "add_user_method_P" method for pressure-dependent methods, but this is not too important for me yet. 

This pull request draft is not urgent, so feel free come back to this later if you need to think about the implementation more.

Thanks again!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d915f5b2776`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.