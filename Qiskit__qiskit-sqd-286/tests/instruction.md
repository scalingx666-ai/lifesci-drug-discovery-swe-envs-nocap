# Issue

**Title:** Bump pylint from 4.0.4 to 4.0.5

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 4.0.4 to 4.0.5.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>88e1ab7</code></a> Bump pylint to 4.0.5, update changelog (<a href="">#10860</a>)</li>
<li><a href=""><code>d96d489</code></a> [Backport maintenance/4.0.x] Relax isort version constraint to allow isort 8 ...</li>
<li><a href=""><code>0b08ccb</code></a> Fix dynamic color mapping for &quot;fail-on&quot; messages when using multiple reporter...</li>
<li><a href=""><code>154dba4</code></a> [Backport maintenance/4.0.x] Fix FP for <code>invalid-name</code> with <code>typing.Final</code> on...</li>
<li><a href=""><code>7b73bfd</code></a> Disable unspecified-encoding for py-version above Python 3.15 (<a href="">#10800</a>)</li>
<li><a href=""><code>4cc98be</code></a> [Backport maintenance/4.0.x] Fix setting options for import order checker (<a href="">#1</a>...</li>
<li><a href=""><code>f0d30a2</code></a> Sync astroid version with requirements file again</li>
<li><a href=""><code>38bdf02</code></a> [Backport maintenance/4.0.x] Fix <code>logging-unsupported-format</code> when logging ...</li>
<li><a href=""><code>f08c33a</code></a> [Backport maintenance/4.0.x] Properly detect <code>self.fail()</code> as a terminating...</li>
<li>See full diff in <a href="https://github.com/pylint-dev/pylint/compare/v4.0.4...v4.0.5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=4.0.4&new-version=4.0.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8b5a078cb24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.