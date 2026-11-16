# Issue

**Title:** Unblock v1.1.1 release workflow

## Description

Fix the reusable vendor-security job's missing `contents: read` permission. The attempted `v1.1.0` tag failed at workflow startup before any release or npm publication, and repository rules prevent deleting that tag. Advance package, catalog, and citation metadata to `v1.1.1` for the first publish.

Validation: `npm test` (8 passed), catalog regeneration (281 skills), `git diff --check`.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=74321360"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

No blocking issue was identified.

What we checked:
- Built offline release assets for the previous and updated revisions and ran each revision’s standalone installer. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>
- Both installers exited successfully and tarball checksums were verified; both revisions installed 67 skills. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>
- Executed the release-consumption-check.py script to invoke each revision’s install.sh; both runs exited with code 0. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>
- The HEAD revision lacks a changelog heading matching its VERSION, indicating a release-note ambiguity rather than an execution issue. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>

<h3>Summary</h3>

The PR grants read-only repository access to the reusable vendor-security gate and updates release metadata to 1.1.1.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (2) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d75a5b9527f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.