# Issue

**Title:** feat!: bundle IO/viz/SELFIES into the core install

## Description

Remove the runtime `datamol[io]`, `datamol[viz]` and `datamol[selfies]` extras and move their dependencies into the core install, so every capability works out of the box with `pip install datamol`. Only test/docs/dev tooling groups remain.

- Core deps now include cloud filesystems (s3fs, gcsfs), Excel/Parquet (openpyxl, xlsxwriter, pyarrow), viz (matplotlib, networkx, nglview, pillow) and selfies.
- CI, env.yml, README and docs updated; selfies lazy-import hint no longer references a removed extra (lazy imports kept so `import datamol` stays light).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb376ecc8936`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.