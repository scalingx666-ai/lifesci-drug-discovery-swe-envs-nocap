# Issue

**Title:** Bump @testing-library/user-event from 14.1.1 to 14.2.0

## Description

Bumps [@testing-library/user-event](https://github.com/testing-library/user-event) from 14.1.1 to 14.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/testing-library/user-event/releases"><code>@​testing-library/user-event</code>'s releases</a>.</em></p>
<blockquote>
<h2>v14.2.0</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.1.1...v14.2.0">14.2.0</a> (2022-05-12)</h2>
<h3>Features</h3>
<ul>
<li>report element with declaration in <code>pointerEventsCheck</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/950">#950</a>) (<a href="">31b7091</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>guard against selection without range (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/953">#953</a>) (<a href="">ab78f3f</a>)</li>
<li><strong>selectOptions:</strong> wait after each click (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/951">#951</a>) (<a href="">7ea7a77</a>)</li>
<li>wait after each method before leaving <code>asyncWrapper</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/952">#952</a>) (<a href="">6f55fee</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>31b7091</code></a> feat: report element with declaration in <code>pointerEventsCheck</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/950">#950</a>)</li>
<li><a href=""><code>7ea7a77</code></a> fix(selectOptions): wait after each click (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/951">#951</a>)</li>
<li><a href=""><code>6f55fee</code></a> fix: wait after each method before leaving <code>asyncWrapper</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/952">#952</a>)</li>
<li><a href=""><code>ab78f3f</code></a> fix: guard against selection without range (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/953">#953</a>)</li>
<li><a href=""><code>bf00145</code></a> test: correct false-negative for advancing timers (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/948">#948</a>)</li>
<li><a href=""><code>ee062e7</code></a> docs: add yannbf as a contributor for code (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/934">#934</a>)</li>
<li>See full diff in <a href="https://github.com/testing-library/user-event/compare/v14.1.1...v14.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@testing-library/user-event&package-manager=npm_and_yarn&previous-version=14.1.1&new-version=14.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee7c25b0d046`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.