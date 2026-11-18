# Issue

**Title:** Bump junit from 4.12 to 4.13.1 in /exec

## Description

Bumps [junit](https://github.com/junit-team/junit4) from 4.12 to 4.13.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/junit-team/junit4/releases">junit's releases</a>.</em></p>
<blockquote>
<h2>JUnit 4.13.1</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit/blob/HEAD/doc/ReleaseNotes4.13.1.md">release notes</a> for details.</p>
<h2>JUnit 4.13</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit/blob/HEAD/doc/ReleaseNotes4.13.md">release notes</a> for details.</p>
<h2>JUnit 4.13 RC 2</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit4/wiki/4.13-Release-Notes">release notes</a> for details.</p>
<h2>JUnit 4.13 RC 1</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit4/wiki/4.13-Release-Notes">release notes</a> for details.</p>
<h2>JUnit 4.13 Beta 3</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit4/wiki/4.13-Release-Notes">release notes</a> for details.</p>
<h2>JUnit 4.13 Beta 2</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit4/wiki/4.13-Release-Notes">release notes</a> for details.</p>
<h2>JUnit 4.13 Beta 1</h2>
<p>Please refer to the <a href="https://github.com/junit-team/junit4/wiki/4.13-Release-Notes">release notes</a> for details.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1b683f4</code></a> [maven-release-plugin] prepare release r4.13.1</li>
<li><a href=""><code>ce6ce3a</code></a> Draft 4.13.1 release notes</li>
<li><a href=""><code>c29dd82</code></a> Change version to 4.13.1-SNAPSHOT</li>
<li><a href=""><code>1d17486</code></a> Add a link to assertThrows in exception testing</li>
<li><a href=""><code>543905d</code></a> Use separate line for annotation in Javadoc</li>
<li><a href=""><code>510e906</code></a> Add sub headlines to class Javadoc</li>
<li><a href=""><code>610155b</code></a> Merge pull request from GHSA-269g-pwp5-87pp</li>
<li><a href=""><code>b6cfd1e</code></a> Explicitly wrap float parameter for consistency (<a href="https://github-redirect.dependabot.com/junit-team/junit4/issues/1671">#1671</a>)</li>
<li><a href=""><code>a5d205c</code></a> Fix GitHub link in FAQ (<a href="https://github-redirect.dependabot.com/junit-team/junit4/issues/1672">#1672</a>)</li>
<li><a href=""><code>3a5c6b4</code></a> Deprecated since jdk9 replacing constructor instance of Double and Float (<a href="https://github-redirect.dependabot.com/junit-team/junit4/issues/1660">#1660</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/junit-team/junit4/compare/r4.12...r4.13.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=junit:junit&package-manager=maven&previous-version=4.12&new-version=4.13.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/configuring-github-dependabot-security-updates)

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
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/asad/SMSD/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da39ddb67237`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.