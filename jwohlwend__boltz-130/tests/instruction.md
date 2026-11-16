# Issue

**Title:** Debug run fixes

## Description

Resolves a few minor issues for the structure and confidence module debug training runs. 

For the structure module training,
1. `run_confidence_sequentially` is not provided in the `validation_args` of the config. Just added the default `False` value in the config.

For the confidence module training,
1. Replaced the model class with `boltz.model.model.Boltz1` instead of `boltz.model.models.boltz.BoltzPreview`
2. `run_confidence_sequentially` set as False in the validation args similar to the structure config changes.
3. The following arguments are invalid, therefore removed them, `run_trunk_and_structure` in `model` args, `use_gaussian` in `confidence_model_args` and `relative_confidence` in `confidence_args`. The last two were also present in the structure config, therefore removed them for correctness. 
4.  `["rel_plddt_loss", "rel_pde_loss", "rel_pae_loss"]` are not logged/present in the loss breakdown of `confidence_loss_dict`. Removed them. 

Post these changes, the debug runs seem to run correctly. Let me know if something needs to be changed here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a64ed647774e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.