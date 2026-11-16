# Issue

**Title:** Fix SOC DOS parsing for latest `pymatgen`

## Description

Since  `Spin.down` entries are no longer stored in `pymatgen` DOS objects parsed from SOC calculations (as desired). There was a patch in `sumo` to delete this entry for SOC calculations if present, to make later downstream plotting easier, but this now causes a `KeyError` when used with the latest `pymatgen` due to this entry no longer being present:
```
sumo-dosplot
Traceback (most recent call last):
  File "/home/mmm0650/miniconda3/bin/sumo-dosplot", line 8, in <module>
    sys.exit(main())
             ^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/sumo/cli/dosplot.py", line 646, in main
    dosplot(
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/sumo/cli/dosplot.py", line 207, in dosplot
    dos, pdos = load_dos(
                ^^^^^^^^^
  File "/home/mmm0650/miniconda3/lib/python3.12/site-packages/sumo/electronic_structure/dos.py", line 132, in load_dos
    del dos.densities[Spin.down]
        ~~~~~~~~~~~~~^^^^^^^^^^^
KeyError: <Spin.down: -1>
```

This small update fixes the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f314123cfb41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.