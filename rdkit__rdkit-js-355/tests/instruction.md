# Issue

**Title:** Bump tough-cookie from 4.1.2 to 4.1.3

## Description

Bumps [tough-cookie](https://github.com/salesforce/tough-cookie) from 4.1.2 to 4.1.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/salesforce/tough-cookie/releases">tough-cookie's releases</a>.</em></p>
<blockquote>
<h2>4.1.3</h2>
<p>Security fix for Prototype Pollution discovery in <a href="">#282</a>. This is a minor release, although output from the <code>inspect</code> utility is affected by this change, we felt this change was important enough to be pushed into the next patch.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4ff4d29</code></a> 4.1.3 release preparation, update the package and lib/version to 4.1.3. (<a href="">#284</a>)</li>
<li><a href=""><code>12d4747</code></a> Prevent prototype pollution in cookie memstore (<a href="">#283</a>)</li>
<li><a href=""><code>f06b72d</code></a> Fix documentation for store.findCookies, missing allowSpecialUseDomain proper...</li>
<li>See full diff in <a href="https://github.com/salesforce/tough-cookie/compare/v4.1.2...v4.1.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=tough-cookie&package-manager=npm_and_yarn&previous-version=4.1.2&new-version=4.1.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/rdkit/rdkit-js/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ecfa8dfd081`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.