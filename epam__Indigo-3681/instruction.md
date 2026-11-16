# Issue

**Title:** Bump qs and express in /utils/indigo-service/frontend/ui

## Description

Bumps [qs](https://github.com/ljharb/qs) and [express](https://github.com/expressjs/express). These dependencies needed to be updated together.
Updates `qs` from 6.14.2 to 6.15.2
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ljharb/qs/blob/main/CHANGELOG.md">qs's changelog</a>.</em></p>
<blockquote>
<h2><strong>6.15.2</strong></h2>
<ul>
<li>[Fix] <code>stringify</code>: skip null/undefined entries in <code>arrayFormat: 'comma'</code> + <code>encodeValuesOnly</code> instead of crashing in <code>encoder</code></li>
<li>[Fix] <code>stringify</code>: use configured <code>delimiter</code> after <code>charsetSentinel</code> (<a href="">#555</a>)</li>
<li>[Fix] <code>stringify</code>: apply <code>formatter</code> to encoded key under <code>strictNullHandling</code> (<a href="">#554</a>)</li>
<li>[Fix] <code>stringify</code>: skip null/undefined filter-array entries instead of crashing in <code>encoder</code> (<a href="">#551</a>)</li>
<li>[Fix] <code>parse</code>: handle nested bracket groups and add regression tests (<a href="">#530</a>)</li>
<li>[readme] fix grammar (<a href="">#550</a>)</li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code></li>
<li>[Tests] add regression tests for keys containing percent-encoded bracket text</li>
</ul>
<h2><strong>6.15.1</strong></h2>
<ul>
<li>[Fix] <code>parse</code>: <code>parameterLimit: Infinity</code> with <code>throwOnLimitExceeded: true</code> silently drops all parameters</li>
<li>[Deps] update <code>@ljharb/eslint-config</code></li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>iconv-lite</code></li>
<li>[Tests] increase coverage</li>
</ul>
<h2><strong>6.15.0</strong></h2>
<ul>
<li>[New] <code>parse</code>: add <code>strictMerge</code> option to wrap object/primitive conflicts in an array (<a href="">#425</a>, <a href="">#122</a>)</li>
<li>[Fix] <code>duplicates</code> option should not apply to bracket notation keys (<a href="">#514</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9aca407</code></a> v6.15.2</li>
<li><a href=""><code>5e33d33</code></a> [Dev Deps] update <code>@ljharb/eslint-config</code></li>
<li><a href=""><code>21f80b3</code></a> [Fix] <code>stringify</code>: skip null/undefined entries in <code>arrayFormat: 'comma'</code> + `e...</li>
<li><a href=""><code>a0a81ea</code></a> [Fix] <code>stringify</code>: use configured <code>delimiter</code> after <code>charsetSentinel</code></li>
<li><a href=""><code>e3062f7</code></a> [Fix] <code>stringify</code>: apply <code>formatter</code> to encoded key under <code>strictNullHandling</code></li>
<li><a href=""><code>0c180a4</code></a> [Fix] <code>stringify</code>: skip null/undefined filter-array entries instead of crashi...</li>
<li><a href=""><code>3a8b94a</code></a> [Tests] add regression tests for keys containing percent-encoded bracket text</li>
<li><a href=""><code>96755ab</code></a> [readme] fix grammar</li>
<li><a href=""><code>a419ce5</code></a> [Fix] <code>parse</code>: handle nested bracket groups and add regression tests</li>
<li><a href=""><code>3f5e1c5</code></a> v6.15.1</li>
<li>Additional commits viewable in <a href="https://github.com/ljharb/qs/compare/v6.14.2...v6.15.2">compare view</a></li>
</ul>
</details>
<br />

Updates `express` from 4.22.1 to 4.22.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/express/releases">express's releases</a>.</em></p>
<blockquote>
<h2>v4.22.2</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: restore &gt;20 array parsing for <code>req.query</code> repeated keys (<a href=""><code>8d09bfe6</code></a>)
<ul>
<li>This also unifies array-cap behavior across notations. Indexed notation (<code>a[0]=...</code>) was historically capped at qs's default <code>arrayLimit</code> of 20 even in older qs versions; after this change it also allows up to 1000 items.</li>
</ul>
</li>
<li>deps: qs@~6.15.1</li>
<li>deps: body-parser@~1.20.5</li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/suuuuuuminnnnnn"><code>@​suuuuuuminnnnnn</code></a> made their first contribution in <a href="">expressjs/express#7021</a></li>
<li><a href="https://github.com/SAY-5"><code>@​SAY-5</code></a> made their first contribution in <a href="">expressjs/express#7181</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/expressjs/express/compare/v4.22.1...v4.22.2">https://github.com/expressjs/express/compare/v4.22.1...v4.22.2</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/express/blob/v4.22.2/History.md">express's changelog</a>.</em></p>
<blockquote>
<h1>4.22.2 / 2026-05-011</h1>
<ul>
<li>fix: restore &gt;20 array parsing for <code>req.query</code> repeated keys (<a href=""><code>8d09bfe6</code></a>)
<ul>
<li>This also unifies array-cap behavior across notations. Indexed notation (<code>a[0]=...</code>) was historically capped at qs's default <code>arrayLimit</code> of 20 even in older qs versions; after this change it also allows up to 1000 items.</li>
</ul>
</li>
<li>deps: qs@~6.15.1</li>
<li>deps: body-parser@~1.20.5</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>df0abc9</code></a> 4.22.2</li>
<li><a href=""><code>836d366</code></a> <code>4.x</code> update qs to 6.15.1, body-parser 1.20.5 (<a href="">#7224</a>)</li>
<li><a href=""><code>8d09bfe</code></a> fix: restore array parsing for req.query repeated keys (<a href="">#7181</a>)</li>
<li><a href=""><code>d39e8ad</code></a> deps: body-parser@~1.20.4 (<a href="">#7021</a>)</li>
<li><a href=""><code>efe85d9</code></a> deps: qs@^6.14.1 (<a href="">#6972</a>)</li>
<li><a href=""><code>f62378e</code></a> 📝 add note to history</li>
<li>See full diff in <a href="https://github.com/expressjs/express/compare/v4.22.1...v4.22.2">compare view</a></li>
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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e34a69a5d1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.