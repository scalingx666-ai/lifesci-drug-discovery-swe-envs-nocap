# Issue

**Title:** Bump prettier from 2.7.0 to 2.7.1

## Description

Bumps [prettier](https://github.com/prettier/prettier) from 2.7.0 to 2.7.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/releases">prettier's releases</a>.</em></p>
<blockquote>
<h2>2.7.1</h2>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#271">Changelog</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md">prettier's changelog</a>.</em></p>
<blockquote>
<h1>2.7.1</h1>
<p><a href="https://github.com/prettier/prettier/compare/2.7.0...2.7.1">diff</a></p>
<h4>Keep useful empty lines in description (<a href="https://github-redirect.dependabot.com/prettier/prettier/pull/13013">#13013</a> by <a href="https://github.com/chimurai"><code>@​chimurai</code></a>)</h4>
<!-- raw HTML omitted -->
<pre lang="graphql"><code># Input
&quot;&quot;&quot;
First line
<p>Second Line
&quot;&quot;&quot;
type Person {
name: String
}
</code></pre></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eeed611</code></a> Release 2.7.1</li>
<li><a href=""><code>794d9d1</code></a> bugfix(graphql): Keep useful empty lines in description (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/13013">#13013</a>)</li>
<li><a href=""><code>dd2af6f</code></a> Fix <code>--skip-dependencies-install</code></li>
<li><a href=""><code>b21772b</code></a> Allow skip depencies install &amp; set repo</li>
<li><a href=""><code>5530ad2</code></a> Merge branch 'main' of github.com:prettier/prettier</li>
<li><a href=""><code>c7c9930</code></a> Clean changelog</li>
<li><a href=""><code>448786f</code></a> Revert changes in release script</li>
<li><a href=""><code>6b388fa</code></a> Add truncate</li>
<li><a href=""><code>109333a</code></a> Git blame ignore 2.7.0</li>
<li><a href=""><code>59ec4f2</code></a> Bump Prettier dependency to 2.7.0</li>
<li>Additional commits viewable in <a href="https://github.com/prettier/prettier/compare/2.7.0...2.7.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=prettier&package-manager=npm_and_yarn&previous-version=2.7.0&new-version=2.7.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c11b07b353b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.