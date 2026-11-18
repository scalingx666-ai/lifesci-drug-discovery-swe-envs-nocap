# Issue

**Title:** Readme suggestions

## Description

Hey! First of all thanks for the work on this, I'm already using and loving.

I noticed some things on the installation instructions while installing for the first time:

- `uv add xyzrender` is actually the command to [add a dependency to an uv project](https://docs.astral.sh/uv/guides/projects/#managing-dependencies)
- for the `v` integration, it's not mentioned that anywhere on `$PATH` is also used for searching the binary

So I changed the installation instruction to use [uv tool install](https://docs.astral.sh/uv/guides/tools/#installing-tools) or [uvx](https://docs.astral.sh/uv/guides/tools/#running-tools) for trying it out.
I also added the option to install from source using `uv` and mentioned the `$PATH` lookup for `v`.

Regarding the `v` binary lookup, I also noticed that while searching `~/bin` if the binary has no version attached it's not found by the `_find_viewer()` function. I have a modified version of it that fixes this and also looks common unix installation paths. If you want I can push these changes here or make a separate PR (or if you prefer to leave this aside as it seems that v integration might change (#8) feel free to tell me).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d32ca2e956a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.