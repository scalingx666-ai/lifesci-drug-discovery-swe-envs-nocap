# Issue

**Title:** Bump myst-nb from 1.1.2 to 1.2.0

## Description

Bumps [myst-nb](https://github.com/executablebooks/myst-nb) from 1.1.2 to 1.2.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/MyST-NB/blob/master/CHANGELOG.md">myst-nb's changelog</a>.</em></p>
<blockquote>
<h2>v1.2.0 - 2025-02-07</h2>
<p>(<a href="https://github.com/executablebooks/MyST-NB/compare/v1.1.2...v1.2.0">full changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>ENH: Support translated notebooks by <a href="https://github.com/OriolAbril"><code>@​OriolAbril</code></a> in <a href="">executablebooks/MyST-NB#600</a></li>
</ul>
<h3>Bugs Fixed</h3>
<ul>
<li>BUG: using rstrip to preserve indents by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#637</a></li>
<li>FIX: fix path suffix condition in core/read.py by <a href="https://github.com/je-cook"><code>@​je-cook</code></a> in <a href="">executablebooks/MyST-NB#641</a></li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>DOCS: adding changelog for 1.1.2 by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#638</a></li>
<li>MAINT: adding python 3.13 to CI and classifiers by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#635</a></li>
<li>CI: adding devdeps testing and cron and workflow dispatch by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#639</a></li>
<li>TST: fail on warnings by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#647</a></li>
<li>add <code>configuration</code> key to readthedocs.yml by <a href="https://github.com/sneakers-the-rat"><code>@​sneakers-the-rat</code></a> in <a href="">executablebooks/MyST-NB#657</a></li>
<li>MAINT: fix CI in prep for release by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#659</a></li>
</ul>
<h3>Other merged PRs</h3>
<ul>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a> in <a href="">executablebooks/MyST-NB#569</a></li>
<li>Revert &quot;[pre-commit.ci] pre-commit autoupdate&quot; by <a href="https://github.com/agoose77"><code>@​agoose77</code></a> in <a href="">executablebooks/MyST-NB#642</a></li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/sneakers-the-rat"><code>@​sneakers-the-rat</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#657</a></li>
</ul>
<p>(<a href="https://github.com/executablebooks/MyST-NB/graphs/contributors?from=2024-09-24&amp;to=2025-02-07&amp;type=c">GitHub contributors page for this release</a>)</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>27c82f3</code></a> Preparing for v1.2.0 (<a href="">#663</a>)</li>
<li><a href=""><code>9591314</code></a> MAINT: fix CI in prep for release (<a href="">#659</a>)</li>
<li><a href=""><code>305c781</code></a> add configuration to readthedocs.yml (<a href="">#657</a>)</li>
<li><a href=""><code>2cd6874</code></a> TST: fail on warnings (<a href="">#647</a>)</li>
<li><a href=""><code>6ee8d01</code></a> ENH: Support translated notebooks (<a href="">#600</a>)</li>
<li><a href=""><code>72b415f</code></a> FIX: fix path suffix condition in core/read.py (<a href="">#641</a>)</li>
<li><a href=""><code>aee9a46</code></a> CI: adding devdeps testing and cron and workflow dispatch (<a href="">#639</a>)</li>
<li><a href=""><code>8389654</code></a> Revert &quot;[pre-commit.ci] pre-commit autoupdate (<a href="">#569</a>)&quot; (<a href="">#642</a>)</li>
<li><a href=""><code>8d6e25d</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#569</a>)</li>
<li><a href=""><code>83f8d1b</code></a> MAINT: adding python 3.13 to CI and classifiers (<a href="">#635</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/executablebooks/myst-nb/compare/v1.1.2...v1.2.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=myst-nb&package-manager=pip&previous-version=1.1.2&new-version=1.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61eb5515df90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.