# Issue

**Title:** Bump dparse from 0.5.1 to 0.5.2

## Description

Bumps [dparse](https://github.com/pyupio/dparse) from 0.5.1 to 0.5.2.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pyupio/dparse/blob/master/HISTORY.rst">dparse's changelog</a>.</em></p>
<blockquote>
<h2>0.5.2 (2022-08-09)</h2>
<ul>
<li>Install pyyaml only when asked for with extras (conda extra)</li>
<li>Add support for piptools requirements.in</li>
<li>Use ConfigParser directly</li>
<li>Removed a regex used in the index server validation, fixing a possible ReDos security issue</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2bcf15b</code></a> Fixing rst issue</li>
<li><a href=""><code>aa53997</code></a> Fixing travis file</li>
<li><a href=""><code>13934e1</code></a> Release 0.5.2</li>
<li><a href=""><code>125beef</code></a> Adding pyyaml to tests, now pyyaml is an extra</li>
<li><a href=""><code>b18762f</code></a> Adding conda extra, pyyaml won't be installed by default.</li>
<li><a href=""><code>69ba6dc</code></a> Updapting travis importlib_metadata</li>
<li><a href=""><code>8c99017</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pyupio/dparse/issues/57">#57</a> from pyupio/security/remove-intensive-regex</li>
<li><a href=""><code>d87364f</code></a> Removing index server validation</li>
<li><a href=""><code>3290bb5</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pyupio/dparse/issues/53">#53</a> from oz123/local-import-yaml</li>
<li><a href=""><code>5a3ad57</code></a> Local import YAML instead of top level</li>
<li>Additional commits viewable in <a href="https://github.com/pyupio/dparse/compare/0.5.1...0.5.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=dparse&package-manager=pip&previous-version=0.5.1&new-version=0.5.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/AstraZeneca/kallisto/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16a4b5c3c835`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.