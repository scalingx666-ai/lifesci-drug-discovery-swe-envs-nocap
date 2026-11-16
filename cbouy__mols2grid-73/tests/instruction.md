# Issue

**Title:** Add support for Marimo notebooks

## Description

## Description
This PR adds support for running `mols2grid` within [marimo](https://marimo.io) notebooks.

Previously, the grid would not render correctly or support interactivity in marimo due to differences in how JavaScript, HTML, and widgets are handled compared to Jupyter. This implementation fixes the issue by:
1.  Detecting the marimo execution environment.
2.  Forcing the grid to render inside an `iframe` when in marimo. This isolates the grid's styles and scripts, ensuring it displays correctly.
3.  Returning a `marimo.vstack` containing both the `anywidget` instance and the `marimo.Html` grid. This ensures the `anywidget` backend is active, enabling bidirectional communication (e.g., for selection).
4.  Suppressing automatic widget display in `__init__`. In Marimo, we manually return the widget in `display()`, so the automatic display from `__init__` (used in Jupyter) caused double rendering and warnings.

## Changes
- **`mols2grid/utils.py`**: Added `is_running_within_marimo()` utility function.
- **`mols2grid/molgrid.py`**: 
    - Updated `MolGrid.display()` to use `marimo.Html` in an iframe and return it wrapped in `marimo.vstack` with the widget.
    - Updated `MolGrid.__init__` to skip `display(widget)` when running in marimo to prevent double rendering.
- **`tests/test_marimo_integration.py`**: Added unit tests to verify marimo detection and display logic.

## Verification
- Verified that `mols2grid.display(df)` renders the interactive grid correctly in a local marimo notebook.
- Verified that selections made in the grid are correctly reflected in `mols2grid.get_selection()`.
- Added unit tests pass with `uv run pytest`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09701af857e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.