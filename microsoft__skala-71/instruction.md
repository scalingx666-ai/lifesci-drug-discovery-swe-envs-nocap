# Issue

**Title:** Fix skala.ase import failure on CPU-only environments

## Description

## Root cause

The docs build has been failing since #58 because `docs/ase.ipynb` cannot execute the very first cell:

```python
from skala.ase import Skala
```

The CI traceback (`myst_nb.core.execute.base.ExecutionError`) hides the underlying notebook error; the `linkcheck` step is just the last to surface it (the HTML build hits the same failure a few seconds earlier).

`src/skala/ase/calculator.py` does:

```python
try:
    import skala.gpu4pyscf as skala_gpu
except ImportError as e:
    skala_gpu = None
    gpu4pyscf_import_error = e
```

But `src/skala/gpu4pyscf/__init__.py` had, at module level:

```python
if not torch.cuda.is_available() and find_spec("pytest") is not None:
    import pytest
    pytest.skip(
        "Skipping gpu4pyscf doctests, because CUDA is not available.",
        allow_module_level=True,
    )
```

`pytest.skip(...)` raises `pytest.outcomes.Skipped`, which derives from **`BaseException`**, not `ImportError`. So on any host where (a) CUDA is unavailable and (b) `pytest` is installed — which is every CI runner and every dev env that installs `.[dev]` or `.[doc]` — the `except ImportError` does not catch it, and `import skala.ase` fails with `Skipped`. This breaks both the docs notebook and any CPU-only use of the ASE calculator.

Repro on `main`:

```
$ python -c "from skala.ase import Skala"
...
File "src/skala/gpu4pyscf/__init__.py", line 19, in <module>
    pytest.skip(...)
Skipped: Skipping gpu4pyscf doctests, because CUDA is not available.
```

## Fix

Two coordinated changes.

**1. `src/skala/gpu4pyscf/__init__.py`** — replace the module-level `pytest.skip` with a plain `ImportError`. The `skala.gpu4pyscf` package genuinely requires CUDA, so "module is unusable" is best expressed as `ImportError`, which is the standard signal callers already handle (including `calculator.py`'s `try/except ImportError`). The `find_spec("pytest")` gate is dropped: it was both insufficient (any env with pytest installed triggered the bug) and unnecessary (the module being unimportable on non-CUDA hosts is correct independent of pytest).

**2. `src/skala/conftest.py`** (new) — the original `pytest.skip` was, despite the broken mechanism, trying to do something legitimate: prevent `pytest --doctest-modules --pyargs skala` (used by `.github/workflows/test.yml`) from failing collection of the gpu4pyscf modules on CPU runners. After change (1), pytest collection sees the `ImportError` and errors out. Restore the intended behavior with a `collect_ignore_glob` that skips `gpu4pyscf/*.py` when CUDA is unavailable. The conftest is placed at `src/skala/` rather than inside `src/skala/gpu4pyscf/` because, as a regular package, the inner directory's conftest would itself be imported as `skala.gpu4pyscf.conftest`, triggering the failing `__init__.py` before pytest could read it.

Dedicated tests in `tests/test_gpu4pyscf_*.py` already use their own `pytest.skip(allow_module_level=True)` guard, which is the correct place for that pattern (inside test modules, where pytest does the importing).

## Verification

- `from skala.ase import Skala` works on a CPU-only env.
- The ASE notebook's GPU cells (`Skala(..., device="cuda")` and `calc.set(device="cpu")`) work, because `calculator.py` catches the `ImportError` and only raises at `calculate()` time if `device="cuda"` is actually invoked.
- `sphinx-build -b html docs docs/_build/html` succeeds end-to-end.
- `pytest --doctest-modules --pyargs skala tests/` → 159 passed, 4 skipped on CPU-only env.
- `ruff format`, `ruff check`, `mypy` pass on both changed files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd2c363de508`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.