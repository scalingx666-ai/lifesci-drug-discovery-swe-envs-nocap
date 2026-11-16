# Issue

**Title:** Creating python API for Nox sessions

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description:**  
This PR transitions the execution process from command-line-based operations to utilizing the `NoxRunner`. The API provides an improved, structured interface for running Nox sessions such as `setup` and `test_from_github`.  Also allows group execution and single execution.

**Example:**  
```python
import os
from test.playground.runner import NoxRunner

BASE_PATH = "test/playground"

config_path = os.path.join(
    os.getcwd(), 
    BASE_PATH, 
    "config.yml"
)
noxfile = os.path.join(
    os.getcwd(), 
    BASE_PATH, 
    "noxfile.py"
)
if __name__ == "__main__":
    runner = NoxRunner(config_path=config_path, noxfile=noxfile)
    runner.setup()
    runner.test_from_github()
    runner.execute_all()
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff9e2b6d6caf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.