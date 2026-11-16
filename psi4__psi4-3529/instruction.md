# Issue

**Title:** Replace libfilesystem with std::filesystem

## Description

`libfilesystem/path.{h,cc}` is a hand-rolled 2016 reimplementation of a subset of `std::filesystem` (`make_absolute`, `is_file`, `stem`, `extension`, `remove_file`, `resize_file`, `operator/`, `getcwd`, `create_directory`). Psi4 is C++20, so `std::filesystem` is available directly (no extra link flag on the modern-compiler baseline). This migrates the five call sites and removes the module.

**Call-site changes**
- `export_plugins.cc`, `load_plugin.cc`: `path::stem()` returns a `std::string` in the old API but a `path` in `std::filesystem`, so → `stem().string()`.
- `create_new_plugin.cc`:
  - `extension()` — **semantic note:** the old API returned the extension *without* the leading dot, `std::filesystem` returns it *with* the dot, so the `"h"`/`"cc"` comparison becomes `".h"`/`".cc"`.
  - `operator/` + `.str()` → `.string()`; `path::getcwd()` → `std::filesystem::current_path()`; `is_directory()` and `create_directory()` are now the `std::filesystem` **free functions**.
- `csg.cc`: `path(filepath_).make_absolute().is_directory()` → `std::filesystem::is_directory(std::filesystem::path(filepath_))` (`is_directory` already resolves relative paths, so `make_absolute` is redundant).
- Drop the `libfilesystem` module and its entry in `psi4/src/psi4/CMakeLists.txt`.

**Behavior note:** `std::filesystem::is_directory`/`create_directory` throw on an underlying error rather than returning `false`; in each call site the caller already errors out on a false/failed result, so behavior is equivalent (and errors are now clearer). Verified no other reference to `libfilesystem` remains. Compilation is the gate (CI); this was authored without a local build.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd6027de91f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.