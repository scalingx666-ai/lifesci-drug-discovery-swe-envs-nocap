# Issue

**Title:** Properly block (de-)serialization for `CustomTransformation`

## Description

This PR adds proper blocking of (de-)serialization of `CustomTransformation` by registering the corresponding hooks.

So far, attempting to serialize this kind of object already failed, but not because of a hook: The type hints of the `TensorCallable` use `Tensor`, and since this is imported lazily, an attempt to use serialization fails with a rather confusing `NameError` as this import cannot be resolved.

To fix the, a `TypeAliasType` was constructed as this is evaluated lazily.

An alternative would have been to use

```python
register_unstructure_hook_func(lambda cls: cls is CustomTransformation, block_serialization_hook)
```

which would not require changes to `TensorCallable` as this doesn't read the class's annotations. Would also be fine to implement this variant, but since this fixes only the *sympton* and not the *cuase*, I went with this approach here. LMK what you prefer :)

Also, no Changelog entry as serialization was technically already impossible before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d285c73a48b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.