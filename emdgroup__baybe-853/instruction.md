# Issue

**Title:** Make `GaussianProcessSurrogate` a factory

## Description

This PR turns `GaussianProcessSurrogate` into a factory that resolves its GP components — kernel, mean, likelihood, and fit criterion — at fit time, instead of storing concrete factories as field defaults.

The reason for this is to enable settings where the choice of one component depends on the modelling context or on how another component is configured — for example mean transfer or multi-fidelity optimization, where the kernel/mean may need to be selected based on the search space or the other components. The previous design, which eagerly stored concrete default factories, could not express such dependencies cleanly.

Notes:
- The kernel/mean/likelihood/fit_criterion factory fields now accept and default to `None`, meaning "auto-select based on context at fit time".
- Component resolution is centralized in `_resolve_components`, called from `_fit`: `None` fields fall back to the corresponding BayBE defaults.
- `from_preset` is unchanged in behavior; its docstring now clarifies that a `None` argument falls back to the chosen preset's default (in contrast to the plain constructor, where `None` defers to auto-selection at fit time).
- The user-facing interface is otherwise unchanged, and existing serialized surrogates continue to deserialize correctly.
- Technically a breaking change: Accessing a factory field before fitting now returns None instead of a concrete default factory, since the defaults are only resolved at fit time, but this was discussed internally and accepted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b939e3588aad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.