# Issue

**Title:** ci(deps): bump astral-sh/setup-uv from 4 to 6

## Description

Bumps [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv) from 4 to 6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v6.6.0 🌈 Support for .tools-versions</h2>
<h2>Changes</h2>
<p>This release adds support for <a href="https://asdf-vm.com/">asdf</a> <code>.tool-versions</code> in the <code>version-file</code> input</p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>Add log message before long API calls to GitHub <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#530</a>)</li>
</ul>
<h2>🚀 Enhancements</h2>
<ul>
<li>Add support for .tools-versions <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#531</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>Bump dependencies <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#532</a>)</li>
<li>chore: update known versions for 0.8.12 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#529</a>)</li>
<li>chore: update known versions for 0.8.11 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#526</a>)</li>
<li>chore: update known versions for 0.8.10 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#525</a>)</li>
</ul>
<h2>v6.2.1 🌈 Fix &quot;No such file or directory version-manifest.json&quot;</h2>
<h2>Changes</h2>
<p>Release v6.2.0 contained a bug that slipped through the automated test. The action tried to look for the default version-manifest.json in the root of the repostory using this action instead of relative to the action itself.</p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>Look for version-manifest.json relative to action path <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#456</a>)</li>
</ul>
<h2>v6.0.0 🌈 activate-environment and working-directory</h2>
<h2>Changes</h2>
<p>This version contains some breaking changes which have been gathering up for a while. Lets dive into them:</p>
<ul>
<li><a href="https://github.com/astral-sh/setup-uv/blob/HEAD/#activate-environment">Activate environment</a></li>
<li><a href="https://github.com/astral-sh/setup-uv/blob/HEAD/#working-directory">Working Directory</a></li>
<li><a href="https://github.com/astral-sh/setup-uv/blob/HEAD/#default-cache-dependency-glob">Default <code>cache-dependency-glob</code></a></li>
<li><a href="https://github.com/astral-sh/setup-uv/blob/HEAD/#use-default-cache-dir-on-self-hosted-runners">Use default cache dir on self hosted runners</a></li>
</ul>
<h3>Activate environment</h3>
<p>In previous versions using the input <code>python-version</code> automatically activated a venv at the repository root.
This led to some unwanted side-effects, was sometimes unexpected and not flexible enough.</p>
<p>The venv activation is now explicitly controlled with the new input <code>activate-environment</code> (false by default):</p>
<pre lang="yaml"><code>- name: Install the latest version of uv and activate the environment
  uses: astral-sh/setup-uv@v6
  with:
&lt;/tr&gt;&lt;/table&gt;
</code></pre>
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>557e51d</code></a> Bump dependencies (<a href="">#547</a>)</li>
<li><a href=""><code>1b46e13</code></a> Fix exclusions in cache-dependency-glob (<a href="">#546</a>)</li>
<li><a href=""><code>26cf676</code></a> chore: update known versions for 0.8.14 (<a href="">#543</a>)</li>
<li><a href=""><code>4e1e303</code></a> chore: update known versions for 0.8.13 (<a href="">#536</a>)</li>
<li><a href=""><code>4959332</code></a> Bump dependencies (<a href="">#532</a>)</li>
<li><a href=""><code>adeb286</code></a> Add support for .tools-versions (<a href="">#531</a>)</li>
<li><a href=""><code>fce199e</code></a> Add log message before long API calls to GitHub (<a href="">#530</a>)</li>
<li><a href=""><code>f758a4a</code></a> chore: update known versions for 0.8.12 (<a href="">#529</a>)</li>
<li><a href=""><code>c0e7e93</code></a> chore: update known versions for 0.8.11 (<a href="">#526</a>)</li>
<li><a href=""><code>fda2399</code></a> chore: update known versions for 0.8.10 (<a href="">#525</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/setup-uv/compare/v4...v6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=astral-sh/setup-uv&package-manager=github_actions&previous-version=4&new-version=6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c82316a9afc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.