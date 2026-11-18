# Issue

**Title:** Bump web-vitals from 3.0.3 to 3.0.4

## Description

Bumps [web-vitals](https://github.com/GoogleChrome/web-vitals) from 3.0.3 to 3.0.4.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/GoogleChrome/web-vitals/blob/main/CHANGELOG.md">web-vitals's changelog</a>.</em></p>
<blockquote>
<h3>v3.0.4 (2022-10-18)</h3>
<ul>
<li>Clamp LCP and FCP to 0 for prerendered pages (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/270">#270</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7f0ed0b</code></a> Release v3.0.4</li>
<li><a href=""><code>431eda6</code></a> Update CHANGELOG</li>
<li><a href=""><code>c41fed3</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/270">#270</a> from tunetheweb/prerender-LCP-FCP</li>
<li><a href=""><code>c334fb7</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/269">#269</a> from tunetheweb/fix-metric-specific-links</li>
<li><a href=""><code>24c309e</code></a> Clamp LCP and FCP to 0 for prerendered pages</li>
<li><a href=""><code>d63c605</code></a> Fix metrics-specific links</li>
<li>See full diff in <a href="https://github.com/GoogleChrome/web-vitals/compare/v3.0.3...v3.0.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=web-vitals&package-manager=npm_and_yarn&previous-version=3.0.3&new-version=3.0.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f82555fc1345`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.