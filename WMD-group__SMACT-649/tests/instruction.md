# Issue

**Title:** security: run CI on pull_request instead of pull_request_target

## Description

Closes the one open CodeQL alert: `actions/untrusted-checkout/high` at `.github/workflows/ci.yml:46`.

## The problem

`ci.yml` triggered on `pull_request_target`, which runs in the context of the **base** repository with its secrets, and then explicitly checked out the fork's commit:

```yaml
on:
  pull_request_target:
...
      - name: Checkout repository
        uses: actions/checkout@v6
        with:
          ref: ${{ github.event.pull_request.head.sha }}
```

and ran `uv sync --extra optional --extra property_prediction --dev`, `uv run pre-commit run --all-files` and `uv run pytest` against it. All three execute code the pull request controls — build hooks, pre-commit hook definitions, test code — in a job holding `secrets.MP_API_KEY` and `secrets.CODECOV_TOKEN`.

The workflow-level `permissions: contents: read` constrains the `GITHUB_TOKEN`, which is good, but does nothing about the secrets. Any pull request from a fork could read them.

## The fix

`pull_request`. Fork jobs get no secrets and a read-only token, so there is nothing to exfiltrate. It also means the workflow definition comes from the pull request, so a change to this file is validated before merge rather than after — this PR's own first run exercises the new configuration, which `pull_request_target` could not do.

`packaging.yml` already works this way and carries a comment explaining why; ci.yml just predates it. Added a matching comment.

The explicit `ref:` goes too. Under `pull_request` the default checkout is the merge commit, which is the more useful thing to test, and the `workflow_call` path from `publish-to-pypi.yml` has no `pull_request` payload so it resolved to the default already.

## One behaviour change worth knowing about

Fork pull requests no longer receive secrets, which affects two steps:

- `test_download_compounds_with_mp_api` skips without `MP_API_KEY`, which is what its `skipif` is for. It still runs for branch PRs and for `push` to master. #647 made the two key sources it accepts consistent.
- The Codecov upload sets `fail_ci_if_error: true`, so a missing `CODECOV_TOKEN` would turn into a red build for an external contributor. Guarded the step to same-repo events instead.

## Verification

`pre-commit run --files .github/workflows/ci.yml` passes; the YAML parses with the expected triggers (`pull_request`, `push`, `workflow_call`), `permissions: contents: read`, and neither checkout step carrying a `with:` block.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6763ba2017f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.