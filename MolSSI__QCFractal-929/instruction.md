# Issue

**Title:** add optional progress bar to client for downloading files

## Description

## Description
This PR adds a progress bar to `download_file` in `client_base` by using `tqdm`. Two new optional arguments are added to `download_file`:

* `show_progress` - This indicates whether or not to show a progress bar for a particular downloaded file. It is set to `False` by default to keep default behavior the same (I am unsure of where else the function is used, and I imagine that you do not always want a progress bar)
* `expected_size` - This is the expected size of the file. If an expected size is provided to tqdm, it will show a bar. Otherwise, it will just print the speed.

I set chunk size when using tqdm because when set to `None` I was not seeing the progress bar update (would sit at zero and suddenly increase at the end). This size (8 MB) worked well for showing progress and actually resulted in faster speeds than no chunk size (tested on server).

In order for this progress bar to be displayed when downloading views, I also added passing these arguments to `download_external_file` in client.

Sample status bar:
```
Downloading to dataset_353_view.sqlite: 100%|██████████████████████| 22.1G/22.1G [00:54<00:00, 433MB/s]
```

## Status
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b002d0d2c8b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.