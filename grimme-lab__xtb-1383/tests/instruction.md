# Issue

**Title:** Automatic setup of commit hooks to ensure signoff

## Description

This pull request introduces automated installation and enforcement of a Developer Certificate of Origin (DCO) sign-off for all commits. It adds a Python-based `commit-msg` git hook and ensures that the hook is installed automatically when configuring the project with either CMake or Meson. Uses Python to ensure cross-platform functionality, although I didn't test it for Windows.

**Git hook enforcement and installation:**

* Added a Python `commit-msg` git hook (`scripts/commit-msg`) that checks commit messages for a valid "Signed-off-by" line, enforcing DCO sign-off on all commits.
* Added a Python installation script (`scripts/install-hooks.py`) that copies the `commit-msg` hook into the repository's `.git/hooks` directory and ensures it is executable.

**Build system integration:**

* Updated `CMakeLists.txt` to automatically run the hook installation script if the project is in a git repository and Python is available, providing user feedback on success or failure.
* Updated `meson.build` to perform the same automatic hook installation using Meson's scripting facilities, again with appropriate user feedback.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39f81981f723`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.