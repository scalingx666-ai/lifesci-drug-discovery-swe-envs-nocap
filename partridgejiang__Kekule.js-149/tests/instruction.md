# Issue

**Title:** Bump morgan from 1.7.0 to 1.9.1 in /src/_extras/MoodleExtensions/jsServer

## Description

Bumps [morgan](https://github.com/expressjs/morgan) from 1.7.0 to 1.9.1.
<details>
<summary>Release notes</summary>

*Sourced from [morgan's releases](https://github.com/expressjs/morgan/releases).*

> ## 1.9.1
>   * Fix using special characters in format
>   * deps: depd@~1.1.2
>     - perf: remove argument reassignment
>
> ## 1.9.0
>   * Use `res.headersSent` when available
>   * deps: basic-auth@~2.0.0
>      - Use `safe-buffer` for improved Buffer API
>   * deps: debug@2.6.9
>   * deps: depd@~1.1.1
>     - Remove unnecessary `Buffer` loading
>
> ## 1.8.2
>   * deps: debug@2.6.8
>     - Fix `DEBUG_MAX_ARRAY_LENGTH`
>     - deps: ms@2.0.0
>
> ## 1.8.1
> - deps: debug@2.6.1
>   - Fix deprecation messages in WebStorm and other editors
>   - Undeprecate `DEBUG_FD` set to `1` or `2`
>
> ## 1.8.0
> - Fix sending unnecessary `undefined` argument to token functions
> - deps: basic-auth@~1.1.0
> - deps: debug@2.6.0
>   - Allow colors in workers
>   - Deprecated `DEBUG_FD` environment variable
>   - Fix error when running under React Native
>   - Use same color for same namespace
>   - deps: ms@0.7.2
> - perf: enable strict mode in compiled functions
</details>
<details>
<summary>Changelog</summary>

*Sourced from [morgan's changelog](https://github.com/expressjs/morgan/blob/master/HISTORY.md).*

> 1.9.1 / 2018-09-10
> ==================
>
>   * Fix using special characters in format
>   * deps: depd@~1.1.2
>     - perf: remove argument reassignment
>
> 1.9.0 / 2017-09-26
> ==================
>
>   * Use `res.headersSent` when available
>   * deps: basic-auth@~2.0.0
>      - Use `safe-buffer` for improved Buffer API
>   * deps: debug@2.6.9
>   * deps: depd@~1.1.1
>     - Remove unnecessary `Buffer` loading
>
> 1.8.2 / 2017-05-23
> ==================
>
>   * deps: debug@2.6.8
>     - Fix `DEBUG_MAX_ARRAY_LENGTH`
>     - deps: ms@2.0.0
>
> 1.8.1 / 2017-02-04
> ==================
>
>   * deps: debug@2.6.1
>     - Fix deprecation messages in WebStorm and other editors
>     - Undeprecate `DEBUG_FD` set to `1` or `2`
>
> 1.8.0 / 2017-02-04
> ==================
>
>   * Fix sending unnecessary `undefined` argument to token functions
>   * deps: basic-auth@~1.1.0
>   * deps: debug@2.6.0
>     - Allow colors in workers
>     - Deprecated `DEBUG_FD` environment variable
>     - Fix error when running under React Native
>     - Use same color for same namespace
>     - deps: ms@0.7.2
>   * perf: enable strict mode in compiled functions
</details>
<details>
<summary>Commits</summary>

-  1.9.1
-  lint: apply standard 12 style
-  Fix using special characters in format
-  tests: use strict equality checks
-  build: use yaml eslint configuration
-  build: Node.js@9.11
-  build: Node.js@8.11
-  build: eslint-plugin-standard@3.1.0
-  build: eslint-plugin-promise@3.8.0
-  build: eslint-plugin-import@2.12.0
- Additional commits viewable in [compare view](https://github.com/expressjs/morgan/compare/1.7.0...1.9.1)
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=morgan&package-manager=npm_and_yarn&previous-version=1.7.0&new-version=1.9.1)](https://help.github.com/articles/configuring-automated-security-fixes)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c386e9607d73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.