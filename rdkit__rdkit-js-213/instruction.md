# Issue

**Title:** Bump vue-tsc from 1.0.7 to 1.0.8

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/vue-language-tools/vue-tsc) from 1.0.7 to 1.0.8.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.0.8 (2022/10/15)</h2>
<ul>
<li>feat: support for twoslash queries (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar-plugins/issues/9">johnsoncodehk/volar-plugins#9</a>)</li>
<li>feat: support <code>generic</code> attribute auto-complete</li>
<li>feat: add <code>volar.vueserver.noProjectReferences</code> setting for support jump to source files from reference projects (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1344">#1344</a>)</li>
<li>fix: SFC parse failed if script content including <code>&lt;script&gt;</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1982">#1982</a>)</li>
<li>fix: avoid report type error for invalid component without enable <code>jsxTemplates</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2007">#2007</a>)</li>
<li>fix: intrinsic tag highlight should only including open tag and close tag (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2009">#2009</a>)</li>
<li>fix: component type should take capitalize property takes precedence over camelize property from context (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2010">#2010</a>)</li>
<li>fix: references codeLens should not including sources on display (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1989#issuecomment-1277585337">johnsoncodehk/volar#1989</a>)</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>10d1a6a</code></a> v1.0.8</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v1.0.8/vue-language-tools/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=1.0.7&new-version=1.0.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2290290fd76c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.