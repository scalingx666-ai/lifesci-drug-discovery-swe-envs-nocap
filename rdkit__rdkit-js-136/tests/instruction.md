# Issue

**Title:** Bump serve from 13.0.4 to 14.0.0

## Description

Bumps [serve](https://github.com/vercel/serve) from 13.0.4 to 14.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/serve/releases">serve's releases</a>.</em></p>
<blockquote>
<h2>14.0.0</h2>
<h3>Overview</h3>
<p><code>serve</code> has had a major update:</p>
<ul>
<li>The core library has been rewritten in TypeScript</li>
<li>The core library is now an ES Module</li>
<li>Added <code>eslint</code> and <code>prettier</code></li>
<li>Added <code>husky</code> and <code>lint-staged</code></li>
</ul>
<p>We now also have a <a href="https://github.com/vercel/serve/blob/main/contributing.md">contribution guide</a>, with linting/type checking running on a GitHub Actions workflow. There are also issue and pull request templates to help folks contribute more easily to the repository.</p>
<h3>Major Changes</h3>
<ul>
<li>[major] TypeScript rewrite, support ES Modules.: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/706">#706</a></li>
</ul>
<h3>Credits</h3>
<p>Huge thanks to <a href="https://github.com/gamemaker1"><code>@​gamemaker1</code></a> for helping!</p>
<h2>14.0.0-canary.0</h2>
<h3>Major Changes</h3>
<ul>
<li>[major] TypeScript rewrite, support ES Modules.: <a href="https://github-redirect.dependabot.com/vercel/serve/issues/706">#706</a></li>
</ul>
<h3>Credits</h3>
<p>Huge thanks to <a href="https://github.com/gamemaker1"><code>@​gamemaker1</code></a> for helping!</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>995247d</code></a> 14.0.0</li>
<li><a href=""><code>a2512c9</code></a> 14.0.0-canary.0</li>
<li><a href=""><code>f67fd3b</code></a> 13.0.4-canary.0</li>
<li><a href=""><code>d2a5187</code></a> [major] TypeScript rewrite, support ES Modules. (<a href="https://github-redirect.dependabot.com/vercel/serve/issues/706">#706</a>)</li>
<li>See full diff in <a href="https://github.com/vercel/serve/compare/13.0.4...14.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=serve&package-manager=npm_and_yarn&previous-version=13.0.4&new-version=14.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a878357cab7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.