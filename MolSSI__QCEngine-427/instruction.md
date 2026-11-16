# Issue

**Title:** Fix parse_environment task_config

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Fixed a minor bug introduced at #400

Expected behavior
```python
>>> os.environ["SCRATCH"] = "/my_scratch"
>>> qcng.get_config(task_config={"scratch_directory": "$SCRATCH"})
<JobConfig ncores=2 memory=2.506 scratch_directory='/my_scratch'>
```

observed behavior
```python
>>> os.environ["SCRATCH"] = "/my_scratch"
>>> qcng.get_config(task_config={"scratch_directory": "$SCRATCH"})
<JobConfig ncores=2 memory=2.506 scratch_directory='$SCRATCH'>
```

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbec059bb521`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.