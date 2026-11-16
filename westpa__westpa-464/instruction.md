# Issue

**Title:** Codecov setup update

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Trying to remove this error, since "file" keyword has been replaced/deprecated in favor of "files" . See README in here: https://github.com/codecov/codecov-action
```
CodeCov
Unexpected input(s) 'file', valid inputs are ['binary', 'codecov_yml_path', 'commit_parent', 'directory', 'disable_file_fixes', 'disable_search', 'disable_safe_directory', 'dry_run', 'env_vars', 'exclude', 'fail_ci_if_error', 'files', 'flags', 'git_service', 'gcov_args', 'gcov_executable', 'gcov_ignore', 'gcov_include', 'handle_no_reports_found', 'job_code', 'name', 'network_filter', 'network_prefix', 'os', 'override_branch', 'override_build', 'override_build_url', 'override_commit', 'override_pr', 'plugins', 'report_code', 'report_type', 'root_dir', 'skip_validation', 'slug', 'swift_project', 'token', 'url', 'use_legacy_upload_endpoint', 'use_oidc', 'verbose', 'version', 'working-directory']

```

For example error see annotation here: https://github.com/westpa/westpa/actions/runs/12284905372/job/34281739464

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x]  Less Errors/Annotations in CI

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/test.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8223b1fa625f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.