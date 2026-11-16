# Issue

**Title:** Remove duplicate flag --repo_path from the fetch command

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

The `--repo_path` and `--from_dir` flags both serve the same purpose: specifying the local path to a model's directory. Right now, `--from_dir` is only used to set the model source, while most users rely on `--repo_path` to load local models. To keep naming consistent with other flags (like `--from_github` and `--from_dockerhub`), we should use `--from_dir` and remove `--repo_path`.

**Changes to be made**

- [x] Remove the [`--repo_path`](https://github.com/ersilia-os/ersilia/blob/bb202b261bb6d4bbe658d207aba7f0c3de495787/ersilia/cli/commands/fetch.py#L25) flag in favor of only keeping the --`from_dir` flag.
- [x] For sake of backward compatibility and not breaking the rest of the code, we can set [`repo_path`](https://github.com/ersilia-os/ersilia/blob/bb202b261bb6d4bbe658d207aba7f0c3de495787/ersilia/cli/commands/fetch.py#L108) argument in the `ModelFetcher` class's constructor with the value the user inputs through `from_dir`.

**Status**

Ready to Review

**To do**

- [x] Implementing test for changes, making sure the `fetch` command is working properly 
```python
import unittest
from ersilia.hub.fetch.fetch import ModelFetcher

class TestModelFetcher(unittest.TestCase):
    
    def test_from_dir_priority_when_repo_path_is_set(self):
        fetcher = ModelFetcher(from_dir="test_repo_path")
        self.assertEqual(fetcher.repo_path, "test_repo_path", "repo_path should match the value provided to from_dir")

    def test_from_dir_fallback_when_repo_path_is_none(self):
        fetcher = ModelFetcher(from_dir="fallback_dir")
        self.assertEqual(fetcher.repo_path, "fallback_dir", "from_dir should be used as the primary path")

    def test_no_repo_path_or_from_dir(self):
        fetcher = ModelFetcher(from_dir=None)
        self.assertIsNone(fetcher.repo_path, "repo_path should be None if from_dir is None")

if __name__ == '__main__':
    unittest.main()
```


Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #1370

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `166ba761d301`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.