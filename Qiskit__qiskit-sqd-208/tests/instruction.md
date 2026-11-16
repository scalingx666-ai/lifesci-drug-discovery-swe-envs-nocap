# Issue

**Title:** Bump pylint from 3.3.6 to 3.3.7

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 3.3.6 to 3.3.7.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f798a4a</code></a> Bump pylint to 3.3.7, update changelog (<a href="">#10367</a>)</li>
<li><a href=""><code>f9773de</code></a> Consistency between  <code>is</code>/<code>is not</code> and <code>==</code>/<code>!=</code> when comparing types...</li>
<li><a href=""><code>0533111</code></a> [fix] Fix a crash for class decorators mistaken for class attributes (<a href="">#10362</a>)...</li>
<li><a href=""><code>887b1b6</code></a> [fix] AttributeError crash when a slice is used as a class decorator (<a href="">#10350</a>)...</li>
<li><a href=""><code>6a02395</code></a> [maintenance/3.3.x] Fix doc build (<a href="">#10336</a>)</li>
<li><a href=""><code>e87d10c</code></a> added black's github link in tutorial (<a href="">#10303</a>) (<a href="">#10335</a>)</li>
<li><a href=""><code>59d4c26</code></a> Fix typo in missing-member-hint-distance documentation (<a href="">#10314</a>) (<a href="">#10315</a>)</li>
<li><a href=""><code>46460d8</code></a> [setuptools] Force the upgrade of setuptools &gt; 77 (<a href="">#10313</a>)</li>
<li><a href=""><code>5b2aa6c</code></a> Speed up the generation of no-member suggestions (<a href="">#10277</a>) (<a href="">#10311</a>)</li>
<li><a href=""><code>744ba53</code></a> Fix crash caused by invalid format strings in <code>.format</code> context (<a href="">#10300</a>) (<a href="">#10</a>...</li>
<li>See full diff in <a href="https://github.com/pylint-dev/pylint/compare/v3.3.6...v3.3.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=3.3.6&new-version=3.3.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3898f82c7ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.