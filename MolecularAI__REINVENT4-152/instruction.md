# Issue

**Title:** feat: make reinvent an executable module

## Description

Make it possible to execute `reinvent` as an [executable module](https://docs.python.org/3/library/__main__.html#main-py-in-python-packages):

```shell
python -m reinvent --help
```

This uses the same function used by the `reinvent` script defined in `pyproject.toml`; calling `python -m reinvent` is identical to using the `reinvent` command.

This will make it easy to configure the VSCode debugger to launch `reinvent` in debug mode. Add this to the `.vscode/launch.json`:

```json
{
    "name": "Reinvent",
    "type": "debugpy",
    "request": "launch",
    "module": "reinvent",
    "console": "integratedTerminal",
    "args": [
        "sampling.toml"
    ]
}
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6881498b3b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.