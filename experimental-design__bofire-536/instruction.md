# Issue

**Title:** Bump Entmoot and LightGBM

## Description

Bumps the version of Entmoot (which provided bug fixes), and LightGBM (which fixed a vulnerability). Also provides a slight shift in the strategy so that `test_strategy_can_be_loaded_from_data_model` works even without Entmoot installed, which avoids an ugly `pytest.importorskip("entmoot")`.

.
Passes all Enting tests with a Gurobi license and `--runslow` on my machine - I don't remember if all of these run on the CI pipeline on GitHub.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4644d48c7160`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.