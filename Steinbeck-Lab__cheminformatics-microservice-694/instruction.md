# Issue

**Title:** chore(deps): bump qs and express in /frontend

## Description

Bumps [qs](https://github.com/ljharb/qs) and [express](https://github.com/expressjs/express). These dependencies needed to be updated together.
Updates `qs` from 6.13.0 to 6.14.1
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ljharb/qs/blob/main/CHANGELOG.md">qs's changelog</a>.</em></p>
<blockquote>
<h2><strong>6.14.1</strong></h2>
<ul>
<li>[Fix] ensure arrayLength applies to <code>[]</code> notation as well</li>
<li>[Fix] <code>parse</code>: when a custom decoder returns <code>null</code> for a key, ignore that key</li>
<li>[Refactor] <code>parse</code>: extract key segment splitting helper</li>
<li>[meta] add threat model</li>
<li>[actions] add workflow permissions</li>
<li>[Tests] <code>stringify</code>: increase coverage</li>
<li>[Dev Deps] update <code>eslint</code>, <code>@ljharb/eslint-config</code>, <code>npmignore</code>, <code>es-value-fixtures</code>, <code>for-each</code>, <code>object-inspect</code></li>
</ul>
<h2><strong>6.14.0</strong></h2>
<ul>
<li>[New] <code>parse</code>: add <code>throwOnParameterLimitExceeded</code> option (<a href="">#517</a>)</li>
<li>[Refactor] <code>parse</code>: use <code>utils.combine</code> more</li>
<li>[patch] <code>parse</code>: add explicit <code>throwOnLimitExceeded</code> default</li>
<li>[actions] use shared action; re-add finishers</li>
<li>[meta] Fix changelog formatting bug</li>
<li>[Deps] update <code>side-channel</code></li>
<li>[Dev Deps] update <code>es-value-fixtures</code>, <code>has-bigints</code>, <code>has-proto</code>, <code>has-symbols</code></li>
<li>[Tests] increase coverage</li>
</ul>
<h2><strong>6.13.1</strong></h2>
<ul>
<li>[Fix] <code>stringify</code>: avoid a crash when a <code>filter</code> key is <code>null</code></li>
<li>[Fix] <code>utils.merge</code>: functions should not be stringified into keys</li>
<li>[Fix] <code>parse</code>: avoid a crash with interpretNumericEntities: true, comma: true, and iso charset</li>
<li>[Fix] <code>stringify</code>: ensure a non-string <code>filter</code> does not crash</li>
<li>[Refactor] use <code>__proto__</code> syntax instead of <code>Object.create</code> for null objects</li>
<li>[Refactor] misc cleanup</li>
<li>[Tests] <code>utils.merge</code>: add some coverage</li>
<li>[Tests] fix a test case</li>
<li>[actions] split out node 10-20, and 20+</li>
<li>[Dev Deps] update <code>es-value-fixtures</code>, <code>mock-property</code>, <code>object-inspect</code>, <code>tape</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3fa11a5</code></a> v6.14.1</li>
<li><a href=""><code>a626704</code></a> [Dev Deps] update <code>npmignore</code></li>
<li><a href=""><code>3086902</code></a> [Fix] ensure arrayLength applies to <code>[]</code> notation as well</li>
<li><a href=""><code>fc7930e</code></a> [Dev Deps] update <code>eslint</code>, <code>@ljharb/eslint-config</code></li>
<li><a href=""><code>0b06aac</code></a> [Dev Deps] update <code>@ljharb/eslint-config</code></li>
<li><a href=""><code>64951f6</code></a> [Refactor] <code>parse</code>: extract key segment splitting helper</li>
<li><a href=""><code>e1bd259</code></a> [Dev Deps] update <code>@ljharb/eslint-config</code></li>
<li><a href=""><code>f4b3d39</code></a> [eslint] add eslint 9 optional peer dep</li>
<li><a href=""><code>6e94d95</code></a> [Dev Deps] update <code>eslint</code>, <code>@ljharb/eslint-config</code>, <code>npmignore</code></li>
<li><a href=""><code>973dc3c</code></a> [actions] add workflow permissions</li>
<li>Additional commits viewable in <a href="https://github.com/ljharb/qs/compare/v6.13.0...v6.14.1">compare view</a></li>
</ul>
</details>
<br />

Updates `express` from 4.21.2 to 4.22.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/express/releases">express's releases</a>.</em></p>
<blockquote>
<h2>v4.22.1</h2>
<h2>What's Changed</h2>
<blockquote>
<p>[!IMPORTANT]<br />
The prior release (4.22.0) included an erroneous breaking change related to the extended query parser. There is no actual security vulnerability associated with this behavior (CVE-2024-51999 has been rejected). The change has been fully reverted in this release.</p>
</blockquote>
<ul>
<li>Release: 4.22.1 by <a href="https://github.com/UlisesGascon"><code>@​UlisesGascon</code></a> in <a href="">expressjs/express#6934</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/expressjs/express/compare/4.22.0...v4.22.1">https://github.com/expressjs/express/compare/4.22.0...v4.22.1</a></p>
<h2>4.22.0</h2>
<h2>Important: Security</h2>
<ul>
<li>Security fix for <a href="https://www.cve.org/CVERecord?id=CVE-2024-51999">CVE-2024-51999</a> (<a href="https://github.com/expressjs/express/security/advisories/GHSA-pj86-cfqh-vqx6">GHSA-pj86-cfqh-vqx6</a>)</li>
</ul>
<h2>What's Changed</h2>
<ul>
<li>Refactor: improve readability by <a href="https://github.com/sazk07"><code>@​sazk07</code></a> in <a href="">expressjs/express#6190</a></li>
<li>ci: add support for Node.js@23.0 by <a href="https://github.com/UlisesGascon"><code>@​UlisesGascon</code></a> in <a href="">expressjs/express#6080</a></li>
<li>Method functions with no path should error by <a href="https://github.com/wesleytodd"><code>@​wesleytodd</code></a> in <a href="">expressjs/express#5957</a></li>
<li>ci: updated github actions ci workflow by <a href="https://github.com/Phillip9587"><code>@​Phillip9587</code></a> in <a href="">expressjs/express#6323</a></li>
<li>ci: reorder <code>npm i</code> steps to fix ci for older node versions by <a href="https://github.com/Phillip9587"><code>@​Phillip9587</code></a> in <a href="">expressjs/express#6336</a></li>
<li>Backport: ci: add node.js 24 to test matrix by <a href="https://github.com/Phillip9587"><code>@​Phillip9587</code></a> in <a href="">expressjs/express#6506</a></li>
<li>chore(4.x): wider range for query test skip by <a href="https://github.com/jonchurch"><code>@​jonchurch</code></a> in <a href="">expressjs/express#6513</a></li>
<li>use tilde notation for certain dependencies by <a href="https://github.com/UlisesGascon"><code>@​UlisesGascon</code></a> in <a href="">expressjs/express#6905</a></li>
<li>deps: qs@6.14.0 by <a href="https://github.com/UlisesGascon"><code>@​UlisesGascon</code></a> in <a href="">expressjs/express#6909</a></li>
<li>deps: use tilde notation for <code>qs</code> by <a href="https://github.com/Phillip9587"><code>@​Phillip9587</code></a> in <a href="">expressjs/express#6919</a></li>
<li>Release: 4.22.0 by <a href="https://github.com/UlisesGascon"><code>@​UlisesGascon</code></a> in <a href="">expressjs/express#6921</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/expressjs/express/compare/4.21.2...4.22.0">https://github.com/expressjs/express/compare/4.21.2...4.22.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/express/blob/v4.22.1/History.md">express's changelog</a>.</em></p>
<blockquote>
<h1>4.22.1 / 2025-12-01</h1>
<ul>
<li>Revert security fix for <a href="https://www.cve.org/CVERecord?id=CVE-2024-51999">CVE-2024-51999</a> (<a href="https://github.com/expressjs/express/security/advisories/GHSA-pj86-cfqh-vqx6">GHSA-pj86-cfqh-vqx6</a>)</li>
</ul>
<h1>4.22.0 / 2025-12-01</h1>
<ul>
<li>Security fix for <a href="https://www.cve.org/CVERecord?id=CVE-2024-51999">CVE-2024-51999</a> (<a href="https://github.com/expressjs/express/security/advisories/GHSA-pj86-cfqh-vqx6">GHSA-pj86-cfqh-vqx6</a>)</li>
<li>deps: use tilde notation for dependencies</li>
<li>deps: qs@6.14.0</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>12fae14</code></a> 4.22.1</li>
<li><a href=""><code>5ddf311</code></a> Revert &quot;sec: security patch for CVE-2024-51999&quot;</li>
<li><a href=""><code>49744ab</code></a> 4.22.0 (<a href="">#6921</a>)</li>
<li><a href=""><code>6e97452</code></a> sec: security patch for CVE-2024-51999</li>
<li><a href=""><code>6a23d34</code></a> deps: use tilde notation for <code>qs</code> (<a href="">#6919</a>)</li>
<li><a href=""><code>8c12cdf</code></a> deps: qs@6.14.0 (<a href="">#6909</a>)</li>
<li><a href=""><code>7fea74f</code></a> deps: use tilde notation for certain dependencies (<a href="">#6905</a>)</li>
<li><a href=""><code>dac7a04</code></a> chore: wider range for query test skip (<a href="">#6513</a>)</li>
<li><a href=""><code>997919b</code></a> ci: add node.js 24 to test matrix (<a href="">#6506</a>)</li>
<li><a href=""><code>36fb59c</code></a> fix(ci): reorder <code>npm i</code> steps to fix ci for older node versions (<a href="">#6336</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/expressjs/express/compare/4.21.2...v4.22.1">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d90c4f1fdb7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.