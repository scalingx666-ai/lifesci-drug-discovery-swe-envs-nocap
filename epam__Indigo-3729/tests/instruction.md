# Issue

**Title:** Port stripSalt and checkSalt from Python to Java API

## Description

## Generic request
- [x] branch name does not contain '#'
- [x] base branch (master) is correct
- [x] code follows product standards
- [x] regression tests updated
### Optional
- [x] unit-tests written

## Summary

`stripSalt` and `checkSalt` previously existed only in the **Python** binding (`api/python/indigo/indigo/indigo_object.py`). This PR ports both to the **Java** API so the two bindings reach parity.

### Changes
- **`Salts.java`** (new) — port of Python `salts.py` `SALTS`: the SMARTS patterns that describe disconnected inorganic components. (`IONS` was not ported — it is unused dead code in the Python module.)
- **`IndigoObject.checkSalt()`** — line-for-line port of the Python method: for each component, substructure-match each salt pattern (loaded via `loadSmarts`, as in Python) and return `true` on the first match.
- **`IndigoObject.stripSalt()`** and **`stripSalt(boolean inplace)`** — port of the Python algorithm: for each component, substructure-match each salt pattern; atoms of matching components are collected and removed, either on a clone (`inplace=false`, the default) or in place (`inplace=true`).
- **`IndigoTests.java`** — cases mirroring the Python suite in `api/python/tests/test_indigo.py`:
  - `checkSalt`: monoatomic cations/anions, molecular salts, complex ions, multiple ions, and the negative cases (no ions, bonded metal/acid groups).
  - `stripSalt`: no salt, single salt, many salts, multiple organics, complex salt, only-salts, and the `inplace` option.

### Verification
- `mvn test-compile` of the `indigo` module passes.
- The Java unit tests could not be executed locally (no native C++ toolchain on the dev host to build `dist/lib`); they will run in CI against the built native library. Behavior matches the Python implementation, whose equivalent tests pass.

> Note: there is no linked issue for this parity port, so the PR title does not follow the `#1234 – issue name` pattern. Happy to attach an issue number if one should be created.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2ed51d82547`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.