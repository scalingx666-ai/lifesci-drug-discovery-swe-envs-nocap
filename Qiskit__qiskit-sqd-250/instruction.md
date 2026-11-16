# Issue

**Title:** Bump ghalactic/github-release-from-tag from 5 to 6

## Description

Bumps [ghalactic/github-release-from-tag](https://github.com/ghalactic/github-release-from-tag) from 5 to 6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ghalactic/github-release-from-tag/releases">ghalactic/github-release-from-tag's releases</a>.</em></p>
<blockquote>
<h2>v6</h2>
<p>This tag currently points to <a href="https://github.com/ghalactic/github-release-from-tag/releases/v6.0.1">v6.0.1</a></p>
<!-- raw HTML omitted -->
<h2>v6.0.0</h2>
<h3><!-- raw HTML omitted --><!-- raw HTML omitted -->Changed</h3>
<ul>
<li>This action now runs on the <code>node24</code> runner instead of <code>node20</code>. If you are using this action on GitHub Enterprise Server, you will need to ensure your runners support <code>node24</code> before upgrading to this version.</li>
</ul>
<!-- raw HTML omitted -->
<h2>v5.4.0</h2>
<h3><!-- raw HTML omitted --><!-- raw HTML omitted -->Added</h3>
<ul>
<li>Added <a href="#config-file-schema-support">config file schema support</a>.</li>
</ul>
<h4><!-- raw HTML omitted --><!-- raw HTML omitted -->Config file schema support</h4>
<p>The configuration schema is now published at: <a href="https://ghalactic.github.io/github-release-from-tag/schema/config.v5.schema.json">https://ghalactic.github.io/github-release-from-tag/schema/config.v5.schema.json</a></p>
<p>Your editor might be able to use this schema to provide autocompletion and validation for your configuration file. For example, if you're using the <a href="https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml">YAML extension for Visual Studio Code</a>, you can add the following header to your configuration file to enable schema support:</p>
<pre lang="yaml"><code># yaml-language-server: $schema=https://ghalactic.github.io/github-release-from-tag/schema/config.v5.schema.json
assets:
  - path: assets/text/file-a.txt
  - path: assets/json/file-b.json
    optional: true
    name: custom-name-b.json
    label: Label for file-b.json
</code></pre>
<p>In case your editor supports using a <code>$schema</code> property directly in the YAML file, the schema has been relaxed to allow this as well:</p>
<pre lang="yaml"><code>$schema: https://ghalactic.github.io/github-release-from-tag/schema/config.v5.schema.json
assets:
  - path: assets/text/file-a.txt
  - path: assets/json/file-b.json
    optional: true
    name: custom-name-b.json
    label: Label for file-b.json
&lt;/tr&gt;&lt;/table&gt;
</code></pre>
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ghalactic/github-release-from-tag/blob/main/CHANGELOG.md">ghalactic/github-release-from-tag's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v5.0.1">v5.0.1</a> - 2024-03-06</h2>
<h3>Fixed</h3>
<ul>
<li>Dependency updates.</li>
</ul>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v5.0.0">v5.0.0</a> - 2023-08-28</h2>
<h3>Changed</h3>
<ul>
<li>This action now runs on the <code>node20</code> runner instead of <code>node16</code>. If you are
using this action on GitHub Enterprise Server, you will need to ensure your
runners support <code>node20</code> before upgrading to this version.</li>
</ul>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v4.2.0">v4.2.0</a> - 2023-08-28</h2>
<h3>Changed</h3>
<ul>
<li>Reverted the <code>v4</code> version of this action to run on Node.js <code>16.x</code> instead of
<code>20.x</code>. The switch to <code>20.x</code> was causing issues with GitHub Enterprise Server
users who don't have support for <code>node20</code> runners yet. A <code>v5</code> version of this
action will be released shortly that will run on Node.js <code>20.x</code>.</li>
</ul>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v4.1.3">v4.1.3</a> - 2023-08-26</h2>
<h3>Fixed</h3>
<ul>
<li>Fixed further internal issues with GitHub Actions shared workflows. No effect
on the action itself.</li>
</ul>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v4.1.2">v4.1.2</a> - 2023-08-26</h2>
<h3>Fixed</h3>
<ul>
<li>Fixed further internal issues with GitHub Actions shared workflows. No effect
on the action itself.</li>
</ul>
<h2><a href="https://github.com/ghalactic/github-release-from-tag/releases/v4.1.1">v4.1.1</a> - 2023-08-26</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>786cabb</code></a> Fix schema versions and README examples</li>
<li><a href=""><code>88eb5ae</code></a> Prepare v6.0.0 release</li>
<li><a href=""><code>8f031d8</code></a> Use node24 as the esbuild target</li>
<li><a href=""><code>940a223</code></a> Update to the <code>node24</code> runner</li>
<li><a href=""><code>b6c641e</code></a> Update dependency <code>@​types/node</code> to v22.18.0</li>
<li><a href=""><code>9a03845</code></a> Update dependency puppeteer to v24.17.0</li>
<li><a href=""><code>1d8fa18</code></a> Update dependency <code>@​types/node</code> to v22.17.2</li>
<li><a href=""><code>ab9d500</code></a> Update dependency puppeteer to v24.16.2</li>
<li><a href=""><code>a227dff</code></a> Update dependency esbuild to v0.25.9</li>
<li><a href=""><code>2d94a69</code></a> Merge pull request <a href="">#195</a> from ghalactic/renovate/actions-checkout-5.x</li>
<li>Additional commits viewable in <a href="https://github.com/ghalactic/github-release-from-tag/compare/v5...v6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ghalactic/github-release-from-tag&package-manager=github_actions&previous-version=5&new-version=6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3172810249e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.