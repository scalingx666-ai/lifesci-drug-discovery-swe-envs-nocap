# Issue

**Title:** Bump actions/checkout from 4.2.2 to 6.0.0

## Description

Bumps [actions/checkout](https://github.com/actions/checkout) from 4.2.2 to 6.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/releases">actions/checkout's releases</a>.</em></p>
<blockquote>
<h2>v6.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Update README to include Node.js 24 support details and requirements by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2248</a></li>
<li>Persist creds to a separate file by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2286</a></li>
<li>v6-beta by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2298</a></li>
<li>update readme/changelog for v6 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2311</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v5.0.0...v6.0.0">https://github.com/actions/checkout/compare/v5.0.0...v6.0.0</a></p>
<h2>v6-beta</h2>
<h2>What's Changed</h2>
<p>Updated persist-credentials to store the credentials under <code>$RUNNER_TEMP</code> instead of directly in the local git config.</p>
<p>This requires a minimum Actions Runner version of <a href="https://github.com/actions/runner/releases/tag/v2.329.0">v2.329.0</a> to access the persisted credentials for <a href="https://docs.github.com/en/actions/tutorials/use-containerized-services/create-a-docker-container-action">Docker container action</a> scenarios.</p>
<h2>v5.0.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Port v6 cleanup to v5 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2301</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v5...v5.0.1">https://github.com/actions/checkout/compare/v5...v5.0.1</a></p>
<h2>v5.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Update actions checkout to use node 24 by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2226</a></li>
<li>Prepare v5.0.0 release by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2238</a></li>
</ul>
<h2>⚠️ Minimum Compatible Runner Version</h2>
<p><strong>v2.327.1</strong><br />
<a href="https://github.com/actions/runner/releases/tag/v2.327.1">Release Notes</a></p>
<p>Make sure your runner is updated to this version or newer to use this release.</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v4...v5.0.0">https://github.com/actions/checkout/compare/v4...v5.0.0</a></p>
<h2>v4.3.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Port v6 cleanup to v4 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2305</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v4...v4.3.1">https://github.com/actions/checkout/compare/v4...v4.3.1</a></p>
<h2>v4.3.0</h2>
<h2>What's Changed</h2>
<ul>
<li>docs: update README.md by <a href="https://github.com/motss"><code>@​motss</code></a> in <a href="">actions/checkout#1971</a></li>
<li>Add internal repos for checking out multiple repositories by <a href="https://github.com/mouismail"><code>@​mouismail</code></a> in <a href="">actions/checkout#1977</a></li>
<li>Documentation update - add recommended permissions to Readme by <a href="https://github.com/benwells"><code>@​benwells</code></a> in <a href="">actions/checkout#2043</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1af3b93</code></a> update readme/changelog for v6 (<a href="">#2311</a>)</li>
<li><a href=""><code>71cf226</code></a> v6-beta (<a href="">#2298</a>)</li>
<li><a href=""><code>069c695</code></a> Persist creds to a separate file (<a href="">#2286</a>)</li>
<li><a href=""><code>ff7abcd</code></a> Update README to include Node.js 24 support details and requirements (<a href="">#2248</a>)</li>
<li><a href=""><code>08c6903</code></a> Prepare v5.0.0 release (<a href="">#2238</a>)</li>
<li><a href=""><code>9f26565</code></a> Update actions checkout to use node 24 (<a href="">#2226</a>)</li>
<li><a href=""><code>08eba0b</code></a> Prepare release v4.3.0 (<a href="">#2237</a>)</li>
<li><a href=""><code>631c7dc</code></a> Update package dependencies (<a href="">#2236</a>)</li>
<li><a href=""><code>8edcb1b</code></a> Update CODEOWNERS for actions (<a href="">#2224</a>)</li>
<li><a href=""><code>09d2aca</code></a> Update README.md (<a href="">#2194</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/checkout/compare/v4.2.2...v6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/checkout&package-manager=github_actions&previous-version=4.2.2&new-version=6.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `edd704e00a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.