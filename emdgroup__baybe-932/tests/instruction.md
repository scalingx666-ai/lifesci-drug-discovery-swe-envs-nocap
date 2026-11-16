# Issue

**Title:** Fix `get_subclasses` typing for mypy 2.4

## Description

mypy 2.4 bundles an updated typeshed in which `type.__subclasses__` is typed as `(self: type[_T]) -> list[type[_T]]` (). On our `TypeVar("_C", bound=type)`, this now resolves to `list[type[Never]]`, so `get_subclasses` fails type checking.

### Changes (`baybe/utils/basic.py`)
- `get_subclasses` now has the signature `type[_T] -> list[type[_T]]`, matching the new typeshed signature. The unused `_C` TypeVar is removed.
- `find_subclass` now has the signature `type[_T] -> type[_T]`, because mypy can no longer infer the element type from a bare `type` argument.

Callers get the same types as before. For example, `get_subclasses(Surrogate)` still returns `list[type[Surrogate]]`. mypy 2.3.1, mypy 2.4.0 and pyrefly all pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5778b0cc2377`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.