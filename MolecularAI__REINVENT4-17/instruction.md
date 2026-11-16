# Issue

**Title:** feature: Implement REINFORCE loss and add corresponding learning strategies for DAP, MAULI, MASCOF

## Description

In the current implementation the learning strategies do not really implement REINFORCE as described in the paper. Especially, the MAULI and MASCOF strategies seem to have a bug. 

This PR adds new learning strategies `dap_reinforce`, `mauli_reinforce` and `mascof_reinforce` that are supposedly correct. The rectified strategies are validated in a simple experiment, i.e. optimizing QED from the pretrained reinvent priors. Config files for running this experiment with the different learning strategies can be found in a separate branch in the downstream repo: 

- [staged_learning_dap.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_dap.toml)
- [staged_learning_dap_reinforce.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_dap_reinforce.toml)
- [staged_learning_mauli.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_mauli.toml)
- [staged_learning_mauli_reinforce.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_mauli_reinforce.toml)
- [staged_learning_mascof.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_mascof.toml)
- [staged_learning_mascof_reinforce.toml](https://github.com/tobiasploetz/REINVENT4/blob/fix/reinforce-loss-experiments/configs/toml/staged_learning_mascof_reinforce.toml)

The optimization trajectory of an exemplary run is shown below, demonstrating that the new strategies for MAULI and MASCOF considerably improve their current counterparts, bringing them on par with DAP:

<img width="1069" alt="image" src="https://github.com/MolecularAI/REINVENT4/assets/44431468/b6363a9b-26fd-4a9b-97f7-ec6c91f4db86">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c281cc391fa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.