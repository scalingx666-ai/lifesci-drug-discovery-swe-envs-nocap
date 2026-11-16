# Issue

**Title:** Bump web-vitals from 3.4.0 to 3.5.0

## Description

Bumps [web-vitals](https://github.com/GoogleChrome/web-vitals) from 3.4.0 to 3.5.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/GoogleChrome/web-vitals/blob/main/CHANGELOG.md">web-vitals's changelog</a>.</em></p>
<blockquote>
<h3>v3.5.0 (2023-09-28)</h3>
<ul>
<li>Run <code>onLCP</code> callback in separate task (<a href="">#386</a>)</li>
<li>Fix INP durationThreshold bug when set to 0 (<a href="">#372</a>)</li>
<li>Prevent FID entries being emitted as INP for non-supporting browsers (<a href="">#368</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dfdf57d</code></a> Release v3.5.0</li>
<li><a href=""><code>9cad8ee</code></a> Update CHANGELOG for 3.5.0 (<a href="">#387</a>)</li>
<li><a href=""><code>1cc298c</code></a> Run onLCP callback in own task (<a href="">#386</a>)</li>
<li><a href=""><code>1e94221</code></a> Bump nunjucks from 3.2.3 to 3.2.4 (<a href="">#385</a>)</li>
<li><a href=""><code>8fcf698</code></a> Upgrade selenium and webdriver (<a href="">#384</a>)</li>
<li><a href=""><code>4b769ff</code></a> Fix INP <code>durationThreshold</code> bug when set to 0 (<a href="">#372</a>)</li>
<li><a href=""><code>27db8a0</code></a> Readme fixes for INP (<a href="">#379</a>)</li>
<li><a href=""><code>a948d3c</code></a> Remove reference to Universal Analytics from README (<a href="">#371</a>)</li>
<li><a href=""><code>3806160</code></a> Prevent FID entries being emitted as INP for non-supporting browsers (<a href="">#368</a>)</li>
<li>See full diff in <a href="https://github.com/GoogleChrome/web-vitals/compare/v3.4.0...v3.5.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=web-vitals&package-manager=npm_and_yarn&previous-version=3.4.0&new-version=3.5.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `658438fb661d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.