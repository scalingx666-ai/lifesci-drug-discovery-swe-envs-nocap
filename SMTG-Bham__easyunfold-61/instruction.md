# Issue

**Title:** Fix kpoints issues

## Description

@zhubonan when I was running `easyunfold generate` with a `Fm-3m` primitive with a `P2_1/m` supercell I was getting the following error:

(The guessed transformation matrix is correct)
```
32_atom_SQS_HSE06_SOC_easyunfold > easyunfold generate Fake_prim_POSCAR  32_atom_SQS_POSCAR  KPOINTS_band --scf-kpoints IBZKPT
(Guessed) Transform matrix:
[[-2.0, 1.0, 1.0], [0.0, -2.0, 2.0], [2.0, 1.0, 1.0]]
210 kpoints specified along the path
Traceback (most recent call last):
  File "/home/mmm0650/miniconda3/bin/easyunfold", line 8, in <module>
    sys.exit(easyunfold())
             ^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/click/core.py", line 1161, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/click/core.py", line 1082, in main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/click/core.py", line 1697, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/click/core.py", line 1443, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/click/core.py", line 788, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/easyunfold/cli.py", line 146, in generate
    unfoldset = UnfoldKSet.from_atoms(transform_matrix,
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/easyunfold/unfold.py", line 235, in from_atoms
    return cls(
           ^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/easyunfold/unfold.py", line 184, in __init__
    self.expand_pc_kpoints()
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/easyunfold/unfold.py", line 262, in expand_pc_kpoints
    kset, weights = expand_K_by_symmetry(kpt, self.pc_opts, self.sc_opts, time_reversal=self.time_reversal)
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/easyunfold/unfold.py", line 120, in expand_K_by_symmetry
    assert out_points[0] is kpt_orig
AssertionError
```
Files attached for reference. 

Digging in, I found that this was caused by the fact that with `expand_K_by_symmetry`; an input `kpt` of [0.5,0.5,0.5] gave these values:
https://github.com/SMTG-Bham/easyunfold/blob/aaf1a1580e7bc7330b9f11c5ac8e9b27fcc37369/easyunfold/unfold.py#L83-L94
```
kpt_orig: [0.5 0.5 0.5]
pc_distinct [array([0.5, 0.5, 0.5]), array([-0.5,  0.5,  0.5]), array([0.0, -0.5,  0.0]), array([0.0, 0.0, -0.5]), array([0.5, 0.0, 0.0]), array([-0.5,  0.5, -0.5]), array([0.5,  0.5, -0.5])]
```

Then for the weight determination loop:
https://github.com/SMTG-Bham/easyunfold/blob/aaf1a1580e7bc7330b9f11c5ac8e9b27fcc37369/easyunfold/unfold.py#L95-L110
`-0.5,  0.5, -0.5` ends up getting matched to `0.5, 0.5, 0.5` and others, giving it a weight of 4 and setting the 'weight' of `0.5, 0.5, 0.5` (i.e. `kpt_orig`) to `0` here, which causes it to be dropped from the `out_points` list and thus fail the assertion check above. However, `-0.5,  0.5, -0.5` and `0.5, 0.5, 0.5` should be considered the same k-point right?

Updating to use `wrap_kpoints` to ensure `+/-0.5, +/-0.5, +/-0.5` are all matched together as in this PR, then gives:
```
kpt_orig [-0.5 -0.5 -0.5]
pc_distinct [array([-0.5, -0.5, -0.5]), array([ 0. , -0.5,  0. ]), array([ 0. ,  0. , -0.5]), array([-0.5,  0. ,  0. ])]
```
and thus a weight of 1 for `-0.5, -0.5, -0.5` as expected -- right? (And passes the assertion test)
Just checking with you that this is correct in your understanding too?

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Bug Fixes**
	- Improved consistency of k-point wrapping within the first Brillouin zone when expanding by symmetry.
	- Enhanced reliability of k-point comparisons during symmetry operations.
	- Adjusted k-point wrapping range to ensure values fall within (-0.5, 0.5].

- **Refactor**
	- Internal properties related to reduced k-points were removed for streamlined initialization.
	- Corrected file path handling for saving k-point files in separate folders.

- **Tests**
	- Updated expected k-point counts and effective mass values in CLI tests.
	- Refined expected number of expanded k-points in unfolding tests.
	- Added comments to assist with updating reference k-point files.

- **Chores**
	- Cleaned up `.gitignore` files by removing duplicate and redundant entries.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaf1a1580e7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.