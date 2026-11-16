# Issue

**Title:** Log a failure when can_delete is False

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

This is my attempt at fixing 

I updated `_delete_model_by_id` to return True if `can_delete` is true and to return False if `can_delete` is False. That way, we can track if we tried to delete a model or not and then update the messaging accordingly.

So the output looks like this now if docker is stopped/paused:
<img width="478" height="336" alt="image" src="https://github.com/user-attachments/assets/4c9cfe82-c1ce-46b1-9610-edbf078f2100" />

And I also did a manual test to ensure that `ersilia delete --all` still works when docker is running:
<img width="594" height="227" alt="image" src="https://github.com/user-attachments/assets/75a69d30-0c84-44ab-99b4-631bee247141" />

**Changes to be made**

So I updated `_delete_model_by_id` to return a boolean, but I was also thinking that we could raise an exception if can_delete is false. Please let me know what your preference is here 🙇

**Status**

I have the change and I wrote a test, but I need to run the test to make sure it works. I tried running it locally with `pytest`, `pytest -v`, and `pytest test/cli/test_delete.py`, but it was taking a long time to execute....

I also tried [running the workflow in my fork](https://github.com/Lehcar/ersilia/actions/runs/19494367945/job/55792974202), but it returned "No results available."

**To do**
I'm waiting to see if the workflows pass on this PR before I mark this ready for review


Related to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3aed98ca4b91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.