# Issue

**Title:** Use view.layout.{width,height} for _set_size

## Description

# Before this change:
<img width="1196" alt="Screen Shot 2019-06-03 at 10 59 55 PM" src="https://user-images.githubusercontent.com/4451957/58848149-754e8b00-8653-11e9-8da5-357f94e6ff9b.png">

# This change
<img width="1181" alt="Screen Shot 2019-06-03 at 10 58 58 PM" src="https://user-images.githubusercontent.com/4451957/58848157-7d0e2f80-8653-11e9-82f0-a426e7e932e8.png">

We don't need to call the private method `_set_size` anymore.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `933790e523c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.