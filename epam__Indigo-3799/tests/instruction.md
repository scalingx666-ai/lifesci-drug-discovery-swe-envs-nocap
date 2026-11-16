# Issue

**Title:** Bump body-parser from 1.20.5 to 1.20.6 in /utils/indigo-service/frontend/ui

## Description

Bumps [body-parser](https://github.com/expressjs/body-parser) from 1.20.5 to 1.20.6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/body-parser/releases">body-parser's releases</a>.</em></p>
<blockquote>
<h2>1.20.6</h2>
<h2>Important: Security</h2>
<ul>
<li>Security fix for <a href="https://www.cve.org/CVERecord?id=CVE-2025-13466">CVE-2026-12590</a> (<a href="https://github.com/expressjs/body-parser/security/advisories/GHSA-v422-hmwv-36x6">GHSA-v422-hmwv-36x6</a>)</li>
</ul>
<h2>What's Changed</h2>
<ul>
<li>fix: improve limit option validation by <a href="https://github.com/Phillip9587"><code>@​Phillip9587</code></a> in <a href="">expressjs/body-parser#741</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/expressjs/body-parser/compare/1.20.5...1.20.6">https://github.com/expressjs/body-parser/compare/1.20.5...1.20.6</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/body-parser/blob/master/HISTORY.md">body-parser's changelog</a>.</em></p>
<blockquote>
<h1>1.20.6 / 2026-07-09</h1>
<ul>
<li>Security fix for <a href="https://github.com/expressjs/body-parser/security/advisories/GHSA-v422-hmwv-36x6">GHSA-v422-hmwv-36x6</a></li>
<li>fix: improve <code>limit</code> option validation (<a href="">#698</a>)
<ul>
<li>Invalid <code>limit</code> values (e.g. unparseable strings or <code>NaN</code>) now throw instead of being silently ignored, which previously disabled size limit enforcement</li>
<li><code>null</code> and <code>undefined</code> fall back to the default 100kb limit</li>
</ul>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5cc4fb8</code></a> 1.20.6 (<a href="">#746</a>)</li>
<li><a href=""><code>3492672</code></a> fix: improve limit option validation (<a href="">#741</a>)</li>
<li>See full diff in <a href="https://github.com/expressjs/body-parser/compare/1.20.5...1.20.6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=body-parser&package-manager=npm_and_yarn&previous-version=1.20.5&new-version=1.20.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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