# Issue

**Title:** Use empty dictionary for empty native_files to maintain consistency w…

## Description

…ith keywords, extras and other dict objects in models

<!-- Thank you for your contribution! -->

## Description
`QCElemental's` default behavior has been to include empty dictionaries for `dict` objects on `AtomicInput/AtomicResult` objects. This default allows for nice behavior like checking for the presence of keys of interest with the usual code without having to first check that `keywords` or `extras` is not `None`:

```python
if my_atomic_input.keywords.get('mykey'):
    # do something

if my_atomic_input.extras.get('mykey'):
    # do something
```

The `native_files` field deviates from this standard and requires additional checks to access its fields:
```python
if my_atomic_result.native_files:
    if my_atomic_result.native_files.get("mykey")
        # do something
```
I propose the previous standard be maintained as I think it makes working with the objects cleaner and more consistent :)

## Changelog description
Use empty dictionary for empty `native_files` to maintain consistency with `keywords`, `extras` and other dict objects in models

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ x] Code base linted
- [ x] Ready to go

@bennybp lemme know if you have any thoughts :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d04a380fd80e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.