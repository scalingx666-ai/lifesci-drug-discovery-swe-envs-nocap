# Issue

**Title:** Bump actions/create-github-app-token from 1 to 2

## Description

Bumps [actions/create-github-app-token](https://github.com/actions/create-github-app-token) from 1 to 2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/create-github-app-token/releases">actions/create-github-app-token's releases</a>.</em></p>
<blockquote>
<h2>v2.0.0</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v1.12.0...v2.0.0">2.0.0</a> (2025-04-03)</h1>
<ul>
<li>feat!: remove deprecated inputs (<a href="">#213</a>) (<a href="">5cc811b</a>)</li>
</ul>
<h3>BREAKING CHANGES</h3>
<ul>
<li>Removed deprecated inputs (<code>app_id</code>, <code>private_key</code>, <code>skip_token_revoke</code>) and made <code>app-id</code> and <code>private-key</code> required in the action configuration.</li>
</ul>
<h2>v1.12.0</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v1.11.7...v1.12.0">1.12.0</a> (2025-03-27)</h1>
<h3>Features</h3>
<ul>
<li>permissions (<a href="">#168</a>) (<a href="">0e0aa99</a>)</li>
</ul>
<h2>v1.11.7</h2>
<h2><a href="https://github.com/actions/create-github-app-token/compare/v1.11.6...v1.11.7">1.11.7</a> (2025-03-20)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> bump undici from 5.28.4 to 7.5.0 (<a href="">#214</a>) (<a href="">a24b46a</a>)</li>
</ul>
<h2>v1.11.6</h2>
<h2><a href="https://github.com/actions/create-github-app-token/compare/v1.11.5...v1.11.6">1.11.6</a> (2025-03-03)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> bump the production-dependencies group with 2 updates (<a href="">#210</a>) (<a href="">1ff1dea</a>)</li>
</ul>
<h2>v1.11.5</h2>
<h2><a href="https://github.com/actions/create-github-app-token/compare/v1.11.4...v1.11.5">1.11.5</a> (2025-02-15)</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3ff1caa</code></a> build(release): 2.0.2 [skip ci]</li>
<li><a href=""><code>eaef294</code></a> fix: improve log messages for token creation (<a href="">#226</a>)</li>
<li><a href=""><code>86e2496</code></a> build(release): 2.0.1 [skip ci]</li>
<li><a href=""><code>2411bfc</code></a> fix(deps): bump the production-dependencies group across 1 directory with 2 u...</li>
<li><a href=""><code>f17d09a</code></a> build(deps-dev): bump the development-dependencies group with 3 updates (<a href="">#225</a>)</li>
<li><a href=""><code>e250d17</code></a> ci(update-permission-inputs): add permissions (<a href="">#230</a>)</li>
<li><a href=""><code>ed258b4</code></a> Rename workflow</li>
<li><a href=""><code>5c652ca</code></a> Update update-inputs.yml</li>
<li><a href=""><code>60ee75d</code></a> ci(update-inputs): create initial version (<a href="">#229</a>)</li>
<li><a href=""><code>064492a</code></a> build(release): 2.0.0 [skip ci]</li>
<li>Additional commits viewable in <a href="https://github.com/actions/create-github-app-token/compare/v1...v2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/create-github-app-token&package-manager=github_actions&previous-version=1&new-version=2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `375ee5720d7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.