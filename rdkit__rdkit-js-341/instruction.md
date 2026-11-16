# Issue

**Title:** Bump tslib from 2.5.0 to 2.5.2

## Description

Bumps [tslib](https://github.com/Microsoft/tslib) from 2.5.0 to 2.5.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Microsoft/tslib/releases">tslib's releases</a>.</em></p>
<blockquote>
<h2>tslib 2.5.2</h2>
<p>This release <a href="">explicitly re-exports helpers</a> to work around TypeScript's incomplete symbol resolution for tslib.</p>
<h2>tslib 2.5.1</h2>
<p>This release of tslib provides fixes for two issues.</p>
<p>First, <a href="">it reverses the order of <code>init</code> hooks provided by decorators</a> to correctly reflect proposed behavior.</p>
<p>Second, it <a href="">corrects the <code>exports</code> field of tslib's <code>package.json</code> and provides accurate declaration files</a> so that it may be consumed under the <code>node16</code> and <code>bundler</code> settings for <code>moduleResolution.</code></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e623061</code></a> Bump version to 2.5.2.</li>
<li><a href=""><code>2b57a92</code></a> Use named reexport to satsify incomplete TS symbol resolution (<a href="">#204</a>)</li>
<li><a href=""><code>91fcbd0</code></a> Reverse order of decorator-injected initializers (<a href="">#202</a>)</li>
<li><a href=""><code>eab3cff</code></a> Merge pull request <a href="">#200</a> from Andarist/fix/import-types</li>
<li><a href=""><code>5ef7d1a</code></a> Update modules/index.d.ts</li>
<li><a href=""><code>7def846</code></a> Merge pull request <a href="">#201</a> from microsoft/fix-esm</li>
<li><a href=""><code>4e79d03</code></a> Merge pull request <a href="">#179</a> from guybedford/patch-4</li>
<li><a href=""><code>033b363</code></a> Add default export to modules/index.js</li>
<li><a href=""><code>897f11e</code></a> Ensure tslib.es6.js is typed</li>
<li><a href=""><code>a0a67d9</code></a> Add Node-specific export condition for ESM entrypoint that re-exports CJS</li>
<li>Additional commits viewable in <a href="https://github.com/Microsoft/tslib/compare/2.5.0...2.5.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=tslib&package-manager=npm_and_yarn&previous-version=2.5.0&new-version=2.5.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c89c0b46fe8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.