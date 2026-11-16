# Issue

**Title:** Fix 'performance-avoid-endl' in core, calc, command and qtplugins

## Description

Part of #3101.

Replaces `std::endl` with `'\n'` where clang-tidy reports `performance-avoid-endl`: 45 fixes in 7 files. The diff is clang-tidy's own fixes, formatted with `git clang-format`, with no hand edits.

Commands (clang-tidy 19.1.7):

```
run-clang-tidy -p ../build \
  -checks='-*,performance-avoid-endl' \
  -header-filter='avogadro/(core|calc|command)/' \
  -fix 'avogadro/(core|calc|command)/.*\.cpp$'

run-clang-tidy -p ../build-qt \
  -checks='-*,performance-avoid-endl' \
  -header-filter='avogadro/qtplugins/' \
  -fix 'avogadro/qtplugins/apbs/apbsdialog\.cpp$'

git clang-format
```

The qtplugins part only touches `apbs/apbsdialog.cpp`; it was the only qtplugins file with this warning. Re-running the commands without `-fix` reports nothing. `ctest` passes (77/77) with avogadrodata cloned next to avogadrolibs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `971bc1d67246`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.