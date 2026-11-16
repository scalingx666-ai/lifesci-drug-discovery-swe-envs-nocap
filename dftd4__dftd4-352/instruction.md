# Issue

**Title:** Bump actions/cache from 4 to 5

## Description

Bumps [actions/cache](https://github.com/actions/cache) from 4 to 5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/cache/releases">actions/cache's releases</a>.</em></p>
<blockquote>
<h2>v5.0.0</h2>
<blockquote>
<p>[!IMPORTANT]
<strong><code>actions/cache@v5</code> runs on the Node.js 24 runtime and requires a minimum Actions Runner version of <code>2.327.1</code>.</strong></p>
<p>If you are using self-hosted runners, ensure they are updated before upgrading.</p>
</blockquote>
<hr />
<h2>What's Changed</h2>
<ul>
<li>Upgrade to use node24 by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/cache#1630</a></li>
<li>Prepare v5.0.0 release by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/cache#1684</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/cache/compare/v4.3.0...v5.0.0">https://github.com/actions/cache/compare/v4.3.0...v5.0.0</a></p>
<h2>v4.3.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add note on runner versions by <a href="https://github.com/GhadimiR"><code>@​GhadimiR</code></a> in <a href="">actions/cache#1642</a></li>
<li>Prepare <code>v4.3.0</code> release by <a href="https://github.com/Link"><code>@​Link</code></a>- in <a href="">actions/cache#1655</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/GhadimiR"><code>@​GhadimiR</code></a> made their first contribution in <a href="">actions/cache#1642</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/cache/compare/v4...v4.3.0">https://github.com/actions/cache/compare/v4...v4.3.0</a></p>
<h2>v4.2.4</h2>
<h2>What's Changed</h2>
<ul>
<li>Update README.md by <a href="https://github.com/nebuk89"><code>@​nebuk89</code></a> in <a href="">actions/cache#1620</a></li>
<li>Upgrade <code>@actions/cache</code> to <code>4.0.5</code> and move <code>@protobuf-ts/plugin</code> to dev depdencies by <a href="https://github.com/Link"><code>@​Link</code></a>- in <a href="">actions/cache#1634</a></li>
<li>Prepare release <code>4.2.4</code> by <a href="https://github.com/Link"><code>@​Link</code></a>- in <a href="">actions/cache#1636</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/nebuk89"><code>@​nebuk89</code></a> made their first contribution in <a href="">actions/cache#1620</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/cache/compare/v4...v4.2.4">https://github.com/actions/cache/compare/v4...v4.2.4</a></p>
<h2>v4.2.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Update to use <code>@​actions/cache</code> 4.0.3 package &amp; prepare for new release by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/cache#1577</a> (SAS tokens for cache entries are now masked in debug logs)</li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> made their first contribution in <a href="">actions/cache#1577</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/cache/compare/v4.2.2...v4.2.3">https://github.com/actions/cache/compare/v4.2.2...v4.2.3</a></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/actions/cache/blob/main/RELEASES.md">actions/cache's changelog</a>.</em></p>
<blockquote>
<h1>Releases</h1>
<h2>How to prepare a release</h2>
<blockquote>
<p>[!NOTE]<br />
Relevant for maintainers with write access only.</p>
</blockquote>
<ol>
<li>Switch to a new branch from <code>main</code>.</li>
<li>Run <code>npm test</code> to ensure all tests are passing.</li>
<li>Update the version in <a href="https://github.com/actions/cache/blob/main/package.json"><code>https://github.com/actions/cache/blob/main/package.json</code></a>.</li>
<li>Run <code>npm run build</code> to update the compiled files.</li>
<li>Update this <a href="https://github.com/actions/cache/blob/main/RELEASES.md"><code>https://github.com/actions/cache/blob/main/RELEASES.md</code></a> with the new version and changes in the <code>## Changelog</code> section.</li>
<li>Run <code>licensed cache</code> to update the license report.</li>
<li>Run <code>licensed status</code> and resolve any warnings by updating the <a href="https://github.com/actions/cache/blob/main/.licensed.yml"><code>https://github.com/actions/cache/blob/main/.licensed.yml</code></a> file with the exceptions.</li>
<li>Commit your changes and push your branch upstream.</li>
<li>Open a pull request against <code>main</code> and get it reviewed and merged.</li>
<li>Draft a new release <a href="https://github.com/actions/cache/releases">https://github.com/actions/cache/releases</a> use the same version number used in <code>package.json</code>
<ol>
<li>Create a new tag with the version number.</li>
<li>Auto generate release notes and update them to match the changes you made in <code>RELEASES.md</code>.</li>
<li>Toggle the set as the latest release option.</li>
<li>Publish the release.</li>
</ol>
</li>
<li>Navigate to <a href="https://github.com/actions/cache/actions/workflows/release-new-action-version.yml">https://github.com/actions/cache/actions/workflows/release-new-action-version.yml</a>
<ol>
<li>There should be a workflow run queued with the same version number.</li>
<li>Approve the run to publish the new version and update the major tags for this action.</li>
</ol>
</li>
</ol>
<h2>Changelog</h2>
<h3>5.0.4</h3>
<ul>
<li>Bump <code>minimatch</code> to v3.1.5 (fixes ReDoS via globstar patterns)</li>
<li>Bump <code>undici</code> to v6.24.1 (WebSocket decompression bomb protection, header validation fixes)</li>
<li>Bump <code>fast-xml-parser</code> to v5.5.6</li>
</ul>
<h3>5.0.3</h3>
<ul>
<li>Bump <code>@actions/cache</code> to v5.0.5 (Resolves: <a href="https://github.com/actions/cache/security/dependabot/33">https://github.com/actions/cache/security/dependabot/33</a>)</li>
<li>Bump <code>@actions/core</code> to v2.0.3</li>
</ul>
<h3>5.0.2</h3>
<ul>
<li>Bump <code>@actions/cache</code> to v5.0.3 <a href="">#1692</a></li>
</ul>
<h3>5.0.1</h3>
<ul>
<li>Update <code>@azure/storage-blob</code> to <code>^12.29.1</code> via <code>@actions/cache@5.0.1</code> <a href="">#1685</a></li>
</ul>
<h3>5.0.0</h3>
<blockquote>
<p>[!IMPORTANT]
<code>actions/cache@v5</code> runs on the Node.js 24 runtime and requires a minimum Actions Runner version of <code>2.327.1</code>.</p>
</blockquote>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6682284</code></a> Merge pull request <a href="">#1738</a> from actions/prepare-v5.0.4</li>
<li><a href=""><code>e340396</code></a> Update RELEASES</li>
<li><a href=""><code>8a67110</code></a> Add licenses</li>
<li><a href=""><code>1865903</code></a> Update dependencies &amp; patch security vulnerabilities</li>
<li><a href=""><code>5656298</code></a> Merge pull request <a href="">#1722</a> from RyPeck/patch-1</li>
<li><a href=""><code>4e380d1</code></a> Fix cache key in examples.md for bun.lock</li>
<li><a href=""><code>b7e8d49</code></a> Merge pull request <a href="">#1701</a> from actions/Link-/fix-proxy-integration-tests</li>
<li><a href=""><code>984a21b</code></a> Add traffic sanity check step</li>
<li><a href=""><code>acf2f1f</code></a> Fix resolution</li>
<li><a href=""><code>95a07c5</code></a> Add wait for proxy</li>
<li>Additional commits viewable in <a href="https://github.com/actions/cache/compare/v4...v5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/cache&package-manager=github_actions&previous-version=4&new-version=5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e7aa70171b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.