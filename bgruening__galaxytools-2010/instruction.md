# Issue

**Title:** CPAT: add dbkey column to all_fasta data table

## Description

CPAT's `tool_data_table_conf.xml.sample` declares `all_fasta` with the
columns `value, name, path`. The standard `all_fasta` table, and every
other tool in this repo that declares it (bismark, instagraal, jbrowse2,
methyldackel, nanopolish), uses `value, dbkey, name, path`.

Galaxy 26.1 refuses to register a data table whose columns conflict with
an already registered table of the same name. On any Galaxy that already
has `all_fasta`, installing CPAT 3.0.5+galaxy1 (`7ccc6234b54e`) fails, and
the tool doesn't load:

```
Data table 'all_fasta' is already registered with columns {'value': 0, 'dbkey': 1, 'name': 2, 'path': 3},
refusing to register conflicting columns {'value': 0, 'name': 1, 'path': 2}.
```

The mismatch arrived with the built-in reference option (#1459).
3.0.4+galaxy0 has no data table and installs fine. This blocks the GTN
*Genome-wide alternative splicing analysis* workflow, which pins
3.0.5+galaxy1.

## Changes

- `tool_data_table_conf.xml.sample` and `.test`: columns become
  `value, dbkey, name, path`.
- `tool-data/all_fasta.loc.sample` and `test-data/all_fasta.loc.test`: add
  the `dbkey` column.
- Bump `VERSION_SUFFIX` to 2.

The tool reads the path as `fields.path`, so the command template is
unchanged.

## Testing

- `planemo lint` and `planemo shed_lint --tools --ensure_metadata`: no
  warnings.
- `planemo test --biocontainers`: all 3 tests pass, including the
  built-in reference test, which loads the updated `all_fasta` table.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<sub>Summary compiled by Claude (Claude Code), working with @afgane.</sub>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10636efa2c06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.