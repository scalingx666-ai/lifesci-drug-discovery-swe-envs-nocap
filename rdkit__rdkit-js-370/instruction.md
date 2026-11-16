# Issue

**Title:** Bump @adobe/css-tools from 4.0.1 to 4.3.1

## Description

Bumps [@adobe/css-tools](https://github.com/adobe/css-tools) from 4.0.1 to 4.3.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/adobe/css-tools/blob/main/History.md"><code>@​adobe/css-tools</code>'s changelog</a>.</em></p>
<blockquote>
<h1>4.3.1 / 2023-03-14</h1>
<ul>
<li>Fix redos vulnerability with specific crafted css string - CVE-2023-26364</li>
</ul>
<h1>4.3.0 / 2023-03-07</h1>
<ul>
<li>Update build tools</li>
<li>Update exports path and files</li>
</ul>
<h1>4.2.0 / 2023-02-21</h1>
<ul>
<li>Add <a href="https://github.com/container"><code>@​container</code></a> support</li>
<li>Add <a href="https://github.com/layer"><code>@​layer</code></a> support</li>
</ul>
<h1>4.1.0 / 2023-01-25</h1>
<ul>
<li>Support ESM Modules</li>
</ul>
<h1>4.0.2 / 2023-01-12</h1>
<ul>
<li><a href="">#71</a> : <a href="https://github.com/import"><code>@​import</code></a> does not work if url contains ';'</li>
<li><a href="">#77</a> : Regression in selector parsing: Attribute selectors not parsed correctly</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/adobe/css-tools/commits">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@adobe/css-tools&package-manager=npm_and_yarn&previous-version=4.0.1&new-version=4.3.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/rdkit/rdkit-js/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9c9f7a144f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.