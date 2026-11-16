# Issue

**Title:** Bump actions/create-github-app-token from 2 to 3

## Description

Bumps [actions/create-github-app-token](https://github.com/actions/create-github-app-token) from 2 to 3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/create-github-app-token/releases">actions/create-github-app-token's releases</a>.</em></p>
<blockquote>
<h2>v3.0.0</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v2.2.2...v3.0.0">3.0.0</a> (2026-03-14)</h1>
<ul>
<li>feat!: node 24 support (<a href="">#275</a>) (<a href="">2e564a0</a>)</li>
<li>fix!: require <code>NODE_USE_ENV_PROXY</code> for proxy support (<a href="">#342</a>) (<a href="">4451bcb</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>remove custom proxy handling (<a href="">#143</a>) (<a href="">dce0ab0</a>)</li>
</ul>
<h3>BREAKING CHANGES</h3>
<ul>
<li>Custom proxy handling has been removed. If you use HTTP_PROXY or HTTPS_PROXY, you must now also set NODE_USE_ENV_PROXY=1 on the action step.</li>
<li>Requires <a href="https://github.com/actions/runner/releases/tag/v2.327.1">Actions Runner v2.327.1</a> or later if you are using a self-hosted runner.</li>
</ul>
<h2>v3.0.0-beta.6</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v3.0.0-beta.5...v3.0.0-beta.6">3.0.0-beta.6</a> (2026-03-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> bump <code>@​actions/core</code> from 1.11.1 to 3.0.0 (<a href="">#337</a>) (<a href="">b044133</a>)</li>
<li><strong>deps:</strong> bump minimatch from 9.0.5 to 9.0.9 (<a href="">#335</a>) (<a href="">5cbc656</a>)</li>
<li><strong>deps:</strong> bump the production-dependencies group with 4 updates (<a href="">#336</a>) (<a href="">6bda5bc</a>)</li>
<li><strong>deps:</strong> bump undici from 7.16.0 to 7.18.2 (<a href="">#323</a>) (<a href="">b4f638f</a>)</li>
</ul>
<h2>v3.0.0-beta.5</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v3.0.0-beta.4...v3.0.0-beta.5">3.0.0-beta.5</a> (2026-03-13)</h1>
<ul>
<li>fix!: require <code>NODE_USE_ENV_PROXY</code> for proxy support (<a href="">#342</a>) (<a href="">d53a1cd</a>)</li>
</ul>
<h3>BREAKING CHANGES</h3>
<ul>
<li>Custom proxy handling has been removed. If you use HTTP_PROXY or HTTPS_PROXY, you must now also set NODE_USE_ENV_PROXY=1 on the action step.</li>
</ul>
<h2>v3.0.0-beta.4</h2>
<h1><a href="https://github.com/actions/create-github-app-token/compare/v3.0.0-beta.3...v3.0.0-beta.4">3.0.0-beta.4</a> (2026-03-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> bump <code>@​octokit/auth-app</code> from 7.2.1 to 8.0.1 (<a href="">#257</a>) (<a href="">bef1eaf</a>)</li>
<li><strong>deps:</strong> bump <code>@​octokit/request</code> from 9.2.3 to 10.0.2 (<a href="">#256</a>) (<a href="">5d7307b</a>)</li>
<li><strong>deps:</strong> bump glob from 10.4.5 to 10.5.0 (<a href="">#305</a>) (<a href="">5480f43</a>)</li>
<li><strong>deps:</strong> bump p-retry from 6.2.1 to 7.1.0 (<a href="">#294</a>) (<a href="">dce3be8</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f8d387b</code></a> build(release): 3.0.0 [skip ci]</li>
<li><a href=""><code>d2129bd</code></a> style: remove extra blank line in release workflow</li>
<li><a href=""><code>77b94ef</code></a> build: refresh generated artifacts</li>
<li><a href=""><code>3ab4c66</code></a> chore: move undici to devDependencies</li>
<li><a href=""><code>739cf66</code></a> docs: update README action versions</li>
<li><a href=""><code>db40289</code></a> build(deps): bump actions versions in test.yml</li>
<li><a href=""><code>496a7ac</code></a> test: migrate from AVA to Node.js native test runner (<a href="">#346</a>)</li>
<li><a href=""><code>3870dc3</code></a> Rename end-to-end proxy job in test workflow</li>
<li><a href=""><code>4451bcb</code></a> fix!: require <code>NODE_USE_ENV_PROXY</code> for proxy support (<a href="">#342</a>)</li>
<li><a href=""><code>dce0ab0</code></a> fix: remove custom proxy handling (<a href="">#143</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/create-github-app-token/compare/v2...v3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/create-github-app-token&package-manager=github_actions&previous-version=2&new-version=3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `663ced45a3e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.