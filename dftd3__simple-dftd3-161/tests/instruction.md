# Issue

**Title:** Fix CI: update Meson, macOS runner, and migrate to meson-python

## Description

CI fails with `RuntimeError: There is no current event loop in thread 'MainThread'` because Meson 0.58.0 uses deprecated `asyncio.get_event_loop()` which throws in Python 3.14.

### Changes
- Update `assets/ci/build-env.yaml` to require `meson >=1.2.3,!=1.8.0`
  - 1.2.3+ contains the asyncio compatibility fix
  - Excludes 1.8.0 consistent with `python-env.yaml`
- Update macOS workflow since `macos-13` runner is retired:
  - Change runner from `macos-13` to `macos-14`
  - Update GCC version from 10 to 12 (gcc@10 unavailable as bottle on macOS 14)
  - Update Homebrew paths from `/usr/local/bin` to `/opt/homebrew/bin` (Apple Silicon)
- Replace deprecated setuptools-based build with meson-python for Python build:
  - Rename `python/mesonpep517.toml` to `python/pyproject.toml`
  - Remove `python/setup.py` and `python/setup.cfg`
  - Keep setuptools as a required dependency in `dftd3/meson.build` and `pyproject.toml`
  - Update `wheel.yml` to remove obsolete mesonpep517 rename step
  - Add meson-python and ninja to `python-env.yaml`
  - Update `build.yml` to use meson-python with `--no-build-isolation`
- Update `wheel.yml` to use `macos-14` instead of retired `macos-13` for ARM64 wheel builds

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>GitHub actions for testing build is broken</issue_title>
> <issue_description>Currently the build via the CI workflow is broken (https://github.com/dftd3/simple-dftd3/actions/runs/20005011041)</issue_description>
>
> <agent_instructions>Update the CI workflow to fix any issues from missing dependencies or incomplete compiler setup</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes dftd3/simple-dftd3#160

<!-- START COPILOT CODING AGENT TIPS -->
---

💬 We'd love your input! Share your thoughts on Copilot coding agent in our [2 minute survey](https://gh.io/copilot-coding-agent-survey).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86dcf336a14a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.