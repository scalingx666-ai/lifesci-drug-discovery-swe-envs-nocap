# Issue

**Title:** Fix raising warnings and pytest depreciation

## Description

This pull-requests fixes:
- that pytest removed the option to capture warnings via None, this gives an error when using Python 3.11, see  and the our pull-request that failed recently #228.  This is heavily used in `test_periodic`, 
- Further `Nose` is used in periodic and is removed by me due to reasons specified by [pytest](https://docs.pytest.org/en/stable/deprecations.html#support-for-tests-written-for-nose).
- Handles all warnings given in all of the tests. This handles issue #208. 
    - For the UserWarnings, I used `pytest.warn(match=)` to make sure the warnings were raised. 
    - In cases, where the warnings were coming from other modules I ignored them use the decorator `@pytest.mark.filterwarnings("ignore:api v1")` to ignore it on the specific test or if I couldn't find out which test were raising a warning I used `pytestmark = pytest.mark.filterwarnings("ignore:...")` to ignore the entire module. This are all specified in the [pytest docs](https://docs.pytest.org/en/7.1.x/how-to/capture-warnings.html).
    - Ignore division by zero and nan in our ode or Poisson solver.
- Added vectorization of interpolation derivatives in cubic with a simple fix. This removes the cubic grid warning.
- Fixed the overflow in spherical harmonics by moving the square-root and adding numpy longdouble precision (just in case) and added a test for orthonormality in high dimensions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56d9a19eb215`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.