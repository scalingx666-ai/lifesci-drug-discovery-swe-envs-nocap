# Issue

**Title:** Fix emsdk latest for minimallib

## Description

Fix the miniallib compilation error on the latest emsdk 7.0 version

#### Reference Issue

#### What does this implement/fix? Explain your changes.

- Adds a compiler option to skip zlib test compilation, which was breaking on the latest EMSDK version.

- Set EMSDK to use the latest again

- Get the npm package version from WASM. This avoids reading `CMakeLists.txt` and stays aligned with the compiled WASM module.

#### Any other comments?

I still need to test the full publish (and revert the package name), but currently I'm being blocked by github downloads returning `504 Gateway Time-out` on both inchi and font dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12b901c741f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.