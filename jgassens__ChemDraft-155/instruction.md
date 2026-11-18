# Issue

**Title:** Windows: retry an atomic file replace briefly when the target is busy

## Description

On Windows, replacing a file by rename can fail for a moment with "Access is denied" (os error 5) or a sharing violation (32) while another writer or reader holds the destination. `tests::concurrent_atomic_writes_to_one_path_never_publish_a_torn_file` tripped on this intermittently on Windows (seen by the Windows session; 10/10 when run alone).

- The final replace retries up to 10 times with a 20 ms backoff (≈180 ms worst case) for those two errors only, then reports the error and removes its temp file.
- `cfg(windows)` only; macOS behaviour is unchanged.
- Retry policy covered by injected unit tests that run on both platforms.

**Review:** Astra (rvatomicdoc-20261020/rvatomic) APPROVE.
**Tests:** cargo fmt, clippy, 334 tests on macOS; Windows run pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f0da344c188`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.