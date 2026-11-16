# Issue

**Title:** Bump @testing-library/user-event from 14.2.1 to 14.2.5

## Description

Bumps [@testing-library/user-event](https://github.com/testing-library/user-event) from 14.2.1 to 14.2.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/testing-library/user-event/releases"><code>@​testing-library/user-event</code>'s releases</a>.</em></p>
<blockquote>
<h2>v14.2.5</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.2.4...v14.2.5">14.2.5</a> (2022-07-15)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>document:</strong> do not track <code>value</code> on <code>HTMLSelectElement</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/989">#989</a>) (<a href="">77a7fa8</a>)</li>
</ul>
<h2>v14.2.4</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.2.3...v14.2.4">14.2.4</a> (2022-07-15)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>use <code>window.FileList</code> instead of implicit global (<a href="">c88865d</a>)</li>
</ul>
<h2>v14.2.3</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.2.2...v14.2.3">14.2.3</a> (2022-07-14)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>document:</strong> use setters/methods on element as default (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/987">#987</a>) (<a href="">c40e614</a>)</li>
</ul>
<h2>v14.2.2</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.2.1...v14.2.2">14.2.2</a> (2022-07-14)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>document:</strong> track <code>HTMLInputElement.setRangeText()</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/984">#984</a>) (<a href="">73443ec</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>77a7fa8</code></a> fix(document): do not track <code>value</code> on <code>HTMLSelectElement</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/989">#989</a>)</li>
<li><a href=""><code>c88865d</code></a> fix: use <code>window.FileList</code> instead of implicit global</li>
<li><a href=""><code>c376fbc</code></a> chore: whitelist implicit globals</li>
<li><a href=""><code>cf5faed</code></a> docs: add dnt1996 as a contributor for bug (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/988">#988</a>)</li>
<li><a href=""><code>c40e614</code></a> fix(document): use setters/methods on element as default (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/987">#987</a>)</li>
<li><a href=""><code>29bdf14</code></a> docs: add dzonatan as a contributor for bug (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/985">#985</a>)</li>
<li><a href=""><code>73443ec</code></a> fix(document): track <code>HTMLInputElement.setRangeText()</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/984">#984</a>)</li>
<li>See full diff in <a href="https://github.com/testing-library/user-event/compare/v14.2.1...v14.2.5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@testing-library/user-event&package-manager=npm_and_yarn&previous-version=14.2.1&new-version=14.2.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `172dbdd4eb2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.