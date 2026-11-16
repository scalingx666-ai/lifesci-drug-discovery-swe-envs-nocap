# Issue

**Title:** Make sure new_we_driver() and new_data_manager() created by WESTRC inherits itself as the rc

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
This is _usually_ not a problem from the cli (since the global `westpa.rc` is the only rc), but if you want to have a non-global rc (i.e. you create `rc = WESTRC()` and not bind it to `westpa.rc`), and run `rc.get_we_driver()`, the new we_driver will create a brand new (empty) `WESTRC()` linked to `westpa.rc` , which will then fail to create a system driver because the new rc has an empty config.

Found it while trying to isolate the rc for each test.

Similar issue for the data manager and propagators as well.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x]  Correctly inherit rc when creating a new we_driver from rc.

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/_rc.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [ ] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

```
from argparse import Namespace
from westpa.core._rc import WESTRC
rc = WESTRC()
args = Namespace(rcfile='tests/refs/west_ref.cfg', verbosity=None)  # Just one of the test files
rc.process_args(args)
rc.get_we_driver()
```

Previously:
```
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
Cell In[8], line 1
----> 1 rc.get_we_driver()

File ~/git/westpa-dask/src/westpa/core/_rc.py:448, in WESTRC.get_we_driver(self)
    446 def get_we_driver(self):
    447     if self._we_driver is None:
--> 448         self._we_driver = self.new_we_driver()
    449     return self._we_driver

File ~/git/westpa-dask/src/westpa/core/_rc.py:422, in WESTRC.new_we_driver(self)
    419     else:
    420         from .we_driver import WEDriver
--> 422         we_driver = WEDriver()
    423 else:
    424     we_driver = extloader.get_object(drivername)(rc=self)

File ~/git/westpa-dask/src/westpa/core/we_driver.py:88, in WEDriver.__init__(self, rc, system)
     86 def __init__(self, rc=None, system=None):
     87     self.rc = rc or westpa.rc
---> 88     self.system = system or self.rc.get_system_driver()
     90     # Whether to adjust counts to exactly match target count
     91     self.do_adjust_counts = True

File ~/git/westpa-dask/src/westpa/core/_rc.py:654, in WESTRC.get_system_driver(self)
    652 def get_system_driver(self):
    653     if self._system is None:
--> 654         self._system = self.new_system_driver()
    655     return self._system

File ~/git/westpa-dask/src/westpa/core/_rc.py:534, in WESTRC.new_system_driver(self)
    532 log.info("No system specified! Exiting program.")
    533 # Gracefully exit
--> 534 raise ValueError("No system defined!")

ValueError: No system defined!
```


Now:
```
System is being built only off of the system driver
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `732fd1198d18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.