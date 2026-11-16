# Issue

**Title:** Support ipywidgets v8

## Description

Fix #1032.

Displaying a controller below the main 3D viewer looks like an exact use case `_ipython_display_`, while `ipywidgets` has replaced `_ipython_display_` with `_repr_mimebundle_`.

[`IPython.core.formatters.IPythonDisplayFormatter`](https://github.com/ipython/ipython/blob/ae0dfcd9d4fb221f0278f07b022f9837b0e51e67/IPython/core/formatters.py#L883-L921) says
> IPython 6.1 introduces `_repr_mimebundle_` for displaying custom mime-types,
> so `_ipython_display_` should only be used for objects that require unusual
> display patterns, such as multiple display calls.

NGLWidget inside another widget still works, while `ipywidgets>=8` seems to assume `_repr_mimebundle_`. It cannot show GUI of NGLWidget if it's inside another widget regardless of the change or the version of ipywidgets.

Another idea to fix the issue is to use `ipywidgets.VBox([viewer, gui])`. It might be more correct fix but
- it would remove the ability to change width of the main viewer; and
- the distinction of the viewer and the box complicates the code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be22c2623117`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.