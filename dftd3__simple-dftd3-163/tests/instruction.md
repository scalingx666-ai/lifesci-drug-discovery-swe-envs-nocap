# Issue

**Title:** Support Skala-1.0 functional

## Description

Adds DFT-D3(BJ) dispersion correction support for the Skala-1.0 functional (same parameters as B3LYP) and fixes a Python build failure caused by a stale setuptools version constraint.

### Skala-1.0 functional support

- Add `p_skala_df` method ID with `case("skala1.0")` mapping (hyphens stripped by `get_method_id`)
- D3(BJ) rational damping only — Skala does not support other D3 variants
- Dedicated DOI (`10.48550/arXiv.2506.14665`) with full 25-author citation in both `citation.f90` and `parameters.toml`
- TOML key quoted as `[parameter."skala-1.0"]` to avoid subtable interpretation

### Bug fix: `get_method_id` uninitialized variable

Initialize `lc_method` to blanks before the hyphen-stripping loop. Without this, method names containing hyphens (like `skala-1.0`) leave uninitialized trailing characters that break `trim()` and string comparison.

### Python: replace deprecated `pkg_resources` import

`test_library.py` used `pkg_resources.parse_version` which was removed in setuptools 78+. Replaced with `packaging.version.Version`:

```python
# Before
from pkg_resources import parse_version
assert parse_version(get_api_version()) == parse_version(__version__)

# After
from packaging.version import Version
assert Version(get_api_version()) == Version(__version__)
```

### Python: remove setuptools version constraint

The `setuptools<78` build-system constraint was added for the now-removed `pkg_resources` usage and was failing CI. Removed the cap — setuptools is still required (cffi's `distutils_extension()` returns a `setuptools.Extension`) but no longer needs a version ceiling.

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Support Skala functional</issue_title>
> <issue_description>* https://aka.ms/SkalaDFT
> * https://aka.ms/SkalaDFT/blog
> * https://aka.ms/SkalaDFT/preprint</issue_description>
>
> <agent_instructions>Implement Skala-1.0 with the same parameters as B3LYP</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes dftd3/simple-dftd3#147

<!-- START COPILOT CODING AGENT TIPS -->
---

✨ Let Copilot coding agent  — coding agent works faster and does higher quality work when set up for your repo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ec0e33714c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.