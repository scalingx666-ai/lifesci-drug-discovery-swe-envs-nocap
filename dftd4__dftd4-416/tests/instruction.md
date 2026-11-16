# Issue

**Title:** Bump fortran-lang/setup-fpm from 10 to 11

## Description

Bumps [fortran-lang/setup-fpm](https://github.com/fortran-lang/setup-fpm) from 10 to 11.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fortran-lang/setup-fpm/releases">fortran-lang/setup-fpm's releases</a>.</em></p>
<blockquote>
<h2>v11: build from source on Linux arm64</h2>
<h2>What's Changed</h2>
<ul>
<li>Build from source on Linux ARM64 too by <a href="https://github.com/kunalKumar-13"><code>@​kunalKumar-13</code></a> in <a href="">fortran-lang/setup-fpm#61</a></li>
<li>CI: replace retired macos-14 runner with macos-26 by <a href="https://github.com/perazz"><code>@​perazz</code></a> in <a href="">fortran-lang/setup-fpm#63</a></li>
<li>Prepare v11 release by <a href="https://github.com/perazz"><code>@​perazz</code></a> in <a href="">fortran-lang/setup-fpm#62</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/kunalKumar-13"><code>@​kunalKumar-13</code></a> made their first contribution in <a href="">fortran-lang/setup-fpm#61</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/fortran-lang/setup-fpm/compare/v10...v11">https://github.com/fortran-lang/setup-fpm/compare/v10...v11</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bccff8c</code></a> Prepare v11 release (<a href="">#62</a>)</li>
<li><a href=""><code>a85db46</code></a> Prepare v11 release</li>
<li><a href=""><code>24657ac</code></a> CI: replace retired macos-14 runner with macos-26 (<a href="">#63</a>)</li>
<li><a href=""><code>2723526</code></a> CI: replace retired macos-14 runner with macos-26</li>
<li><a href=""><code>eef8f4a</code></a> Build from source on Linux ARM64 too (<a href="">#61</a>)</li>
<li><a href=""><code>ed81f38</code></a> Run every fpm version on linux-arm64 too</li>
<li><a href=""><code>04877c7</code></a> Address review: fold the arm64 job into the matrix, drop the platform gate</li>
<li><a href=""><code>94a9f74</code></a> Build from source on Linux ARM64 too</li>
<li>See full diff in <a href="https://github.com/fortran-lang/setup-fpm/compare/v10...v11">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=fortran-lang/setup-fpm&package-manager=github_actions&previous-version=10&new-version=11)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1107ea7c7c21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.