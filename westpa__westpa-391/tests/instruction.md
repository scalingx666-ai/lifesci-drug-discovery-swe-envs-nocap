# Issue

**Title:** Bump pypa/cibuildwheel from 2.16.5 to 2.17.0

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 2.16.5 to 2.17.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>v2.17.0</h2>
<ul>
<li>🌟 Adds the ability to inherit configuration in TOML overrides. This makes certain configurations much simpler. If you're overriding an option like <code>before-build</code> or <code>environment</code>, and you just want to add an  extra command or environment variable, you can just append (or prepend) to the previous config. See <a href="https://cibuildwheel.pypa.io/en/stable/options/#inherit">the docs</a> for more information. (<a href="">#1730</a>)</li>
<li>🌟 Adds official support for native arm64 macOS GitHub runners. To use them, just specify <code>macos-14</code> as an <code>os</code> of your job in your workflow file. You can also keep <code>macos-13</code> in your build matrix to build x86_64. Check out the new <a href="https://cibuildwheel.pypa.io/en/stable/setup/#github-actions">GitHub Actions example config</a>.</li>
<li>✨ You no longer need to specify <code>--platform</code> to run cibuildwheel locally! Instead it will detect your platform automatically. This was a safety feature, no longer necessary. (<a href="">#1727</a>)</li>
<li>🛠 Removed setuptools and wheel pinned versions. This only affects old-style projects without a <code>pyproject.toml</code>, projects with <code>pyproject.toml</code> are already getting fresh versions of their <code>build-system.requires</code> installed into an isolated environment. (<a href="">#1725</a>)</li>
<li>🛠 Improve how the GitHub Action passes arguments (<a href="">#1757</a>)</li>
<li>🛠 Remove a system-wide install of pipx in the GitHub Action (<a href="">#1745</a>)</li>
<li>🐛 No longer will cibuildwheel override the PIP_CONSTRAINT environment variable when using the <code>build</code> frontend. Instead it will be extended. (<a href="">#1675</a>)</li>
<li>🐛 Fix a bug where building and testing both x86_86 and arm64 wheels on the same runner caused the wrong architectures in the test environment (<a href="">#1750</a>)</li>
<li>🐛 Fix a bug that prevented testing a CPython 3.8 wheel targeting macOS 11+ on x86_64 (<a href="">#1768</a>)</li>
<li>📚 Moved the docs onto the official PyPA domain - they're now available at <a href="https://cibuildwheel.pypa.io">https://cibuildwheel.pypa.io</a> . (<a href="">#1775</a>)</li>
<li>📚 Docs and examples improvements (<a href="">#1762</a>, <a href="">#1734</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<h3>v2.17.0</h3>
<p><em>11 March 2024</em></p>
<ul>
<li>🌟 Adds the ability to inherit configuration in TOML overrides. This makes certain configurations much simpler. If you're overriding an option like <code>before-build</code> or <code>environment</code>, and you just want to add an  extra command or environment variable, you can just append (or prepend) to the previous config. See <a href="https://cibuildwheel.pypa.io/en/stable/options/#inherit">the docs</a> for more information. (<a href="">#1730</a>)</li>
<li>🌟 Adds official support for native arm64 macOS GitHub runners. To use them, just specify <code>macos-14</code> as an <code>os</code> of your job in your workflow file. You can also keep <code>macos-13</code> in your build matrix to build x86_64. Check out the new <a href="https://cibuildwheel.pypa.io/en/stable/setup/#github-actions">GitHub Actions example config</a>.</li>
<li>✨ You no longer need to specify <code>--platform</code> to run cibuildwheel locally! Instead it will detect your platform automatically. This was a safety feature, no longer necessary. (<a href="">#1727</a>)</li>
<li>🛠 Removed setuptools and wheel pinned versions. This only affects old-style projects without a <code>pyproject.toml</code>, projects with <code>pyproject.toml</code> are already getting fresh versions of their <code>build-system.requires</code> installed into an isolated environment. (<a href="">#1725</a>)</li>
<li>🛠 Improve how the GitHub Action passes arguments (<a href="">#1757</a>)</li>
<li>🛠 Remove a system-wide install of pipx in the GitHub Action (<a href="">#1745</a>)</li>
<li>🐛 No longer will cibuildwheel override the PIP_CONSTRAINT environment variable when using the <code>build</code> frontend. Instead it will be extended. (<a href="">#1675</a>)</li>
<li>🐛 Fix a bug where building and testing both x86_86 and arm64 wheels on the same runner caused the wrong architectures in the test environment (<a href="">#1750</a>)</li>
<li>🐛 Fix a bug that prevented testing a CPython 3.8 wheel targeting macOS 11+ on x86_64 (<a href="">#1768</a>)</li>
<li>📚 Moved the docs onto the official PyPA domain - they're now available at <a href="https://cibuildwheel.pypa.io">https://cibuildwheel.pypa.io</a> . (<a href="">#1775</a>)</li>
<li>📚 Docs and examples improvements (<a href="">#1762</a>, <a href="">#1734</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8d94547</code></a> Bump version: v2.17.0</li>
<li><a href=""><code>ca06deb</code></a> Merge pull request <a href="">#1775</a> from pypa/doc-domain</li>
<li><a href=""><code>f7e1922</code></a> CirrusCI fixes (<a href="">#1786</a>)</li>
<li><a href=""><code>0d8e919</code></a> [Bot] Update dependencies (<a href="">#1784</a>)</li>
<li><a href=""><code>022de07</code></a> Merge pull request <a href="">#1785</a> from pypa/revert-1783</li>
<li><a href=""><code>920f574</code></a> Remove manylinux1 docker pin</li>
<li><a href=""><code>5c06f3c</code></a> docs: Add how to run tests in development (<a href="">#1698</a>)</li>
<li><a href=""><code>e2a0839</code></a> fix: set SYSTEM_VERSION_COMPAT=0 during pip install on macos (<a href="">#1768</a>)</li>
<li><a href=""><code>87fff77</code></a> chore(deps): bump the actions group with 1 update (<a href="">#1776</a>)</li>
<li><a href=""><code>8ef9486</code></a> Add <code>pedalboard</code> to projects.yml. (<a href="">#1781</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v2.16.5...v2.17.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=2.16.5&new-version=2.17.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4e722013d79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.