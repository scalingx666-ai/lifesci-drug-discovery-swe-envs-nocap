# Issue

**Title:** Bump shell-quote from 1.8.1 to 1.10.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [shell-quote](https://github.com/ljharb/shell-quote) from 1.8.1 to 1.10.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ljharb/shell-quote/blob/main/CHANGELOG.md">shell-quote's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.9.0...v1.10.0">v1.10.0</a> - 2026-07-10</h2>
<h3>Merged</h3>
<ul>
<li>[New] <code>parse</code>: add opt-in <code>splitUnquoted</code> option for shell field-splitting of unquoted expansions <a href=""><code></code></a></li>
</ul>
<h3>Commits</h3>
<ul>
<li>[Fix] <code>parse</code>: match nested <code>${...}</code> braces so nested parameter expansion is consumed as one substitution <a href=""><code>c0842c8</code></a></li>
<li>[Tests] <code>parse</code>: pin single-quote literalness and unmatched-quote handling <a href=""><code>a0d03e3</code></a></li>
<li>[readme] remove the space in js code fences so evalmd evaluates them <a href=""><code>2116fa3</code></a></li>
<li>[Tests] <code>quote</code>: pin conservative escaping of <code>=</code>, <code>@</code>, <code>^</code>, <code>,</code>, <code>:</code>, <code>!</code> (<a href="">#11</a>) <a href=""><code>1c36f3f</code></a></li>
<li>[readme] document that <code>quote</code> outputs POSIX quoting, not <code>cmd.exe</code>/PowerShell <a href=""><code>100e96e</code></a></li>
<li>[readme] document <code>parse</code>'s supported parameter-expansion subset <a href=""><code>e1c75cd</code></a></li>
<li>[Fix] <code>parse</code>: a backslash inside single quotes must not escape the closing quote <a href=""><code>5d460a3</code></a></li>
<li>[readme] fix stale example outputs <a href=""><code>2de86f5</code></a></li>
<li>[Tests] <code>quote</code>: pin that a backslash with whitespace is not doubled in single quotes (<a href="">#14</a>) <a href=""><code>190e236</code></a></li>
<li>[readme] <code>quote</code>: use output verbatim; do not re-quote it (<a href="">#11</a>) <a href=""><code>1b36468</code></a></li>
<li>[Refactor] <code>parse</code>: fix swapped <code>SINGLE_QUOTE</code>/<code>DOUBLE_QUOTE</code> variable names <a href=""><code>801af5c</code></a></li>
<li>[types] fix an error TS v6 ignores but v7 fails on <a href=""><code>59bbf8b</code></a></li>
<li>[Dev Deps] update <code>@arethetypeswrong/cli</code>, <code>evalmd</code> <a href=""><code>a04d475</code></a></li>
<li>[Dev Deps] update <code>@arethetypeswrong/ci</code>, <code>eslint</code> <a href=""><code>d390f9a</code></a></li>
<li>[Tests] <code>quote</code>: the tilde test escapes every <code>~</code>, not just a leading one (<a href="">#9</a>) <a href=""><code>617d119</code></a></li>
</ul>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.8.4...v1.9.0">v1.9.0</a> - 2026-06-24</h2>
<h3>Commits</h3>
<ul>
<li>[New] add types <a href=""><code>dca6e21</code></a></li>
<li>[Dev Deps] update <code>eslint</code> <a href=""><code>9aa9e8f</code></a></li>
<li>[Fix] <code>parse</code>: finalize tokens in linear time (GHSA-395f-4hp3-45gv) <a href=""><code>7ff5488</code></a></li>
<li>[actions] update workflows <a href=""><code>75e8497</code></a></li>
<li>[actions] Windows + node 4/6/7: pin eslint to 9 before install, since npm 2/3 cannot stage eslint 10<code>@types/esrecurse</code> <a href=""><code>3fb739d</code></a></li>
<li>[actions] retry <code>npm install</code> on Windows to survive npm 2/3 staging-rename flake <a href=""><code>abe0163</code></a></li>
<li>[actions] Windows + node 5/7: install deps with a modern node <a href=""><code>b4bafa2</code></a></li>
<li>[Fix] <code>quote</code>: escape leading <code>~</code> to prevent shell tilde-expansion <a href=""><code>7a76c1a</code></a></li>
<li>[Dev Deps] update <code>auto-changelog</code>, <code>tape</code> <a href=""><code>7184b44</code></a></li>
<li>[Dev Deps] apparently <code>jackspeak</code> is no longer in the graph <a href=""><code>9ba368a</code></a></li>
</ul>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.8.3...v1.8.4">v1.8.4</a> - 2026-05-22</h2>
<h3>Commits</h3>
<ul>
<li>[Fix] <code>quote</code>: validate object-token shapes <a href=""><code>4378a6e</code></a></li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>auto-changelog</code>, <code>eslint</code>, <code>npmignore</code> <a href=""><code>22ebec0</code></a></li>
<li>[Tests] increase coverage <a href=""><code>9f3caa3</code></a></li>
<li>[readme] replace runkit CI badge with shields.io check-runs badge <a href=""><code>3344a04</code></a></li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code> <a href=""><code>699c511</code></a></li>
</ul>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.8.2...v1.8.3">v1.8.3</a> - 2025-06-01</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>64988d9</code></a> v1.10.0</li>
<li><a href=""><code>617d119</code></a> [Tests] <code>quote</code>: the tilde test escapes every <code>~</code>, not just a leading one (<a href="">#9</a>)</li>
<li><a href=""><code>59bbf8b</code></a> [types] fix an error TS v6 ignores but v7 fails on</li>
<li><a href=""><code>190e236</code></a> [Tests] <code>quote</code>: pin that a backslash with whitespace is not doubled in singl...</li>
<li><a href=""><code>a04d475</code></a> [Dev Deps] update <code>@arethetypeswrong/cli</code>, <code>evalmd</code></li>
<li><a href=""><code>b9545b3</code></a> [New] <code>parse</code>: add opt-in <code>splitUnquoted</code> option for shell field-splitting of...</li>
<li><a href=""><code>1b36468</code></a> [readme] <code>quote</code>: use output verbatim; do not re-quote it (<a href="">#11</a>)</li>
<li><a href=""><code>1c36f3f</code></a> [Tests] <code>quote</code>: pin conservative escaping of <code>=</code>, <code>@</code>, <code>^</code>, <code>,</code>, <code>:</code>, <code>!</code> (<a href="">#11</a>)</li>
<li><a href=""><code>e1c75cd</code></a> [readme] document <code>parse</code>'s supported parameter-expansion subset</li>
<li><a href=""><code>c0842c8</code></a> [Fix] <code>parse</code>: match nested <code>${...}</code> braces so nested parameter expansion is ...</li>
<li>Additional commits viewable in <a href="https://github.com/ljharb/shell-quote/compare/v1.8.1...v1.10.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=shell-quote&package-manager=npm_and_yarn&previous-version=1.8.1&new-version=1.10.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3f2f30fb3bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.