# Issue

**Title:** tools: update 3Dtrees Potree wrapper to 1.2.0

## Description

## Summary
- bump the 3Dtrees Potree Galaxy wrapper to ghcr.io/3dtrees-earth/3dtrees_potree:1.2.0
- expose the new comma-separated special coloring instance attributes argument with the default PredInstance_SAT,PredInstance_FoMa
- add a multi-segmentation LAZ fixture with two instance segmentations and two species attributes
- update tests to assert both generated coloring attributes and both special coloring mapping JSON files

## Validation
- Rebasing target: bgruening/galaxytools@master (63e12817)
- docker pull ghcr.io/3dtrees-earth/3dtrees_potree:1.2.0
- planemo test --docker --docker_run_extra_arguments "--cpus 10 --memory 50g" --job_workers 1 --test_timeout 1800 tools/3dtrees_potree/3dtrees_potree.xml
- Result: All 2 test(s) executed passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `63e128174aa3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.