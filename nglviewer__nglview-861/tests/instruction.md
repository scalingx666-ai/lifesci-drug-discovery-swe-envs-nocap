# Issue

**Title:** Bump eslint from 3.19.0 to 6.6.0 in /js

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 3.19.0 to 6.6.0.
<details>
<summary>Release notes</summary>

*Sourced from [eslint's releases](https://github.com/eslint/eslint/releases).*

> ## v6.6.0
> *  Update: false positives in function-call-argument-newline () () (Scott O'Hara)
> *  Update: improve report location for no-trailing-spaces () () (Milos Djermanovic)
> *  Update: no-trailing-spaces false negatives after comments () () (Milos Djermanovic)
> *  Fix: no-misleading-character-class crash on invalid regex () () (Milos Djermanovic)
> *  Update: Add enforceForIndexOf option to use-isnan () () (Milos Djermanovic)
> *  Update: measure plugin loading time and output in debug message () (Victor Homyakov)
> *  Fix: operator-assignment removes and duplicates comments () (Milos Djermanovic)
> *  Fix: operator-assignment invalid autofix with adjacent tokens () (Milos Djermanovic)
> *  Fix: CLIEngine#addPlugin reset lastConfigArrays () () (Toru Nagashima)
> *  Chore: Fix lint failure in JSDoc comment () (Brandon Mills)
> *  Update: Add ignored prop regex no-param-reassign () (Luke Bennett)
> *  Chore: Remove unused parameter in dot-location () (Milos Djermanovic)
> *  Fix: no-obj-calls false positive () () (Toru Nagashima)
> *  Fix: problematic installation issue () () (Toru Nagashima)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Docs: Add note about Node.js requiring SSL support () () (Nicholas C. Zakas)
> *  Fix: improve report location for no-tabs () (Milos Djermanovic)
> *  Update: Enable function string option in comma-dangle () () (YeonJuan)
> *  Docs: fix doc for no-unneeded-ternary rule () () (Sam Rae)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Chore: Provide debug log for parser errors () (Brad Zacher)
> *  Update: enforceForOrderingRelations no-unsafe-negation () () (Sam Rae)
> *  Update: improve report location for no-mixed-operators () (Chiawen Chen)
> *  Fix: prefer-numeric-literals invalid autofix with adjacent tokens () (Milos Djermanovic)
> *  Update: enforceForNewInMemberExpressions no-extra-parens () () (Milos Djermanovic)
> *  Fix: array-bracket-newline consistent error with comments () () (Milos Djermanovic)
> *  Fix: report full dot location in dot-location () (Milos Djermanovic)
> *  Update: make isSpaceBetweenTokens() ignore newline in comments () (YeonJuan)
> *  Update: remove default overrides in keyword-spacing () () (YeonJuan)
> *  Update: improve report location for no-space-in-parens () (Chiawen Chen)
> *  Update: improve report location for no-multi-spaces () (Chiawen Chen)
> *  Upgrade: bump inquirer to ^7.0.0 () (Joe Graham)
> *  Chore: Add a script for testing with more control () (Eric Wang)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  New: pass cwd from cli engine () (Eric Wang)
> *  Update: no-self-assign should detect member expression with this () (Tibor Blenessy)
> *  Docs: Clarify `eslint:recommended` semver policy () (Kevin Partington)
> *  Docs: Fixes object type for `rules` in "Use a Plugin" () (Daisy Develops)
> *  Docs: Fix typo in v6 migration guide () (Benjamim Sonntag)
> *  Chore: update version parameter name () (Toru Nagashima)
> *  Chore: enable jsdoc/require-description () (Kai Cataldo)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Chore: Clean up inline directive parsing () (Jordan Eldredge)
> *  Docs: fix wrong max-depth example () () (Gabriel R Sezefredo)
> *  Docs: Fix minor formatting/grammar errors () (cherryblossom000)
> *  Docs: Fix missing word in sentence () (Dan Boulet)
> *  Chore: enable additional eslint-plugin-jsdoc rules () (Kai Cataldo)
> *  Chore: update issue template with --eslint-fix flag () (James George)
> *  Sponsors: Sync README with website (ESLint Jenkins)
></tr></table> ... (truncated)
</details>
<details>
<summary>Changelog</summary>

*Sourced from [eslint's changelog](https://github.com/eslint/eslint/blob/master/CHANGELOG.md).*

> v6.6.0 - October 25, 2019
>
> *  Update: false positives in function-call-argument-newline () () (Scott O'Hara)
> *  Update: improve report location for no-trailing-spaces () () (Milos Djermanovic)
> *  Update: no-trailing-spaces false negatives after comments () () (Milos Djermanovic)
> *  Fix: no-misleading-character-class crash on invalid regex () () (Milos Djermanovic)
> *  Update: Add enforceForIndexOf option to use-isnan () () (Milos Djermanovic)
> *  Update: measure plugin loading time and output in debug message () (Victor Homyakov)
> *  Fix: operator-assignment removes and duplicates comments () (Milos Djermanovic)
> *  Fix: operator-assignment invalid autofix with adjacent tokens () (Milos Djermanovic)
> *  Fix: CLIEngine#addPlugin reset lastConfigArrays () () (Toru Nagashima)
> *  Chore: Fix lint failure in JSDoc comment () (Brandon Mills)
> *  Update: Add ignored prop regex no-param-reassign () (Luke Bennett)
> *  Chore: Remove unused parameter in dot-location () (Milos Djermanovic)
> *  Fix: no-obj-calls false positive () () (Toru Nagashima)
> *  Fix: problematic installation issue () () (Toru Nagashima)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Docs: Add note about Node.js requiring SSL support () () (Nicholas C. Zakas)
> *  Fix: improve report location for no-tabs () (Milos Djermanovic)
> *  Update: Enable function string option in comma-dangle () () (YeonJuan)
> *  Docs: fix doc for no-unneeded-ternary rule () () (Sam Rae)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Chore: Provide debug log for parser errors () (Brad Zacher)
> *  Update: enforceForOrderingRelations no-unsafe-negation () () (Sam Rae)
> *  Update: improve report location for no-mixed-operators () (Chiawen Chen)
> *  Fix: prefer-numeric-literals invalid autofix with adjacent tokens () (Milos Djermanovic)
> *  Update: enforceForNewInMemberExpressions no-extra-parens () () (Milos Djermanovic)
> *  Fix: array-bracket-newline consistent error with comments () () (Milos Djermanovic)
> *  Fix: report full dot location in dot-location () (Milos Djermanovic)
> *  Update: make isSpaceBetweenTokens() ignore newline in comments () (YeonJuan)
> *  Update: remove default overrides in keyword-spacing () () (YeonJuan)
> *  Update: improve report location for no-space-in-parens () (Chiawen Chen)
> *  Update: improve report location for no-multi-spaces () (Chiawen Chen)
> *  Upgrade: bump inquirer to ^7.0.0 () (Joe Graham)
> *  Chore: Add a script for testing with more control () (Eric Wang)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  New: pass cwd from cli engine () (Eric Wang)
> *  Update: no-self-assign should detect member expression with this () (Tibor Blenessy)
> *  Docs: Clarify `eslint:recommended` semver policy () (Kevin Partington)
> *  Docs: Fixes object type for `rules` in "Use a Plugin" () (Daisy Develops)
> *  Docs: Fix typo in v6 migration guide () (Benjamim Sonntag)
> *  Chore: update version parameter name () (Toru Nagashima)
> *  Chore: enable jsdoc/require-description () (Kai Cataldo)
> *  Sponsors: Sync README with website (ESLint Jenkins)
> *  Chore: Clean up inline directive parsing () (Jordan Eldredge)
> *  Docs: fix wrong max-depth example () () (Gabriel R Sezefredo)
> *  Docs: Fix minor formatting/grammar errors () (cherryblossom000)
> *  Docs: Fix missing word in sentence () (Dan Boulet)
> *  Chore: enable additional eslint-plugin-jsdoc rules () (Kai Cataldo)
> *  Chore: update issue template with --eslint-fix flag () (James George)
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  6.6.0
-  Build: changelog update for 6.6.0
-  Update: false positives in function-call-argument-newline () (...
-  Update: improve report location for no-trailing-spaces () ()
-  Update: no-trailing-spaces false negatives after comments () (...
-  Fix: no-misleading-character-class crash on invalid regex () (...
-  Update: Add enforceForIndexOf option to use-isnan () ()
-  Update: measure plugin loading time and output in debug message ()
-  Fix: operator-assignment removes and duplicates comments ()
-  Fix: operator-assignment invalid autofix with adjacent tokens ()
- Additional commits viewable in [compare view](https://github.com/eslint/eslint/compare/v3.19.0...v6.6.0)
</details>
<details>
<summary>Maintainer changes</summary>

This version was pushed to npm by [eslintbot](https://www.npmjs.com/~eslintbot), a new releaser for eslint since your current version.
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=3.19.0&new-version=6.6.0)](https://help.github.com/articles/configuring-automated-security-fixes)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/arose/nglview/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `480357077b73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.