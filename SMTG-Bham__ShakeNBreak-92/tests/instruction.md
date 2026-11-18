# Issue

**Title:** Updated oxidation state guessing

## Description

As discussed with @kavanase via email, this PR replaces the old Pymatgen `oxi_state_guesses` with `guess_and_set_oxi_states_with_timeout` from doped. The Pymatgen function gets stuck for large bulk structures with irreducible chemical formulas, e.g. X96Y97 which can occur if trying to ShakeNBreak defect complexes. 

There are some slight differences in output between the two functions, so the checks in some tests have been changed slightly. For some reason, it also causes a variable in `distortions.py` to become a NumPy float instead of a regular float, causing test failures in `test_distortion.py` (which are fixed by converting them to floats):
`Original Neighbour Distances: [(np.float64(2.83), 32, 'Te'), (np.float64(2.83), 41, 'Te')]\n`

On another note, I think both functions might break for systems with multiple oxidation states per element like Fe3O4. The Pymatgen function returns an averaged fractional oxidation state (Fe2.66+). Doped returns a mixture of oxidation states (Fe2+,Fe3+), but this is lost in `guessed_oxidation_states` as it is a `dict` with element symbols (Fe) as keys.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96b4df786e31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.