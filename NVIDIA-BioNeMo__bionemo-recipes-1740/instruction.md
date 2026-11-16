# Issue

**Title:** fix(evo2): print_pid takes a single message argument

## Description

## Description

The `debug` branch in the ZeRO-3 checkpoint conversion helper calls `print_pid` with two arguments:

```python
# recipes/evo2_megatron/src/bionemo/evo2/utils/checkpoint/zero3_conversion_lib.py:276
        if debug:
            print_pid("Found buffers:", buffer_names)
```

but `print_pid` takes exactly one:

```python
# same file, :100
def print_pid(msg: str):
    """Prints the process ID along with a message."""
    pid = os.getpid()
    print(f"{pid=}:{msg}")
```

so turning on the module-level `debug` flag (`debug = 0` at :72) turns this branch into a crash:

```
TypeError: print_pid() takes 1 positional argument but 2 were given
```

Every other `print_pid` call in the file — `:290`, `:400`, `:413`, `:416`, `:424`, `:436`, `:444`, and the rest — passes a single f-string. This one call kept the two-argument `print(...)` shape it had before `print` was swapped for `print_pid`. It is the only `if debug:` branch in the file that does not work.

## Fix

Fold the value into the message, matching the surrounding call sites:

```python
            print_pid(f"Found buffers: {buffer_names}")
```

Per `AGENTS.md` and `ci/scripts/check_copied_files.py`, `recipes/evo2_megatron/src/bionemo/evo2` is the source for `recipes/evo2_phage_gen/src/bionemo/evo2`, so the same one-line change is mirrored into the destination copy (its copied-file notice is left intact — the two files are otherwise byte-identical, which I confirmed by diffing the blobs on `main`).

## Verification

Extracted the real `print_pid` from `main` with `ast` and replayed both call shapes:

```
BEFORE line 276 -> TypeError: print_pid() takes 1 positional argument but 2 were given
AFTER : pid=50040:Found buffers: ['a.buf', 'b.buf']
```

`ruff 0.12.8` (the `.pre-commit-config.yaml` pin) with the repo's `.ruff.toml`: `2 files already formatted`, and `ruff check` reports nothing new — the one pre-existing `RUF100` per file (the unused `# noqa: PERF402` at `:288`) is present on unpatched `main` too and is untouched here.

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39d06c085a21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.