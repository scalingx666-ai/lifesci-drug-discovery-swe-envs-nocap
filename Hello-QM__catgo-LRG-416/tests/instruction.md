# Issue

**Title:** fix(workflow): batch_submitter honors base_work_dir (fixes parallel-job permission-denied)

## Description

Parallel/fan-out HPC tasks go through `batch_submitter`, which read only `config[paths][base_dir]`. The run config sets `base_work_dir` (promoted to `hpc.base_work_dir` by the scanner), so base_dir was empty and the batch dir became `/<workflow_id>/...` → `mkdir: cannot create directory: Permission denied` at the filesystem root.

Resolve base_dir via the same chain as `resolve_work_dir` (paths.base_dir → hpc.base_work_dir → base_work_dir → ~/calculations).

**Found live**: the ORR workflow's clean-slab geo_opt completed (2h47m VASP run), then its 3 parallel adsorbate geo_opts all failed with this permission-denied error.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `069fb7ff72d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.