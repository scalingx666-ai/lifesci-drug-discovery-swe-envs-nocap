# Issue

**Title:** Bump actions/checkout from 4.1.7 to 4.2.2

## Description

Bumps [actions/checkout](https://github.com/actions/checkout) from 4.1.7 to 4.2.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/releases">actions/checkout's releases</a>.</em></p>
<blockquote>
<h2>v4.2.2</h2>
<h2>What's Changed</h2>
<ul>
<li><code>url-helper.ts</code> now leverages well-known environment variables by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1941</a></li>
<li>Expand unit test coverage for <code>isGhes</code> by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1946</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v4.2.1...v4.2.2">https://github.com/actions/checkout/compare/v4.2.1...v4.2.2</a></p>
<h2>v4.2.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Check out other refs/* by commit if provided, fall back to ref by <a href="https://github.com/orhantoy"><code>@​orhantoy</code></a> in <a href="">actions/checkout#1924</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Jcambass"><code>@​Jcambass</code></a> made their first contribution in <a href="">actions/checkout#1919</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v4.2.0...v4.2.1">https://github.com/actions/checkout/compare/v4.2.0...v4.2.1</a></p>
<h2>v4.2.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add Ref and Commit outputs by <a href="https://github.com/lucacome"><code>@​lucacome</code></a> in <a href="">actions/checkout#1180</a></li>
<li>Dependabot updates in <a href="">actions/checkout#1777</a> &amp; <a href="">actions/checkout#1872</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/yasonk"><code>@​yasonk</code></a> made their first contribution in <a href="">actions/checkout#1869</a></li>
<li><a href="https://github.com/lucacome"><code>@​lucacome</code></a> made their first contribution in <a href="">actions/checkout#1180</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v4.1.7...v4.2.0">https://github.com/actions/checkout/compare/v4.1.7...v4.2.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>11bd719</code></a> Prepare 4.2.2 Release (<a href="">#1953</a>)</li>
<li><a href=""><code>e3d2460</code></a> Expand unit test coverage (<a href="">#1946</a>)</li>
<li><a href=""><code>163217d</code></a> <code>url-helper.ts</code> now leverages well-known environment variables. (<a href="">#1941</a>)</li>
<li><a href=""><code>eef6144</code></a> Prepare 4.2.1 release (<a href="">#1925</a>)</li>
<li><a href=""><code>6b42224</code></a> Add workflow file for publishing releases to immutable action package (<a href="">#1919</a>)</li>
<li><a href=""><code>de5a000</code></a> Check out other refs/* by commit if provided, fall back to ref (<a href="">#1924</a>)</li>
<li><a href=""><code>d632683</code></a> Prepare 4.2.0 release (<a href="">#1878</a>)</li>
<li><a href=""><code>6d193bf</code></a> Bump braces from 3.0.2 to 3.0.3 (<a href="">#1777</a>)</li>
<li><a href=""><code>db0cee9</code></a> Bump the minor-npm-dependencies group across 1 directory with 4 updates (<a href="">#1872</a>)</li>
<li><a href=""><code>b684943</code></a> Add Ref and Commit outputs (<a href="">#1180</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/checkout/compare/v4.1.7...v4.2.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/checkout&package-manager=github_actions&previous-version=4.1.7&new-version=4.2.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16ff94ade86e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.