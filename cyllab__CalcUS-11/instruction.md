# Issue

**Title:** Project is now preselected based on previously selected project when running new calculation

## Description

Now the previously selected project is preselected, when we open the new calculation page. If there is no preselected project, it will by default select the project alphabetically. I have used [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) for this implementation (It stores data without any expiration date) and using the database was unnecessary for this purpose. Below is the screen recording of the implementation.

https://drive.google.com/file/d/1HBEBgid9jqkifrktpU9oRJ-qTyLaAD7C/view?usp=sharing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a051a6ad6cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.