# Issue

**Title:** Bump pylint from 4.0.5 to 4.0.6

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 4.0.5 to 4.0.6.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8a39635</code></a> Bump pylint to 4.0.6, update changelog (<a href="">#11105</a>)</li>
<li><a href=""><code>150f23c</code></a> [Backport maintenance/4.0.x] Allow digits in ParamSpec and TypeVarTuple names...</li>
<li><a href=""><code>8b6251e</code></a> [Backport maintenance/4.0.x] Fix crash when enum member inference fails (<a href="">#11093</a>)</li>
<li><a href=""><code>d57aadb</code></a> [Backport maintenance/4.0.x] Fix <code>implicit-str-concat</code> false positive for mix...</li>
<li><a href=""><code>d9ea8d9</code></a> [Backport maintenance/4.0.x] Fix <code>unnecessary-comprehension</code> suggestion when ...</li>
<li><a href=""><code>cb1792a</code></a> [Backport maintenance/4.0.x] Allow digits in TypeVar names for invalid-name c...</li>
<li><a href=""><code>ee2ab9a</code></a> Handle InferenceError in decorator return analysis</li>
<li><a href=""><code>5bb5498</code></a> [Backport maintenance/4.0.x] Fix crash in typecheck checker when metaclass ar...</li>
<li><a href=""><code>a940533</code></a> [Backport maintenance/4.0.x] Fix a crash in <code>consider-using-enumerate</code> for no...</li>
<li><a href=""><code>b7a873a</code></a> [Backport maintenance/4.0.x] Fix crash in deprecated checker for non-string `...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v4.0.5...v4.0.6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=4.0.5&new-version=4.0.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4c6eecb292c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.