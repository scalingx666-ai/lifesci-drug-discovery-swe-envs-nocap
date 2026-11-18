# Issue

**Title:** chore(deps-dev): bump preact from 10.26.5 to 10.28.2

## Description

Bumps [preact](https://github.com/preactjs/preact) from 10.26.5 to 10.28.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/preactjs/preact/releases">preact's releases</a>.</em></p>
<blockquote>
<h2>10.28.2</h2>
<h2>Fixes</h2>
<ul>
<li>Enforce strict equality for VNode object constructors</li>
</ul>
<h2>10.28.1</h2>
<h2>Fixes</h2>
<ul>
<li>Fix erroneous diffing w/ growing list (<a href="">#4975</a>, thanks <a href="https://github.com/JoviDeCroock"><code>@​JoviDeCroock</code></a>)</li>
</ul>
<h2>10.28.0</h2>
<h2>Types</h2>
<ul>
<li>Updates dangerouslySetInnerHTML type so future TS will accept Trusted… (<a href="">#4931</a>, thanks <a href="https://github.com/lukewarlow"><code>@​lukewarlow</code></a>)</li>
<li>Adds snap events (<a href="">#4947</a>, thanks <a href="https://github.com/argyleink"><code>@​argyleink</code></a>)</li>
<li>Remove missed jsx duplicates (<a href="">#4950</a>, thanks <a href="https://github.com/rschristian"><code>@​rschristian</code></a>)</li>
<li>Fix scroll events (<a href="">#4949</a>, thanks <a href="https://github.com/rschristian"><code>@​rschristian</code></a>)</li>
</ul>
<h2>Fixes</h2>
<ul>
<li>Fix cascading renders with signals (<a href="">#4966</a>, thanks <a href="https://github.com/JoviDeCroock"><code>@​JoviDeCroock</code></a>)</li>
<li>add <code>commpat/server.browser</code> entry (<a href="">#4941</a> &amp; <a href="">#4940</a>, thanks <a href="https://github.com/marvinhagemeister"><code>@​marvinhagemeister</code></a>)</li>
<li>Avoid lazy components without result going in throw loop (<a href="">#4937</a>, thanks <a href="https://github.com/JoviDeCroock"><code>@​JoviDeCroock</code></a>)</li>
</ul>
<h2>Performance</h2>
<ul>
<li>Backport some v11 optimizations (<a href="">#4967</a>, thanks <a href="https://github.com/JoviDeCroock"><code>@​JoviDeCroock</code></a>)</li>
</ul>
<h2>10.27.3</h2>
<h2>Fixes</h2>
<ul>
<li>Enforce strict equality for VNode object constructors</li>
</ul>
<h2>10.27.2</h2>
<h2>Types</h2>
<ul>
<li>Mirror non-JSX types to the 'preact' namespace (<a href="">#4904</a>, thanks <a href="https://github.com/rschristian"><code>@​rschristian</code></a>)</li>
</ul>
<h2>Fixes</h2>
<ul>
<li>Address memory leak (<a href="">#4906</a>, thanks <a href="https://github.com/JoviDeCroock"><code>@​JoviDeCroock</code></a>)</li>
</ul>
<h2>10.27.1</h2>
<h2>Performance</h2>
<ul>
<li>Avoid re-inserting children during bailout (<a href="">#4890</a>, thanks <a href="https://github.com/vasylenkoval"><code>@​vasylenkoval</code></a>)</li>
</ul>
<h2>Types</h2>
<ul>
<li>add missing React.Key (<a href="">#4864</a>, thanks <a href="https://github.com/shyguy1412"><code>@​shyguy1412</code></a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6f91446</code></a> 10.28.2</li>
<li><a href=""><code>37c3e03</code></a> Strict equality check on constructor (<a href="">#4985</a>)</li>
<li><a href=""><code>6670a4a</code></a> chore: Adjust TS linting setup (<a href="">#4982</a>)</li>
<li><a href=""><code>2af522b</code></a> 10.28.1 (<a href="">#4978</a>)</li>
<li><a href=""><code>f7693b7</code></a> Fix erroneous diffing w/ growing list (<a href="">#4975</a>)</li>
<li><a href=""><code>b36b6a7</code></a> 10.28.0 (<a href="">#4968</a>)</li>
<li><a href=""><code>4d40e96</code></a> Backport some v11 optimizations (<a href="">#4967</a>)</li>
<li><a href=""><code>7b74b40</code></a> Fix cascading renders with signals (<a href="">#4966</a>)</li>
<li><a href=""><code>3ab5c6f</code></a> Updates dangerouslySetInnerHTML type so future TS will accept Trusted… (<a href="">#4931</a>)</li>
<li><a href=""><code>ff30c2b</code></a> Adds snap events (<a href="">#4947</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/preactjs/preact/compare/10.26.5...10.28.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=preact&package-manager=npm_and_yarn&previous-version=10.26.5&new-version=10.28.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `baddafe36bde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.