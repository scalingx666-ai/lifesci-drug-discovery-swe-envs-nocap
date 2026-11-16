# Issue

**Title:** Bump pylint from 3.3.8 to 4.0.4

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 3.3.8 to 4.0.4.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e16f942</code></a> Bump pylint to 4.0.4, update changelog</li>
<li><a href=""><code>657b386</code></a> [Backport maintenance/4.0.x] [invalid-name] Fix FP for exclusive assignment o...</li>
<li><a href=""><code>03f8a92</code></a> [Backport maintenance/4.0.x] fix: avoid false positive when module-level name...</li>
<li><a href=""><code>84b6552</code></a> Bump pylint to 4.0.3, update changelog (<a href="">#10741</a>)</li>
<li><a href=""><code>77b0cd8</code></a> [Backport maintenance/4.0.x] fix(expand_modules): pass ignore_list to modutil...</li>
<li><a href=""><code>755f2d0</code></a> [Backport maintenance/4.0.x] Upgrade astroid to 4.0.2 (<a href="">#10733</a>)</li>
<li><a href=""><code>c96a9e4</code></a> [Backport maintenance/4.0.x] Fix crash when a variable annotation is used as ...</li>
<li><a href=""><code>108191e</code></a> [Backport maintenance/4.0.x] Fix a false positive for class attribute typed w...</li>
<li><a href=""><code>0ed8172</code></a> [Backport maintenance/4.0.x] Fix crash when a <code>slice</code> object is called (<a href="">#10728</a>)</li>
<li><a href=""><code>b128b7d</code></a> [Backport maintenance/4.0.x] Fix a false positive for ``unbalanced-tuple-unpa...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v3.3.8...v4.0.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=3.3.8&new-version=4.0.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47195febfd0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.