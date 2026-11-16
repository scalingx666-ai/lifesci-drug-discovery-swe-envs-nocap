# Issue

**Title:** Add GPL-2.0-or-later to accepted licenses and the model request form

## Description

## What

- Adds `GPL-2.0-or-later` to `ersilia/hub/content/metadata/license.txt`, next to the `GPL-2.0-only` entry added in #1954.
- Lists both `GPL-2.0-only` and `GPL-2.0-or-later` in the License dropdown of `.github/ISSUE_TEMPLATE/model_request.yml`. Neither was selectable there, so requesters of GPL-2.0 models could not pick their licence.

## Why

GPL-2.0-only was needed for eos8bpb (MechGate). Models under GPL-2.0-or-later were still rejected by the licence check. The Airtable `Models.License` select already has both options, so metadata updates will not fail as they did after the eos8bpb merge.

## Not run

No tests were run. This only changes a licence list and a form dropdown.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `40f11a18eab3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.