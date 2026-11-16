# Issue

**Title:** Bump @testing-library/user-event from 14.3.0 to 14.4.1

## Description

Bumps [@testing-library/user-event](https://github.com/testing-library/user-event) from 14.3.0 to 14.4.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/testing-library/user-event/releases"><code>@​testing-library/user-event</code>'s releases</a>.</em></p>
<blockquote>
<h2>v14.4.1</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.4.0...v14.4.1">14.4.1</a> (2022-08-02)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>build:</strong> transpile to es2019 syntax (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1016">#1016</a>) (<a href="">4291cb8</a>)</li>
</ul>
<h2>v14.4.0</h2>
<h2><a href="https://github.com/testing-library/user-event/compare/v14.3.0...v14.4.0">14.4.0</a> (2022-08-02)</h2>
<h3>Features</h3>
<ul>
<li><strong>pointer</strong>: dispatch <code>auxclick</code> events (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><strong>event:</strong> be robust against incomplete event implementations (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1009">#1009</a>) (<a href="">289828b</a>)</li>
<li><strong>upload:</strong> be robust against missing FileList implementation (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1007">#1007</a>) (<a href="">a46b4d7</a>)</li>
<li><strong>keyboard</strong>: switch modifier state of lock keys on the correct event (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>keyboard</strong>: remove platform-specific additional key events for <code>Control</code> on <code>AltGraph</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: dispatch <code>contextmenu</code> events with <code>detail: 0</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: always set <code>PointerEvent.isPrimary</code> (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: set <code>button</code> property on pointer events separately from legacy mouse events (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: click closest common ancestor if <code>mousedown</code> and <code>mouseup</code> happen on different elements (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: omit click event on release if another button is released first (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: dispatch <code>mouseover</code>, <code>mouseenter</code> and <code>mousemove</code> on disabled elements (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: prevent <code>mouse*</code> events per <code>pointerdown</code> event handler (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: dispatch <code>*out</code> and <code>*over</code> events when moving into / out of nested elements (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
<li><strong>pointer</strong>: dispatch <code>*enter</code> and <code>*leave</code> events on ancestors (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>) (<a href="">2852509</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4291cb8</code></a> fix(build): transpile to es2019 syntax (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1016">#1016</a>)</li>
<li><a href=""><code>47f2036</code></a> docs: add DGollings as a contributor for bug (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1013">#1013</a>)</li>
<li><a href=""><code>7b1aeea</code></a> docs: add alkstal as a contributor for bug (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1012">#1012</a>)</li>
<li><a href=""><code>01abea3</code></a> docs: add Parnswir as a contributor for bug (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1011">#1011</a>)</li>
<li><a href=""><code>289828b</code></a> fix(event): be robust against incomplete event implementations (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1009">#1009</a>)</li>
<li><a href=""><code>a46b4d7</code></a> fix(upload): be robust against missing FileList implementation (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1007">#1007</a>)</li>
<li><a href=""><code>2852509</code></a> feat: separate input devices from pointer/keyboard API (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1003">#1003</a>)</li>
<li><a href=""><code>c6aafb7</code></a> test: prevent false-positive with fake timers (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1010">#1010</a>)</li>
<li><a href=""><code>1c156c2</code></a> chore: do not build in pre-commit (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1008">#1008</a>)</li>
<li><a href=""><code>6749918</code></a> docs: add marilari88 as a contributor for doc (<a href="https://github-redirect.dependabot.com/testing-library/user-event/issues/1005">#1005</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/testing-library/user-event/compare/v14.3...v14.4.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@testing-library/user-event&package-manager=npm_and_yarn&previous-version=14.3.0&new-version=14.4.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `867b4bcb3ce7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.