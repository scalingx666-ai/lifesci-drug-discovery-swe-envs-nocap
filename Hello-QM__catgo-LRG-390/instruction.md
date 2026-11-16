# Issue

**Title:** fix(hpc): bundle asyncssh crypto deps (pynacl/bcrypt) + custodian — v1.3.1

## Description

Corrected replacement for the retracted v1.3.0.

**Bug:** packaged builds (desktop + VS Code sidecar) could not connect to HPC — SSH hung at "connecting…". The PyInstaller bundle was missing `pynacl` + `bcrypt` (asyncssh's crypto backends for Ed25519 / Curve25519 / encrypted OpenSSH keys); undeclared deps → not installed in CI, not collected by the spec. asyncssh itself was always bundled. Expanse uses publickey + TOTP, so publickey auth failed before the OTP stage (no kbdint logs → hang).

**Fix:**
- declare `bcrypt`, `pynacl` (requirements.txt + pyproject.toml)
- `catgo_server.spec`: collect asyncssh submodules + pin bcrypt/nacl; also collect **custodian** (VASP job error-correction, lazily imported → was missing → packaged workflows crashed)
- bump 1.3.0 → 1.3.1 (all version files) + CHANGELOG

**Verified:** dev backend (deps present) connects to Expanse with TOTP; rebuilt sidecar bundles asyncssh+bcrypt+nacl+custodian (PYZ TOC).

After merge: tag `v1.3.1` to fan out the release.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bef952a3e42b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.