# Issue

**Title:** West.cfg numpy dtype bug fix

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
 #289

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Numpy removed aliases like `np.int`, `np.float`, `np.bool` back in Numpy 1.24. This lead to a side effect where if you define 
your dataset dtype with something like `int`, initialization will fail because the data manager attempts to pull `np.int`. (See below)

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Allow users to specify dtypes that no longer have np aliases.

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/data_manager.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

`west.cfg` input
```
west:
  data:
    west_data_file: west.h5
    datasets:
      - name:        pcoord
        scaleoffset: 4
      - name:        rmsd
        scaleoffset: 4
      - name:        state_indices
        dtype:       int 
```

Error Message after running `w_init`
```
Updating system with the options from the configuration file
Traceback (most recent call last):
  File "/Users/User/miniconda3/envs/westpa-workshop2024/bin/w_init", line 8, in <module>
    sys.exit(entry_point())
             ^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/cli/core/w_init.py", line 111, in entry_point
    initialize(
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/cli/core/w_init.py", line 147, in initialize
    sim_manager = westpa.rc.get_sim_manager()
                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/_rc.py", line 370, in get_sim_manager
    self._sim_manager = self.new_sim_manager()
                        ^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/_rc.py", line 361, in new_sim_manager
    sim_manager = WESimManager(rc=self)
                  ^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/sim_manager.py", line 52, in __init__
    self.data_manager = self.rc.get_data_manager()
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/_rc.py", line 386, in get_data_manager
    self._data_manager = self.new_data_manager()
                         ^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/_rc.py", line 378, in new_data_manager
    data_manager = westpa.core.data_manager.WESTDataManager()
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/data_manager.py", line 286, in __init__
    self.process_config()
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/data_manager.py", line 255, in process_config
    dsopts = normalize_dataset_options(dsopts, path_prefix='auxdata' if dsopts['name'] != 'pcoord' else '')
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/User/Documents/Important/Pitt/git/westpa-project/src/westpa/core/data_manager.py", line 1526, in normalize_dataset_options
    dsopts['dtype'] = np.dtype(getattr(np, dtype))
                               ^^^^^^^^^^^^^^^^^^
  File "/Users/User/miniconda3/envs/westpa-workshop2024/lib/python3.11/site-packages/numpy/__init__.py", line 324, in __getattr__
    raise AttributeError(__former_attrs__[attr])
AttributeError: module 'numpy' has no attribute 'int'.
`np.int` was a deprecated alias for the builtin `int`. To avoid this error in existing code, use `int` by itself. Doing this will not modify any behavior and is safe. When replacing `np.int`, you may wish to use e.g. `np.int64` or `np.int32` to specify the precision. If you wish to review your current use, check the release note link for additional information.
The aliases was originally deprecated in NumPy 1.20; for more details and guidance see the original release note at:
    https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations. Did you mean: 'inf'?
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `587296bd4283`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.