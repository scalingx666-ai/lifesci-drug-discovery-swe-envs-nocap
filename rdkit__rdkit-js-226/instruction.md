# Issue

**Title:** Bump serve from 14.0.1 to 14.1.0

## Description

Bumps [serve](https://github.com/vercel/serve) from 14.0.1 to 14.1.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/serve/releases">serve's releases</a>.</em></p>
<blockquote>
<h2>14.1.0</h2>
<h3>Minor Changes</h3>
<ul>
<li>Feat: Add support for PFX or PKCS12 encoded certificates: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/708">#708</a></li>
<li>Feat: add request logging: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/716">#716</a></li>
</ul>
<h3>Patches</h3>
<ul>
<li>Docs(readme): add note about using node 14+: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/715">#715</a></li>
<li>Tests: add cli unit tests: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/719">#719</a></li>
<li>Test: Included tests for verifying SSL hosting: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/720">#720</a></li>
<li>Bump <code>serve-handler</code> from <code>6.1.3</code> to <code>6.1.5</code>: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/738">#738</a></li>
<li>Add publish workflow: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/740">#740</a></li>
</ul>
<h3>Credits</h3>
<p>Huge thanks to <a href="https://github.com/schemburkar"><code>@​schemburkar</code></a> and <a href="https://github.com/gamemaker1"><code>@​gamemaker1</code></a> for helping!</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>526a717</code></a> 14.1.0</li>
<li><a href=""><code>30842d4</code></a> Add publish workflow (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/740">#740</a>)</li>
<li><a href=""><code>161b807</code></a> Bump <code>serve-handler</code> from <code>6.1.3</code> to <code>6.1.5</code> (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/738">#738</a>)</li>
<li><a href=""><code>337279c</code></a> feat: add request logging (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/716">#716</a>)</li>
<li><a href=""><code>0616ce3</code></a> Test: Included tests for verifying SSL hosting (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/720">#720</a>)</li>
<li><a href=""><code>92fd640</code></a> feat: Add support for PFX or PKCS12 encoded certificates (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/708">#708</a>)</li>
<li><a href=""><code>36d60e7</code></a> tests: add cli unit tests (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/719">#719</a>)</li>
<li><a href=""><code>f8abc37</code></a> docs(readme): add note about using node 14+ (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/715">#715</a>)</li>
<li>See full diff in <a href="https://github.com/vercel/serve/compare/14.0.1...14.1.0">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~vercel-release-bot">vercel-release-bot</a>, a new releaser for serve since your current version.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=serve&package-manager=npm_and_yarn&previous-version=14.0.1&new-version=14.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d234c0418b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.