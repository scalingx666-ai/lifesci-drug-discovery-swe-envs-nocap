# Issue

**Title:** chore: upgrade dependencies to resolve

## Description

## Runs `uv lock --upgrade` to pull in patched versions of transitive dependencies flagged by dependabot. 

No SMACT source code changes.                                          
                                                         
  Resolves alerts:                                     
  - h11 ≥ 0.16.0 (critical #73) — malformed              
  chunked-encoding bodies                                
  - pillow ≥ 12.1.1 (high #97–#99) — PSD out-of-bounds   
  write
  - pillow ≥ 11.3.0 (high #79) — BCn buffer overflow
  - urllib3 ≥ 2.6.3 (high #83, #84, #88) — decompression
  bomb / redirect bypass
  - cryptography ≥ 46.0.5 (high #94, #96) — SECT curve
  subgroup attack
  - nbconvert ≥ 7.17.0 (high #95) — uncontrolled search
  path on Windows
  - tornado ≥ 6.5 (high #75) — excessive logging DoS
  - setuptools ≥ 78.1.1 (high #74) — path traversal in
  PackageIndex
  - werkzeug ≥ 3.1.6 (medium #72, #82, #89, #100, #102) —
   Windows device name bypass
  - filelock ≥ 3.20.3 (medium #85, #90) — TOCTOU symlink
  race
  - fonttools ≥ 4.60.2 (medium #81) — arbitrary file
  write in varLib
  - urllib3 ≥ 2.5.0 (medium #77, #78) — redirect control
  issues
  - requests ≥ 2.32.4 (medium #76) — .netrc credential
  leak
  - virtualenv ≥ 20.36.1 (medium #91) — TOCTOU directory
  creation
  - PyNaCl ≥ 1.6.2 (medium #68, #87) — libsodium
  incomplete input validation
  - jupyterlab ≥ 4.4.8 (low #80) — missing noopener on
  LaTeX links
  - flask ≥ 3.1.3 (low #101, #103) — missing Vary: Cookie
   header


  ## Test plan
  - [ ] All CI tests pass with upgraded dependencies

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Chores**
  * Updated dependency version constraints in project configuration to enforce specific compatibility requirements between core packages, preventing known incompatibilities between emmet-core and other pinned dependencies whilst ensuring stable and reliable package operations.
  * Refined internal module import handling mechanisms to enhance overall package stability and resilience.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c516fb9c9d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.