# Issue

**Title:** Bump vue-tsc from 0.40.1 to 0.40.4

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.1 to 0.40.4.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.4 (2022/8/29)</h2>
<ul>
<li>feat: respect VSCode <code>*.format.enable</code> settings</li>
<li>fix: template should not compile if content no change</li>
<li>fix: component preview not working on windows (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1737">#1737</a>)</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
<h2>0.40.3 (2022/8/29)</h2>
<ul>
<li>perf: incremental update SFC blocks without full parse SFC and mitigate memory leak</li>
<li>perf: incremental update html template interpolation without recompile template</li>
<li>perf: cache <code>ts.createSourceFile</code> for tsx code gen</li>
<li>fix(vue-component-meta): cannot create checker with TS 4.8.2</li>
<li>fix: document features not working on Web IDE (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1479">#1479</a>)</li>
<li>fix: avoid auto complete triggers too aggressive in Sublime (<a href="https://github-redirect.dependabot.com/sublimelsp/LSP-volar/issues/114">sublimelsp/LSP-volar#114</a>)</li>
</ul>
<h2>0.40.2 (2022/8/28)</h2>
<ul>
<li>feat(vue-component-meta): add <code>createComponentMetaCheckerByJsonConfig</code> API to support create checker without tsconfig</li>
<li>feat: move <code>highlight dom elements ☑</code> codeLens to status bar (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1535">#1535</a>)</li>
<li>feat: incremental update diagnostics cache range and avoid flicker (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1718">#1718</a>)</li>
<li>perf: incremental update TS script snapshot (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1718">#1718</a>)</li>
<li>perf: faster source map code mapping</li>
<li>fix: pug template tag mapping range incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1723">#1723</a>)</li>
<li>fix: vite plugin import path incorrect on windows (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1772">#1772</a>)</li>
<li>fix: false positive error on style attr when enabled <code>compilerOptions.exactOptionalPropertyTypes</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1560">#1560</a>)</li>
<li>fix: .html intellisense of petite-vue not working</li>
<li>fix: .html intellisense of alpie not working</li>
<li>fix: intellisense not working for node_modules files with takeover mode on windows (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1641">#1641</a>)</li>
<li>fix: avoid vue-tsc type check .html, .md files (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1661">#1661</a>)</li>
<li>fix: <code>compilerOptions.types</code> resolve path incorrect on multiple workspaces (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1679">#1679</a>)</li>
<li>fix: cannot count script setup variable usage in template if disalbe jsx (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1729">#1729</a>)</li>
<li>fix: cannot resolve indirect circular reference components types (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1708">#1708</a>)</li>
<li>fix: cannot recognize namespace component (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1726">#1726</a>)</li>
<li>fix: template components types break by regular SFC <code>components</code> option (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1731">#1731</a>)</li>
<li>fix: indentation behavior incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1762">#1762</a>)</li>
<li>fix: TS1308 'async' error missing when use script setup (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1753">#1753</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>018d260</code></a> v0.40.4</li>
<li><a href=""><code>51eca3c</code></a> v0.40.3</li>
<li><a href=""><code>baa87a7</code></a> v0.40.2</li>
<li><a href=""><code>53315dd</code></a> fix(vue-tsc): disable type checking in .html, .md before has option</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.4/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.1&new-version=0.40.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b847b4a582a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.