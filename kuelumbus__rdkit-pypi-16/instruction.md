# Issue

**Title:** Bump pypa/cibuildwheel from 2.1.3 to 2.2.2

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 2.1.3 to 2.2.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>v2.2.2</h2>
<ul>
<li>🐛 Fix bug in the GitHub Action step causing a syntax error (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/895">#895</a>)</li>
</ul>
<h2>v2.2.1</h2>
<ul>
<li>🛠 Added a <code>config-file</code> option on the GitHub Action to specify something other than pyproject.toml in your GitHub Workflow file. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/883">#883</a>)</li>
<li>🐛 Fix missing resources in sdist and released wheel on PyPI. We've also made some internal changes to our release processes to make them more reliable. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/893">#893</a>, <a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/894">#894</a>)</li>
</ul>
<h2>v2.2.1b1</h2>
<ul>
<li>🛠 Added a <code>config-file</code> option on the GitHub Action to specify something
other than pyproject.toml in your GitHub Workflow file. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/883">#883</a>)</li>
<li>🐛 Fix missing resources in sdist and released wheel on PyPI. We've made
some internal change to our release processes to make them more reliable.
(<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/893">#893</a>, <a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/894">#894</a>)</li>
</ul>
<h2>v2.2.0</h2>
<ul>
<li>
<p>🌟 Added support for <a href="https://www.python.org/dev/peps/pep-0656/">musllinux</a>. Support for this new wheel format lets projects build wheels for Linux distributions that use <a href="https://musl.libc.org/">musl libc</a>, notably, <a href="https://alpinelinux.org/">Alpine</a> Docker containers. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/768">#768</a>)</p>
<p>Musllinux builds are enabled by default. If you're not ready to build musllinux, add <code>*-musllinux_*</code> to your <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#build-skip"><code>CIBW_SKIP</code>/<code>skip</code></a> option. Or, you might have to make some changes to your options - to simplify that process, you can use...</p>
</li>
<li>
<p>🌟 TOML option overrides! This provides much greater flexibility in configuration via pyproject.toml. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/854">#854</a>)</p>
<p>You can now set build options for any subset of your builds using a match pattern. So, for example, you can customise CPython 3.8 builds with an override on <code>cp38-*</code> or musllinux builds by selecting <code>*musllinux*</code>. Check out <a href="https://cibuildwheel.readthedocs.io/en/latest/options/#overrides">the docs</a> for more info on the specifics.</p>
</li>
<li>
<p>🛠 Added support for building PyPy wheels on macOS 11 CI runners. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/875">#875</a>)</p>
</li>
<li>
<p>🛠 Setting an empty string for the <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#manylinux-image"><code>CIBW_*_IMAGE</code></a> option will now fallthrough to the config file or cibuildwheel's default, rather than causing an error. This makes the option easier to use in CI build matricies. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/829">#829</a>)</p>
</li>
<li>
<p>🛠 Support for TOML 1.0 when reading config files, via the <code>tomli</code> package. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/876">#876</a>)</p>
</li>
</ul>
<h2>v2.2.0b1</h2>
<p><em>Currently in prerelease. The below release notes will be condensed into a single entry on final release.</em></p>
<p><em>v2.2.0b1 (19 October 2021)</em></p>
<ul>
<li>
<p>🌟 TOML option overrides. This provides much greater flexibility in configuration via pyproject.toml.</p>
<p>You can now set build options for any subset of your builds using a match pattern. So, for example, you can customise CPython 3.8 builds with an override on <code>cp38-*</code> or musllinux builds by selecting <code>*musllinux*</code>. Check out <a href="https://cibuildwheel.readthedocs.io/en/latest/options/#overrides">the docs</a> for more info on the specifics.</p>
</li>
</ul>
<p><em>v2.2.0a1 (23 September 2021)</em></p>
<ul>
<li>
<p>🌟 Added support for <a href="https://www.python.org/dev/peps/pep-0656/">musllinux</a>. Support for this new wheel format lets projects build wheels for Linux distributions that use <a href="https://musl.libc.org/">musl libc</a>, notably, <a href="https://alpinelinux.org/">Alpine</a> Docker containers.</p>
<p>Musllinux builds are enabled by default. To disable them on your project, add <code>*-musllinux_*</code> to your <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#build-skip"><code>CIBW_SKIP</code>/<code>skip</code></a>
option. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/768">#768</a>)</p>
</li>
<li>
<p>🛠 Setting an empty string for the <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#manylinux-image"><code>CIBW_*_IMAGE</code></a> option will now fallthrough to the config file or cibuildwheel's default, rather than causing an error. This makes the option easier to use in CI build matricies. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/829">#829</a>)</p>
</li>
</ul>
<h2>v2.2.0a1</h2>
<p><em>Currently in prerelease. The below release notes will be condensed into a single entry on final release.</em></p>
<p><em>v2.2.0a1 (23 September 2021)</em></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<h3>v2.2.2</h3>
<p><em>26 October 2021</em></p>
<ul>
<li>🐛 Fix bug in the GitHub Action step causing a syntax error (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/895">#895</a>)</li>
</ul>
<h3>v2.2.1</h3>
<p><em>26 October 2021</em></p>
<ul>
<li>🛠 Added a <code>config-file</code> option on the GitHub Action to specify something other than pyproject.toml in your GitHub Workflow file. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/883">#883</a>)</li>
<li>🐛 Fix missing resources in sdist and released wheel on PyPI. We've also made some internal changes to our release processes to make them more reliable. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/893">#893</a>, <a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/894">#894</a>)</li>
</ul>
<h3>v2.2.0</h3>
<p><em>22 October 2021</em></p>
<ul>
<li>
<p>🌟 Added support for <a href="https://www.python.org/dev/peps/pep-0656/">musllinux</a>. Support for this new wheel format lets projects build wheels for Linux distributions that use <a href="https://musl.libc.org/">musl libc</a>, notably, <a href="https://alpinelinux.org/">Alpine</a> Docker containers. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/768">#768</a>)</p>
<p>Musllinux builds are enabled by default. If you're not ready to build musllinux, add <code>*-musllinux_*</code> to your <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#build-skip"><code>CIBW_SKIP</code>/<code>skip</code></a> option. Or, you might have to make some changes to your options - to simplify that process, you can use...</p>
</li>
<li>
<p>🌟 TOML option overrides! This provides much greater flexibility in configuration via pyproject.toml. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/854">#854</a>)</p>
<p>You can now set build options for any subset of your builds using a match pattern. So, for example, you can customise CPython 3.8 builds with an override on <code>cp38-*</code> or musllinux builds by selecting <code>*musllinux*</code>. Check out <a href="https://cibuildwheel.readthedocs.io/en/latest/options/#overrides">the docs</a> for more info on the specifics.</p>
</li>
<li>
<p>🛠 Added support for building PyPy wheels on macOS 11 CI runners. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/875">#875</a>)</p>
</li>
<li>
<p>🛠 Setting an empty string for the <a href="https://cibuildwheel.readthedocs.io/en/stable/options/#manylinux-image"><code>CIBW_*_IMAGE</code></a> option will now fallthrough to the config file or cibuildwheel's default, rather than causing an error. This makes the option easier to use in CI build matricies. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/829">#829</a>)</p>
</li>
<li>
<p>🛠 Support for TOML 1.0 when reading config files, via the <code>tomli</code> package. (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/876">#876</a>)</p>
</li>
</ul>
<p><!-- raw HTML omitted -->Note: This version is not available on PyPI due to some missing resources in the release files. Please use a later version instead.<!-- raw HTML omitted --></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2f4987f</code></a> Bump version: v2.2.2</li>
<li><a href=""><code>8a45128</code></a> fix: missing s in action (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/895">#895</a>)</li>
<li><a href=""><code>578098a</code></a> Bump version: v2.2.1</li>
<li><a href=""><code>b31559f</code></a> Update release steps in docs</li>
<li><a href=""><code>90024de</code></a> Bump version: v2.2.1b1</li>
<li><a href=""><code>bc3d3d1</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/894">#894</a> from henryiii/henryiii/ci/release</li>
<li><a href=""><code>88c8e5c</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/893">#893</a> from henryiii/henryiii/fix/manifest</li>
<li><a href=""><code>a1342c1</code></a> ci: release to PyPI from CI on GitHub Release</li>
<li><a href=""><code>0bfbd5b</code></a> fix: produce working SDists</li>
<li><a href=""><code>4515cd2</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="https://github-redirect.dependabot.com/pypa/cibuildwheel/issues/890">#890</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v2.1.3...v2.2.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=2.1.3&new-version=2.2.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `167680b35f0d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.