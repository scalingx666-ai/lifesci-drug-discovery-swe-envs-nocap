# Issue

**Title:** Make moving making work again

## Description

#1102 

Long story short:
I accidentally used `_handle_custom_msg` method name that overwrites  https://github.com/jupyter-widgets/ipywidgets/blob/b78de43e12ff26e4aa16e6e4c6844a7c82a8ee1c/python/ipywidgets/ipywidgets/widgets/widget.py#L788

The `view. on_msg(self. _handle_custom_msg)` has never worked due to the wrong signature. This failure blocks `on_msg` function execution in https://github.com/nglviewer/nglview/blob/98d7df9c5b2c035278724eacfb8184631c17015b/nglview/contrib/movie.py#L226

The `view._handle_custom_msg`, however, is still be executed in different code branch: https://github.com/jupyter-widgets/ipywidgets/blob/b78de43e12ff26e4aa16e6e4c6844a7c82a8ee1c/python/ipywidgets/ipywidgets/widgets/widget.py#L761-L782

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98d7df9c5b2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.