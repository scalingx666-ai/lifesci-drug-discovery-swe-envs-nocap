# Issue

**Title:** Bump pylint from 3.3.7 to 3.3.8

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 3.3.7 to 3.3.8.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>98942ba</code></a> Bump pylint to 3.3.8, update changelog (<a href="">#10486</a>)</li>
<li><a href=""><code>6a1620a</code></a> Update pytest-benchmark requirement from ~=4.0 to ~=5.1 (<a href="">#10066</a>) (<a href="">#10484</a>)</li>
<li><a href=""><code>cef60cc</code></a> Fix false-negative for used-before-assignment with postponed evaluation in fu...</li>
<li><a href=""><code>5a5a9be</code></a> Fix <code>unused-variable</code> false positive when using same name for multiple except...</li>
<li><a href=""><code>6ec71ba</code></a> Respect docstring-min-length in docparams extension (<a href="">#10104</a>) (<a href="">#10434</a>)</li>
<li><a href=""><code>fbde890</code></a> Fix Mermaid printer rendering double underscores as bold formatting (<a href="">#10403</a>) ...</li>
<li><a href=""><code>51234e5</code></a> Fix Pyreverse: Aggregations aren't filtered according to filter mode (PUB_ONL...</li>
<li><a href=""><code>329c967</code></a> Use custom Github App to authenticate backport job (<a href="">#10394</a>) (<a href="">#10396</a>)</li>
<li><a href=""><code>7038ef4</code></a> [Backport maintenance/3.3.x] Resolve possibly-used-before-assignment false po...</li>
<li><a href=""><code>045f179</code></a> Resolve <code>possibly-used-before-assignment</code> false positives from <code>match</code> block ...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v3.3.7...v3.3.8">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=3.3.7&new-version=3.3.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a3db29ad59d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.