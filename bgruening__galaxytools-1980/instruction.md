# Issue

**Title:** Sync CI workflows with tools-iuc

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

---

Syncs `ci.yaml`, `pr.yaml` and `slash.yaml` with galaxyproject/tools-iuc@99e9631e, like the earlier syncs in #1779, #1717 and #1264.

## Why

Two CI fixes landed upstream that we are missing, and both fail here every day.

**galaxyproject/tools-iuc#8281.** `deploy-report` passes `token: ${{ secrets.PAT }}` to `create-or-update-comment`. `PAT` is not set in this repo, and an empty value overrides the action's own `github.token` default, so the step fails with `Error: Parameter token or opts.auth is required`. 11 of the last 12 pushes to `master` failed this way, 8 of them only because of this, after the ToolShed deploy had already worked (for example [33746959522](https://github.com/bgruening/galaxytools/actions/runs/33746959522)).

**galaxyproject/tools-iuc#8280.** `slash.yaml` started a runner for every issue comment and then failed on the missing `PAT`. The last 8 `issue_comment` runs here are all red. It now only runs when the comment holds the command, and skips the dispatch when no PAT is set. That is what @bgruening asked for in #1944: *"should be configured that its not failing when there are not credentials, because all the tool repos will most likely not use it."*

Both also replace `sharesight/find-github-pull-request` and `8BitJonny/gh-get-current-pr` with a `gh api` call, which clears the two Node 20 warnings. The author of the first  it is unmaintained and suggested not depending on it.

Together these close items 1 to 3 of #1944.

## Also in here

- `actions/checkout` v6 to v7, `actions/setup-python` v6 to v7, `actions/cache` v5 to v6
- `GALAXY_BRANCH` `release_26.0` to `release_26.1`, matching IUC. This changes which Galaxy release tools are tested against.

## The three commits

1. The three files copied from IUC, unchanged.
2. The four `repository_owner` conditions set back to `bgruening`.
3. `deploy-report` given `pull-requests: write`.

Commit 2 is the one to look at. The synced files carry IUC's `repository_owner == 'galaxyproject'`, which would quietly disable the deploy, report and dispatch jobs here. An earlier sync shipped exactly that twice, fixed later in 0901e22f (2022) and db11d789 (2026-02). Keeping it as its own commit makes the upstream content and our local change easy to review apart.

| File | Job |
|---|---|
| `ci.yaml:15` | setup |
| `pr.yaml:415` | deploy |
| `pr.yaml:452` | deploy-report |
| `slash.yaml:8` | dispatch, moved from step to job level by #8280 |

`GALAXY_FORK: galaxyproject` is left alone on purpose.

Commit 3 came out of reviewing this PR. The `permissions` block added by #8281 grants `pull-requests: read`, but the comment target is always a pull request, so the `github.token` fallback would have returned 403 instead of posting. Since we have no PAT, that is our only path. It is now fixed upstream too in galaxyproject/tools-iuc#8405, so the files still match.

## Not included

- `ready-for-review.yaml`, IUC only. It needs `actions/create-github-app-token` with App secrets we do not have. That is the GitHub App from #1944 item 1, still a maintainer call, so porting it would add a workflow that cannot run.
- `ci.yaml`'s two `secrets.PAT` uses stay unguarded. `ci.yaml` only runs on `schedule` or `repository_dispatch`, and both PAT steps need the dispatch payload. A dispatch only happens if `slash.yaml` already used that same secret, so `PAT` is never empty when they run and a guard would be dead code.
- `gxy-*.yml`, ours only, untouched.

## Checks

`.github/**` is in `pr.yaml`'s `paths-ignore`, so this PR does not run the workflows it edits.

- The only difference from IUC is the four `repository_owner` lines above, checked with `diff`.
- `grep repository_owner .github/workflows/*.yaml | grep galaxyproject` gives nothing.
- `actionlint` reports 4 findings. All 4 were already here before the sync and are in IUC too, so nothing new is introduced.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49928178f9ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.