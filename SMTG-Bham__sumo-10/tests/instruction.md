# Issue

**Title:** Cache DOS colours and re-use them

## Description

This addresses #8 by ensuring that orbital colours will be consistent across multiplots and between re-plot calls from an interactive notebook.

A dict  `sumo.plotting.colour_cache` is held at the plotting level (as other plots may wish to share this information) and initialised as `{}`; when the dos_plotter does not find an orbital colour specified in the ``colours`` argument it will take the next item from a cycle and update the cache with `{element: {orbital: colour}}`. To clear the cache and start the colour cycle from the beginning, this module-level variable can be manually reset to `{}`. This would rarely be necessary: I still recommend that any real colour tweaking should be done by passing a dict or config directly.

Tests are included and currently pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cca0a647a0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.