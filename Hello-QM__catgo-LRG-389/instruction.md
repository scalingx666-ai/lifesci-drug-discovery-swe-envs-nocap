# Issue

**Title:** release: v1.3.0 — multi-pane workspace + full format/hotkey/edition docs

## Description

Cut **v1.3.0**. Version bumped across package.json, tauri.conf.json, Cargo.toml/lock, extensions/vscode/package.json, citation.cff.

### Docs / descriptions (verified against code, not guessed)
- **readme (en + zh)** — enriched Features; new **Supported formats** matrix (read/write by software: VASP, QE, CP2K, ABACUS, ORCA, Gaussian, CASTEP, SIESTA, OpenMX, LAMMPS, GROMACS, AMBER, ASE, phonopy, SPARK + generic/molecular); new **Keyboard shortcuts** reference; new **Editions & scope** matrix.
- **VS Code extension** — fixed description (dropped unsupported DCD/XTC/TRR, added real breadth) and an accurate Scope section: the extension embeds the full single-window viewer (view/edit/measure/save/export + toolbar builders/analysis/OPTIMADE), and the *desktop-shell-only* parts are the multi-pane workspace, the standalone workflow DAG editor, and the HPC terminal/job manager.
- **catbot-plugin** — accurate, broader description; version → 1.3.0.
- **CHANGELOG** + desktop **releaseBody** — 1.3.0 notes, Linux downloads added.

### Tagging
After merge, push `v1.3.0` to fan out the release workflows (desktop draft release, VSIX publish, sidecar binaries).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cd478cc5678`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.