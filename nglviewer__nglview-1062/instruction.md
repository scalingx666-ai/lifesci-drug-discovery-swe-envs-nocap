# Issue

**Title:** Set `sharedPackages` to support multiple versions

## Description

Fix #1060.

Migration guide (to v7) mentions `'@jupyter-widgets/base'` should be an external dependency, but the guide only fixes nbextension.
https://ipywidgets.readthedocs.io/en/8.0.5/migration_guides.html#updating-webpack-configuration

The corresponding config key for labextension is `jupyterlab.sharedPackages`, whose value I followed 
https://jupyterlab.readthedocs.io/en/3.6.x/extension/extension_dev.html#deduplication

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f478e0f56f68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.