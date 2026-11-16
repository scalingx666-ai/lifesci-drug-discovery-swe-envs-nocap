# Issue

**Title:** Bump decode-uri-component and @testing-library/jest-dom in /utils/indigo-service/frontend/ui

## Description

Removes [decode-uri-component](https://github.com/SamVerschueren/decode-uri-component). It's no longer used after updating ancestor dependency [@testing-library/jest-dom](https://github.com/testing-library/jest-dom). These dependencies need to be updated together.

Removes `decode-uri-component`

Updates `@testing-library/jest-dom` from 4.2.4 to 7.0.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/testing-library/jest-dom/releases">@​testing-library/jest-dom's releases</a>.</em></p>
<blockquote>
<h2>v7.0.1</h2>
<h2><a href="https://github.com/testing-library/jest-dom/compare/v7.0.0...v7.0.1">7.0.1</a> (2026-08-09)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>declare vitest as an optional peer dependency (<a href="">#733</a>) (<a href="">3782c78</a>)</li>
</ul>
<h2>v7.0.0</h2>
<h1><a href="https://github.com/testing-library/jest-dom/compare/v6.10.0...v7.0.0">7.0.0</a> (2026-07-20)</h1>
<h3>Features</h3>
<ul>
<li>add toContainAnyBy* and toContainOneBy* query matchers (<a href="">1e39089</a>)</li>
</ul>
<h3>BREAKING CHANGES</h3>
<ul>
<li><code>@​testing-library/dom</code> is now a required peer dependency. The minimum supported
Node.js version is now 22.</li>
</ul>
<p>Repaired release for <a href="">testing-library/jest-dom#731</a></p>
<h2>v6.10.0</h2>
<h1><a href="https://github.com/testing-library/jest-dom/compare/v6.9.1...v6.10.0">6.10.0</a> (2026-07-20)</h1>
<h3>Features</h3>
<ul>
<li>add toContainAnyBy* and toContainOneBy* query matchers (<a href="">#731</a>) (<a href="">cae44df</a>)</li>
</ul>
<h2>v6.9.1</h2>
<h2><a href="https://github.com/testing-library/jest-dom/compare/v6.9.0...v6.9.1">6.9.1</a> (2025-10-01)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Fix undefined <code>Node</code> error (nodejs) (<a href="">#707</a>) (<a href="">0ff8904</a>)</li>
</ul>
<h2>v6.9.0</h2>
<h1><a href="https://github.com/testing-library/jest-dom/compare/v6.8.0...v6.9.0">6.9.0</a> (2025-09-30)</h1>
<h3>Features</h3>
<ul>
<li>Add .toAppearBefore/.toAppearAfter matcher (<a href="">#702</a>) (<a href="">95f870a</a>)</li>
</ul>
<h2>v6.8.0</h2>
<h1><a href="https://github.com/testing-library/jest-dom/compare/v6.7.0...v6.8.0">6.8.0</a> (2025-08-20)</h1>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3782c78</code></a> fix: declare vitest as an optional peer dependency (<a href="">#733</a>)</li>
<li><a href=""><code>1e39089</code></a> feat: add toContainAnyBy* and toContainOneBy* query matchers</li>
<li><a href=""><code>cae44df</code></a> feat: add toContainAnyBy* and toContainOneBy* query matchers (<a href="">#731</a>)</li>
<li><a href=""><code>55c07ce</code></a> ci: switch release to npm trusted publishing (<a href="">#726</a>)</li>
<li><a href=""><code>213256f</code></a> docs: move toHaveSelection from the deprecated section (<a href="">#717</a>)</li>
<li><a href=""><code>0ff8904</code></a> fix: Fix undefined <code>Node</code> error (nodejs) (<a href="">#707</a>)</li>
<li><a href=""><code>95f870a</code></a> feat: Add .toAppearBefore/.toAppearAfter matcher (<a href="">#702</a>)</li>
<li><a href=""><code>d6663f5</code></a> docs: add nossbigg as a contributor for code, and test (<a href="">#703</a>)</li>
<li><a href=""><code>779b712</code></a> feat: add toBePartiallyPressed matcher (<a href="">#203</a>) (<a href="">#692</a>)</li>
<li><a href=""><code>e15f789</code></a> docs: add kretajak as a contributor for code, and test (<a href="">#691</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/testing-library/jest-dom/compare/v4.2.4...v7.0.1">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for <code>@​testing-library/jest-dom</code> since your current version.</p>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93b041db7d94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.