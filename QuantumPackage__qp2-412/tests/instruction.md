# Issue

**Title:** ezfio_interface: create data/qp_edit_config without racing

## Description

`ninja` runs `ei_handler.py --path_module` once per module, all in parallel (43 such edges in the current manifest). On a tree where `data/qp_edit_config/` does not exist yet — first build of a fresh tree, or after any `rm -rf` of that directory — every one of them calls `_write`, whose directory creation is check-then-act:

```
FileExistsError: [Errno 17] File exists: '/Users/scemama/qp3/data/qp_edit_config'
  qp_edit_config.py:326 in _write  <- save_module_config:334 <- emit_module:397 <- ei_handler.py:621
FAILED: [10/923] ei_handler.py --path_module .../src/bitmask
```

and the whole build aborts. A rerun passes because the directory then exists — a lost create-race, not a logic error.

Fix: `os.makedirs(directory, exist_ok=True)`.

`_write` is the only writer of these files, and handler/module ids are unique across modules, so no two edges touch the same `.toml`; the directory is the only shared mutable object.

### Evidence (laptop, 2026-11-12)

- **Synchronized-entry control** (43 writers released on one common epoch): pre-fix 10/10 iterations fail with 3-8 `FileExistsError`; post-fix 10/10 clean, 43/43 files written.
- Naive replay of the 43 real manifest command lines passes 10/10 **both** pre- and post-fix — the window is microseconds and Python startup spreads the processes over ~0.3 s, so that replay is not a discriminator. Worth knowing for anyone re-testing this.
- One manifest pass with `data/qp_edit_config` removed and every `EZFIO.cfg` touched: exit 0, 43/43 `ei_handler` edges reran, zero `FileExistsError`.
- `data/qp_edit_config/registry.toml` is produced by `build_rust_tools.sh`, not by the module graph: removing the directory also requires `ei_handler.py generate_registry`.

The identical one-liner is queued on the qp2 `rust-rewrite` line (local commit `310194a8`), since `qp2` `dev-stable` does not carry this file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98d230abfc6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.