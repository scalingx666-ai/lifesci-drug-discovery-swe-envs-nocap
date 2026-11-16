# Issue

**Title:** Reset component caches when forces get a new positions tensor

## Description

.

`requires_positions_grad` now keeps a weak reference to the positions tensor that the last graph was built for. When `forces` (or
another method behind that decorator) gets a different tensor, it first clears the classical, interaction and integral caches. These are
the caches `Calculator.reset()` clears, apart from the result cache, which is already keyed on the tensor id. Calls with the same tensor
keep using the caches, so repeated derivatives of one graph are not slowed down.

**Test:** `test/test_calculator/test_cache/test_positions_graph.py` covers forces after `energy`, and `forces` twice with a new tensor,
for GFN1 with the PyTorch driver and, when libcint is available, for GFN1 and GFN2 with libcint. All 6 cases fail on `main` (2070660) and
pass on this branch.

**Other tests run locally** (Python 3.11, torch 2.14.1 CPU, the tad versions `main` pins, tad-libcint 0.3.0):
- `test/test_calculator`: 60 passed
- `test/test_singlepoint/test_grad_gfn1.py`: 42 passed
- `test/test_singlepoint/test_grad_gfn2.py`: 18 passed
- `test/test_singlepoint/test_hess.py`: 3 passed
- `test/test_properties/test_hessian.py`: 7 passed
- `test/test_properties/test_vibration.py`: 3 passed
- `test/test_properties/test_dipole_deriv.py`: 8 passed

The rest of the suite was not run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `207066072fd8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.