# Issue

**Title:** Lazify `get_candidates`

## Description

Another step closer to lazification. Finally avoids candidate materialization by offering an appropriate lazy interface.

**Why the two-method interface?**

`get_candidates()` is part of the public API and must return a native type – returning a narwhals wrapper would leak an implementation detail to users. The natural return type for a potentially large candidate set is a lazy frame, so callers can defer materialization until they actually need the data.

The tension is: internal library callers need an *eager* narwhals `DataFrame` to perform operations like `.filter()`, positional indexing, and `.sample()`. If `get_candidates()` returned the native lazy frame, every such caller would need to re-wrap it in narwhals and normalize before collecting:

```python
# with a single public get_candidates() -> IntoLazyFrame
candidates = nw.from_native(subspace.get_candidates()).lazy().collect()

# with the two-method design
candidates = subspace._get_candidates().collect()
```

The `.lazy()` call in the first form is unavoidable: for a pandas-backed result, `nw.from_native(pd.DataFrame)` gives a `nw.DataFrame` (not a `nw.LazyFrame`), so `.collect()` does not exist on it without normalizing through `.lazy()` first. This boilerplate would appear at every internal call site.

The two-method design resolves this cleanly:

- **`get_candidates() -> IntoLazyFrame`**: public API, returns the native lazy frame. Callers own the decision of when to materialize.
- **`_get_candidates() -> nw.LazyFrame`**: private, stays in narwhals. Internal callers collect exactly when and how they need to (eager frame, specific native type, or a lazy aggregation like a row count), without any re-wrapping overhead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f40f477c6ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.