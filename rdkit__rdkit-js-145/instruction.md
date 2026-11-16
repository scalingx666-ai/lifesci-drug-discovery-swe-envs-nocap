# Issue

**Title:** Bump @testing-library/user-event from 14.2.5 to 14.2.6

## Description

Bumps [@testing-library/user-event](https://github.com/testing-library/user-event) from 14.2.5 to 14.2.6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/testing-library/user-event/releases"><code>@​testing-library/user-event</code>'s releases</a>.</em></p>
<blockquote>
<h2>v14.2.6</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.2.5...v14.2.6">14.2.6</a> (2022-07-18)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>document:</strong> reduce impact of React@17 workaround (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/992">#992</a>) (<a href="">9816d38</a>)</li>
<li><strong>pointer:</strong> do not throw for <code>pointer-events: none</code> on previous target (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/991">#991</a>) (<a href="">6e4058b</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6e4058b</code></a> fix(pointer): do not throw for <code>pointer-events: none</code> on previous target (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/991">#991</a>)</li>
<li><a href=""><code>9816d38</code></a> fix(document): reduce impact of React@17 workaround (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/992">#992</a>)</li>
<li>See full diff in <a href="https://github.com/testing-library/user-event/compare/v14.2.5...v14.2.6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@testing-library/user-event&package-manager=npm_and_yarn&previous-version=14.2.5&new-version=14.2.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `269c23c7d309`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.