# Issue

**Title:** Bump zone.js from 0.11.8 to 0.12.0

## Description

Bumps [zone.js](https://github.com/angular/angular/tree/HEAD/packages/zone.js) from 0.11.8 to 0.12.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/angular/angular/blob/main/packages/zone.js/CHANGELOG.md">zone.js's changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/angular/angular/compare/zone.js-0.11.8...zone.js-0.12.0">0.12.0</a> (2022-10-27)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>zone.js:</strong> cancel tasks only when they are scheduled or running (<a href="https://github-redirect.dependabot.com/angular/angular/issues/46435">#46435</a>) (<a href="">b618b5a</a>), closes <a href="https://github-redirect.dependabot.com/angular/angular/issues/45711">#45711</a></li>
<li><strong>zone.js:</strong> Fix ConsoleTask interface typo (<a href="https://github-redirect.dependabot.com/angular/angular/issues/47090">#47090</a>) (<a href="">91954cf</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>24c93bb</code></a> release: cut the zone.js-0.12.0 release (<a href="">#47895</a>)</li>
<li><a href=""><code>b618b5a</code></a> fix(zone.js): cancel tasks only when they are scheduled or running (<a href="">#46435</a>)</li>
<li><a href=""><code>370aa34</code></a> build: update dependency google-closure-compiler to v20221004 (<a href="">#47696</a>)</li>
<li><a href=""><code>b2aa9ce</code></a> build: update puppeteer to 18.0.5 (<a href="">#47584</a>)</li>
<li><a href=""><code>8637253</code></a> refactor(zone.js): remove zone-async-tagging from zone.js (<a href="">#47416</a>)</li>
<li><a href=""><code>59aa2c0</code></a> test(zone.js): update jest test code after upgrade to jest 29.0 (<a href="">#47486</a>)</li>
<li><a href=""><code>c9991ca</code></a> build: update dependency google-closure-compiler to v20220905 (<a href="">#47437</a>)</li>
<li><a href=""><code>7d3df47</code></a> build: update to TypeScript 4.8 final (<a href="">#47270</a>)</li>
<li><a href=""><code>31429ea</code></a> feat(core): support TypeScript 4.8 (<a href="">#47038</a>)</li>
<li><a href=""><code>91954cf</code></a> fix(zone.js): Fix ConsoleTask interface typo (<a href="">#47090</a>)</li>
<li>See full diff in <a href="https://github.com/angular/angular/commits/zone.js-0.12.0/packages/zone.js">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=zone.js&package-manager=npm_and_yarn&previous-version=0.11.8&new-version=0.12.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f7c402ffea6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.