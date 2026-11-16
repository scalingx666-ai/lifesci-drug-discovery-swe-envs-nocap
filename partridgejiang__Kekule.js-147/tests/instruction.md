# Issue

**Title:** Bump debug from 2.2.0 to 4.1.1 in /src/_extras/MoodleExtensions/jsServer

## Description

Bumps [debug](https://github.com/visionmedia/debug) from 2.2.0 to 4.1.1.
<details>
<summary>Release notes</summary>

*Sourced from [debug's releases](https://github.com/visionmedia/debug/releases).*

> ## 4.1.1
> This  backport fixes a bug in coveralls configuration as well as the `.extend()` function.
> 
> # Patches
> 
> - test: only run coveralls on travis (, , d0e498f159bd425b3403db38c98fe26a345d4dcd)
> - copy custom logger to namespace extension (, 57ef085703a0158679cc4a56a4980653b828ce51)
>
> ## 4.1.0
> # Minor Changes
> 
> - migrate Makefile to npm scripts (4236585a40787fe60ed625452163299600df2ce6)
> - feat: Return namespaces string when invoking disable() (7ef8b417a86941372074f749019b9f439a1f6ef6)
> 
> Massive _thank you_ to [@&#8203;mblarsen](https://github.com/mblarsen) and [@&#8203;outsideris](https://github.com/outsideris) for knocking out two long-awaited changes.
>
> ## 4.0.1
> This patch restores browserify functionality as well as keeping the intended functionality with Unpkg.com.
> 
> ### Patches
> - fix browserify and supply alternative unpkg entry point (): 99c95e3d54b07a918ad65bc148a2930ea8bfdd02
>
> ## 4.0.0
> A long-awaited release to `debug` is available now: **`4.0.0`**.
> 
> #### Due to the delay in release and the number of changes made (including bumping dependencies in order to mitigate vulnerabilities), it is highly recommended maintainers update to the latest package version and _test thoroughly_.
> 
> #### This release drops support for Node 4 and 5 in alignment with the [Node.js LTS Release Schedule](https://github.com/nodejs/Release).
> 
> ---
> 
> ### Major Changes
> - move to XO (): ba8a424d41e9dc6129e081ac3aa9715be6a45fbd
> - add Node.js 10, remove Node.js 4 (): 05b0ceb8856bc7b6bb0f2adc3de5cae3cea9c872
> 
> ### Minor Changes
> - bump vulnerable packages: 853853f9f588044d76df3daf1959ca56c5f341b7
> - Fix nwjs support (): 207a6a2d53507ec9dd57c94c46cc7d3dd272306d
> - add instance extends feature (): e43e5fed177b8698674748063f4ed1aaba1d59c8
> - Add TVMLKit support (): 02b9ea9fd7ec95c42de47da13b4b6bb8e50025d8
> 
> ### Patches
> - clean up builds: 3ca23316a470f6bc6e0d75d297179cfc19bbc763
> - remove needless command aliases in makefile: 9f4f8f59ba745166b0c014a61c76de5e73d4841a
> - no longer checking for BROWSER=1: 623c08ef73f8211278d5596c88041c65a2a58ee7
> - fix tests: 57cde56e43003f6b404d4b3d9d76b74aafaeeec8
> - clean up makefile: 62822f12668e8a0b1d1a4fd5a1c2fce1d8715da3
> - fix tests: 833b6f84c8f8dc5b6f13da38ab0ef8a8ff86c0c9
> - add .editorconfig: 2d2509e26bf6df1e1954267e3b1a1cb83973fb09
> - add yarn-error.log to .gitignore: 7e1d5d94f31b37b460fb8d88000ab7ed0be3597e
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  4.1.1
-  remove .coveralls.yaml
-  copy custom logger to namespace extension ()
-  test: only run coveralls on travis
-  4.1.0
-  feat: Return namespaces string when invoking disable()
-  migrate Makefile to npm scripts
-  4.0.1
-  fix browserify and supply alternative unpkg entry point ()
-  4.0.0
- Additional commits viewable in [compare view](https://github.com/visionmedia/debug/compare/2.2.0...4.1.1)
</details>
<details>
<summary>Maintainer changes</summary>

This version was pushed to npm by [qix](https://www.npmjs.com/~qix), a new releaser for debug since your current version.
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=debug&package-manager=npm_and_yarn&previous-version=2.2.0&new-version=4.1.1)](https://help.github.com/articles/configuring-automated-security-fixes)

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

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/partridgejiang/Kekule.js/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6ae8ad2ae5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.