# Issue

**Title:** Lazy-load pandas

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Currently, a little less than half of the time taken to import anything from QCPortal is spend dealing with Pandas. I think most use cases don't involve [its direct use](https://github.com/search?q=repo%3AMolSSI%2FQCFractal%20import%20pandas&type=code), so it can be loaded later when needed. This improvement should propagate to downstream packages which want to i.e. use `PortalClient` or build off of record models but don't need Pandas.

Before:

```shell
$ hyperfine \                                                                    14:31:18  ☁  4ebcd88f ☀
    'python -c "from qcportal import PortalClient"' \
    --prepare \
    'python -c "from qcportal import PortalClient"'
Benchmark 1: python -c "from qcportal import PortalClient"
  Time (mean ± σ):     621.8 ms ±  10.0 ms    [User: 514.2 ms, System: 96.5 ms]
  Range (min … max):   608.4 ms … 642.9 ms    10 runs

```

```shell
$ python -X importtime -c "from qcportal import PortalClient" 2> tuna.log && tuna tuna.log
```

![image](https://github.com/user-attachments/assets/a3ac0112-176b-413b-9eb6-a137259f97ac)

With these changes:

```shell
$ fc                                                                     14:27:45  ☁  lazy-load-pandas ☀
hyperfine \
    'python -c "from qcportal import PortalClient"' \
    --prepare \
    'python -c "from qcportal import PortalClient"'
Benchmark 1: python -c "from qcportal import PortalClient"
  Time (mean ± σ):     375.1 ms ±   7.5 ms    [User: 318.7 ms, System: 50.1 ms]
  Range (min … max):   368.1 ms … 394.3 ms    10 runs
```
## Status
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `655fa6982477`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.