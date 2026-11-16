# Issue

**Title:** Fix SADGuess.build_SAD binding for pybind11 3.x

## Description

## Problem

Builds against **pybind11 3.x** fail to compile `export_fock.cc`:

```
pybind11/pybind11.h:600: error: no matching conversion for functional-style cast from
  '(lambda at export_fock.cc:208)' to
  'detail::function_ref<SADGuess (shared_ptr<BasisSet>, vector<shared_ptr<BasisSet>>)>'
```

This is a **pre-existing incompatibility on master** exposed by the pybind11 3.x that CI environments have picked up (it built fine on pybind11 < 3). It is unrelated to any particular PR — it currently breaks the Azure build of every open PR.

## Root cause

`SADGuess.build_SAD` returns a `scf::SADGuess` **by value**. `SADGuess` owns a `std::unique_ptr<JK>` (deletes the copy constructor) and declares `~SADGuess()` (suppresses the move constructor), so it is neither copyable nor movable — it was only returnable by value via C++17 guaranteed copy elision.

pybind11 3.x wraps every bound callable in `detail::function_ref`, whose templated constructor is constrained on `std::is_convertible<decltype(fn(args...)), Ret>`. That trait materializes the result as an **xvalue** (`std::declval<SADGuess>()`), which requires a move/copy constructor — so `is_convertible<SADGuess, SADGuess>` is **false**, the templated constructor SFINAEs out, and only `function_ref`'s own copy/move constructors remain (which don't accept a lambda). pybind11 < 3 used a different, `is_invocable_r`-style path that accounts for prvalue elision, so it compiled.

## Fix

Return `std::make_shared<scf::SADGuess>(...)`. The class is held by `shared_ptr<SADGuess>`, so the Python-visible type is unchanged; `shared_ptr` is copyable/movable, so the `function_ref` constraint is satisfied. This is also the idiomatic factory form for a shared_ptr-held class and is backward compatible with older pybind11.

## Verification

Reproduced the exact `function_ref` constraint with a faithful mock of `SADGuess` (a `unique_ptr` member + a user-declared destructor) and confirmed, under both clang and gcc:

- by-value factory → `is_convertible<SADGuess, SADGuess>` is false → **rejected** (reproduces the CI error);
- `make_shared` factory → `is_convertible<shared_ptr<SADGuess>, shared_ptr<SADGuess>>` is true → **accepted**.

(The full build against pybind11 3.x is confirmed by this PR's own CI.)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be64f8888b12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.