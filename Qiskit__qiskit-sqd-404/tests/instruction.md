# Issue

**Title:** Define the per-Python notebook environments tox.ini meant to define (backport #398)

## Description

`env_list` asks for `py310-notebook` through `py314-notebook`, but none of those environments existed.

tox expands numeric ranges in a section name before it splits the name on braces, so

```ini
[testenv:{,py-,py3-,py310-,py311-,py312-,py313-,py314-}notebook]
```

parses as `py3` plus the range `10-14`. That defines `py3notebook`, `4notebook`, `5notebook`, `6notebook` and `7notebook` — none of which anything asks for — and never defines `py310-notebook` or its siblings. Those fell through to `[testenv]`, where they picked up the `test` extras and a bare `pytest`, so

```
tox -e py312-notebook
```

installed the unit-test dependencies and ran the unit tests, reporting success without executing a single notebook cell.

Spelling the names out fixes it. CI is unaffected either way, since it runs `tox -e py,notebook` and the unfactored `notebook` env always resolved correctly — this only bit someone running a versioned environment by hand.

This also modernizes the key spellings tox 4 prefers: `minversion`, `envlist`, `basepython` and `passenv` become `min_version`, `env_list`, `base_python` and `pass_env`. `isolated_build` is dropped, having been the default since tox 4. I diffed the resolved configuration of every environment before and after: unchanged apart from `PYTHONHASHSEED`, which tox randomizes per run.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.
<hr>This is an automatic backport of pull request #398 done by [Mergify](https://mergify.com).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8af09c60a5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.