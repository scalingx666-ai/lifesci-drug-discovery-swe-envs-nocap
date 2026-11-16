# Issue

**Title:** Bump path-to-regexp and express in /utils/indigo-service/frontend/ui

## Description

Bumps [path-to-regexp](https://github.com/pillarjs/path-to-regexp) and [express](https://github.com/expressjs/express). These dependencies needed to be updated together.
Updates `path-to-regexp` from 0.1.12 to 3.3.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pillarjs/path-to-regexp/releases">path-to-regexp's releases</a>.</em></p>
<blockquote>
<h2>0.1.13</h2>
<h2>Important</h2>
<ul>
<li>Fix <a href="https://www.cve.org/CVERecord?id=CVE-2026-4867">CVE-2026-4867</a> (<a href="https://github.com/pillarjs/path-to-regexp/security/advisories/GHSA-37ch-88jc-xwx2">GHSA-37ch-88jc-xwx2</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/pillarjs/path-to-regexp/compare/v0.1.12...v.0.1.13">https://github.com/pillarjs/path-to-regexp/compare/v0.1.12...v.0.1.13</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pillarjs/path-to-regexp/blob/master/History.md">path-to-regexp's changelog</a>.</em></p>
<blockquote>
<h1>Moved to <a href="https://github.com/pillarjs/path-to-regexp/releases">GitHub Releases</a></h1>
<h2>3.0.0 / 2019-01-13</h2>
<ul>
<li>Always use prefix character as delimiter token, allowing any character to be a delimiter (e.g. <code>/:att1-:att2-:att3-:att4-:att5</code>)</li>
<li>Remove <code>partial</code> support, prefer escaping the prefix delimiter explicitly (e.g. <code>\\/(apple-)?icon-:res(\\d+).png</code>)</li>
</ul>
<h2>2.4.0 / 2018-08-26</h2>
<ul>
<li>Support <code>start</code> option to disable anchoring from beginning of the string</li>
</ul>
<h2>2.3.0 / 2018-08-20</h2>
<ul>
<li>Use <code>delimiter</code> when processing repeated matching groups (e.g. <code>foo/bar</code> has no prefix, but has a delimiter)</li>
</ul>
<h2>2.2.1 / 2018-04-24</h2>
<ul>
<li>Allow empty string with <code>end: false</code> to match both relative and absolute paths</li>
</ul>
<h2>2.2.0 / 2018-03-06</h2>
<ul>
<li>Pass <code>token</code> as second argument to <code>encode</code> option (e.g. <code>encode(value, token)</code>)</li>
</ul>
<h2>2.1.0 / 2017-10-20</h2>
<ul>
<li>Handle non-ending paths where the final character is a delimiter
<ul>
<li>E.g. <code>/foo/</code> before required either <code>/foo/</code> or <code>/foo//</code> to match in non-ending mode</li>
</ul>
</li>
</ul>
<h2>2.0.0 / 2017-08-23</h2>
<ul>
<li>New option! Ability to set <code>endsWith</code> to match paths like <code>/test?query=string</code> up to the query string</li>
<li>New option! Set <code>delimiters</code> for specific characters to be treated as parameter prefixes (e.g. <code>/:test</code>)</li>
<li>Remove <code>isarray</code> dependency</li>
<li>Explicitly handle trailing delimiters instead of trimming them (e.g. <code>/test/</code> is now treated as <code>/test/</code> instead of <code>/test</code> when matching)</li>
<li>Remove overloaded <code>keys</code> argument that accepted <code>options</code></li>
<li>Remove <code>keys</code> list attached to the <code>RegExp</code> output</li>
<li>Remove asterisk functionality (it's a real pain to properly encode)</li>
<li>Change <code>tokensToFunction</code> (e.g. <code>compile</code>) to accept an <code>encode</code> function for pretty encoding (e.g. pass your own implementation)</li>
</ul>
<h2>1.7.0 / 2016-11-08</h2>
<ul>
<li>Allow a <code>delimiter</code> option to be passed in with <code>tokensToRegExp</code> which will be used for &quot;non-ending&quot; token match situations</li>
</ul>
<h2>1.6.0 / 2016-10-03</h2>
<ul>
<li>Populate <code>RegExp.keys</code> when using the <code>tokensToRegExp</code> method (making it consistent with the main export)</li>
<li>Allow a <code>delimiter</code> option to be passed in with <code>parse</code></li>
<li>Updated TypeScript definition with <code>Keys</code> and <code>Options</code> updated</li>
</ul>
<h2>1.5.3 / 2016-06-15</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2eb1293</code></a> 3.3.0</li>
<li><a href=""><code>d31670a</code></a> Add backtrack protection to 3.x release (<a href="">#321</a>)</li>
<li><a href=""><code>6d2e8db</code></a> 3.2.0</li>
<li><a href=""><code>0e0dce9</code></a> Add native <code>match</code> function to library</li>
<li><a href=""><code>dd966ea</code></a> Fix <code>validate: false</code> examples in README</li>
<li><a href=""><code>ead0298</code></a> Changed coverage tool to nyc (<a href="">#201</a>)</li>
<li><a href=""><code>1aa2238</code></a> Bump node version tests</li>
<li><a href=""><code>f232e6d</code></a> 3.1.0</li>
<li><a href=""><code>cb331c6</code></a> Update dev dependencies</li>
<li><a href=""><code>36344dc</code></a> Rename <code>noValidate</code> option to <code>validate</code></li>
<li>Additional commits viewable in <a href="https://github.com/pillarjs/path-to-regexp/compare/v0.1.12...v3.3.0">compare view</a></li>
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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d351e2af5cfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.