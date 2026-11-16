# Issue

**Title:** Pass --v-kl, --eps and --alpha to the default loss function

## Description

## Bug report

 (also the same mechanism as #1233, closed in January as "if this comes up again ... re-open").

This contribution was developed through OMEGA, the research system I designed and direct. AI agents performed the implementation, test development and execution within that system; Claude Code was used for this contribution. I have not personally reproduced the results.

`--v-kl/--evidential-regularization`, `--eps` and `--alpha` only reached the loss function when `--loss-function` was also given. Without it, `build_model` passed `criterion=None` and the predictor built its default loss with class defaults. The flags were dropped silently: the log and the saved model both show the default values.

Affected task types (each tested here): `regression-evidential` (`--v-kl`, `--eps`), `regression-quantile` (`--alpha`, which sets the target interval), and `classification-dirichlet` (`--v-kl`). The same pattern was also in `build_MAB_model`.

This PR adds `build_criterion()` in `chemprop/cli/train.py`, used by both `build_model` and `build_MAB_model`:

- `--loss-function` given: build that loss, as before.
- No `--loss-function`, but a loss hyperparameter given: build the task type's default loss (`predictor_cls._T_default_criterion`) with it.
- Neither given: return `None`, so the predictor builds its default loss exactly as before.

To tell "given" from "not given", `--v-kl`, `--eps` and `--alpha` now default to `None`. For an explicit `--loss-function`, the previous CLI defaults (`v_kl=0.0`, `eps=1e-8`, `alpha=0.1`) are still filled in. So runs that pass none of these flags behave exactly as they did.

## Example

```
chemprop train -i tests/data/regression/mol/mol.csv --epochs 3 -t regression-quantile --alpha 0.05
```

Criterion restored from the saved checkpoint (`model.predictor.criterion`), 3-epoch run per case:

| command | main (db0bb86) | this PR |
|---|---|---|
| `-t regression-evidential --v-kl 0.5 --eps 1e-4` | `EvidentialLoss(v_kl=0.2, eps=1e-08)` | `EvidentialLoss(v_kl=0.5, eps=0.0001)` |
| `-t regression-quantile --alpha 0.05` | `QuantileLoss(alpha=0.1)` | `QuantileLoss(alpha=0.05)` |
| `-t classification-dirichlet --v-kl 0.5` | `DirichletLoss(v_kl=0.2)` | `DirichletLoss(v_kl=0.5)` |
| `-t regression-evidential --v-kl 0.5 --eps 1e-4 -l evidential` | `v_kl=0.5, eps=0.0001` | unchanged |
| `-t regression-evidential` | `v_kl=0.2, eps=1e-08` | unchanged |
| `-t regression-quantile` | `alpha=0.1` | unchanged |
| `-t regression-evidential -l evidential` | `v_kl=0.0, eps=1e-08` | unchanged |

Tests added:

- `tests/cli/test_cli_regression_mol.py::test_train_loss_hyperparameters`: 6 cases, including the 4 unchanged ones from the table as controls.
- `tests/cli/test_cli_classification_mol.py::test_train_dirichlet_v_kl`: 2 cases.
- `tests/cli/test_cli_MAB.py::test_train_evidential_v_kl`: checks the mol, atom and bond predictors.

- `tests/cli/test_cli_regression_mol.py::test_train_config_replays_loss_hyperparameters`: 3 cases. Trains, re-trains from the saved `config.toml`, and checks both runs' loss.
- `tests/cli/test_cli_regression_mol.py::test_train_legacy_config_warns`: a config in the 2.3.1 format warns; one without the three values does not.

On main, 4 of the first 9 fail (the bug cases); with this PR, 9 pass. Of the 5 config tests, 2 fail on main (`--v-kl 0.5` is ignored in the original run; no warning) and 5 pass with this PR.

`chemprop hpopt` builds its models through the same `build_model`, so it had the same bug and gets the same fix. One-trial Ray Tune run (random search, `-t regression-evidential --v-kl 0.5`, 3 epochs), loss read from `best_checkpoint.ckpt` and from a `train` re-run of `best_config.toml`:

| | main (db0bb86) | this PR |
|---|---|---|
| trial loss | `EvidentialLoss(v_kl=0.2)` | `EvidentialLoss(v_kl=0.5)` |
| `best_config.toml` | `v-kl = 0.5`, `eps = 1e-08`, `alpha = 0.1` | `v-kl = 0.5` |
| `train --config-path best_config.toml` | `v_kl=0.2` | `v_kl=0.5` |

The agent also checked that the tests are not vacuous: reverting the new branch, dropping the explicit-loss defaults, or applying the old CLI defaults to the task default each makes at least one test fail.

Existing modules run before and after this change, on CPU: `test_cli_regression_mol`, `test_cli_classification_mol`, `test_cli_classification_mol_multiclass`, `test_cli_regression_rxn+mol`, `test_cli_MAB`, `test_parsing`, `tests/unit/cli`, `tests/unit/nn/test_loss_functions`. Result with this PR, after installing the `hpopt` extras (ray 2.59.0, optuna 5.0.0, hyperopt): 183 passed and 3 skipped. The 3 skips are the hpopt tests' own platform skips for macOS with Python 3.12; `test_optuna_quick` ran and passed. Before the hpopt extras were installed: 177 passed and 4 skipped, on main and with the first commit alike. On Apple Silicon with MPS auto-selected, `test_train_config` and `test_freeze_model` fail identically on main and on this branch (MPS determinism/device errors, cf. #1351). They pass when MPS is hidden.

## Questions

1. **CLI default vs class default for `--v-kl`.** The CLI default has been `0.0`, while `EvidentialLoss`/`DirichletLoss` default to `0.2` (the value Soleimany et al. 2021 recommend, per the help text). So `-t regression-evidential` and `-t regression-evidential -l evidential` train different objectives. This PR keeps both behaviours unchanged so no existing run changes. If you would rather unify on 0.2, it is a one-line change in `build_criterion`.
2. **Re-running an old `config.toml`.** With this PR, `config.toml` only contains the loss hyperparameters that were actually given (a `None` value is not written), so a saved config replays to the same loss function as the original run (`test_train_config_replays_loss_hyperparameters`). Configs saved by 2.3.1 and earlier always contain `v-kl = 0.0`, `eps = 1e-08` and `alpha = 0.1`, which those versions ignored unless `loss-function` was set. Re-running such a config for `regression-evidential`/`classification-dirichlet` now uses `v_kl=0.0`, where the original run used 0.2. Values set explicitly in a config can't be told apart from these written defaults, so the PR keeps honouring them. When a config file sets exactly these three values and no `loss-function`, `validate_train_args` logs a warning that names the change and how to reproduce the original run (`test_train_legacy_config_warns`). The alternative is to treat that exact triple as "not given", which reproduces old runs but silently ignores anyone who sets all three on purpose. I can switch to that if you prefer.
3. KnathanM's suggestion in #1233 was to set `args.loss_function` from the task type in `process_train_args`. This PR builds the default loss in `build_model` instead. That keeps `args.loss_function`, the saved config and the "No loss function was specified!" log line as they are, and avoids changing `v_kl` from 0.2 to 0.0 for default runs (because of question 1). I'm happy to switch if you prefer that approach.

## Checklist
- [x] linted with flake8? (also `black --check` 23.12.1 and `isort --check` on the touched files)
- [x] (if necessary) appropriate unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b90e3e21461`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.