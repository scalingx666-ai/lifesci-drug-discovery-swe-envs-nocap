# Issue

**Title:** Bump typedoc from 0.25.1 to 0.25.3

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.25.1 to 0.25.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.25.3</h2>
<h3>Features</h3>
<ul>
<li>Added <code>--sourceLinkExternal</code> option to render source code links as external, <a href="">#2415</a>.</li>
<li>TypeDoc no longer requires the <code>declarationMap</code> option to be set to true to handle cross-package links in packages mode, <a href="">#2416</a>.</li>
<li>Added <code>external-last</code> option for the <code>--sort</code> option, <a href="">#2418</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc now attempts to correct local anchor links in readme files which are broken by its deconfliction logic, <a href="">#2413</a>.</li>
<li>TypeDoc now finds comments on index signatures again, <a href="">#2414</a>.</li>
<li>TypeDoc now does a better job of detecting properties when destructured function arguments are used.</li>
<li>Quotes will now be properly escaped in HTML attribute values.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/mogelbrod"><code>@​mogelbrod</code></a></li>
<li><a href="https://github.com/rsanchez"><code>@​rsanchez</code></a></li>
</ul>
<h2>v0.25.2</h2>
<h3>Features</h3>
<ul>
<li>Added <code>navigationLeaves</code> option to remove branches from the navigation tree, <a href="">#2382</a>.</li>
<li>Added <code>sortEntryPoints</code> option (defaults to true) to allow disabling entry point sorting, <a href="">#2393</a>.</li>
<li>Improved support for multi-word searches, <a href="">#2400</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed conversion of <code>@template</code> constraints on JSDoc defined type parameters, <a href="">#2389</a>.</li>
<li>Invalid link validation is now correctly suppressed before all projects have been converted in packages mode, <a href="">#2403</a>.</li>
<li>Fixed tsconfig handling for projects using a solution-style tsconfig, <a href="">#2406</a>.</li>
<li>Fixed broken settings icons caused by icon caching introduced in 0.25.1, <a href="">#2408</a>.</li>
<li>Corrected module comment handling on declaration files containing a single <code>declare module &quot;foo&quot;</code>, <a href="">#2401</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/schiem"><code>@​schiem</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.25.3 (2023-10-29)</h2>
<h3>Features</h3>
<ul>
<li>Added <code>--sourceLinkExternal</code> option to render source code links as external, <a href="">#2415</a>.</li>
<li>TypeDoc no longer requires the <code>declarationMap</code> option to be set to true to handle cross-package links in packages mode, <a href="">#2416</a>.</li>
<li>Added <code>external-last</code> option for the <code>--sort</code> option, <a href="">#2418</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc now attempts to correct local anchor links in readme files which are broken by its deconfliction logic, <a href="">#2413</a>.</li>
<li>TypeDoc now finds comments on index signatures again, <a href="">#2414</a>.</li>
<li>TypeDoc now does a better job of detecting properties when destructured function arguments are used.</li>
<li>Quotes will now be properly escaped in HTML attribute values.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/mogelbrod"><code>@​mogelbrod</code></a></li>
<li><a href="https://github.com/rsanchez"><code>@​rsanchez</code></a></li>
</ul>
<h2>v0.25.2 (2023-10-08)</h2>
<h3>Features</h3>
<ul>
<li>Added <code>navigationLeaves</code> option to remove branches from the navigation tree, <a href="">#2382</a>.</li>
<li>Added <code>sortEntryPoints</code> option (defaults to true) to allow disabling entry point sorting, <a href="">#2393</a>.</li>
<li>Improved support for multi-word searches, <a href="">#2400</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed conversion of <code>@template</code> constraints on JSDoc defined type parameters, <a href="">#2389</a>.</li>
<li>Invalid link validation is now correctly suppressed before all projects have been converted in packages mode, <a href="">#2403</a>.</li>
<li>Fixed tsconfig handling for projects using a solution-style tsconfig, <a href="">#2406</a>.</li>
<li>Fixed broken settings icons caused by icon caching introduced in 0.25.1, <a href="">#2408</a>.</li>
<li>Corrected module comment handling on declaration files containing a single <code>declare module &quot;foo&quot;</code>, <a href="">#2401</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/schiem"><code>@​schiem</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>839b192</code></a> Update changelog for release</li>
<li><a href=""><code>af2d099</code></a> Bump version to 0.25.3</li>
<li><a href=""><code>57a4b43</code></a> Correctly escape quotes in attributes</li>
<li><a href=""><code>ee58d34</code></a> Add declaration paths to remap cache in packages mode</li>
<li><a href=""><code>7e0b959</code></a> Update changelog</li>
<li><a href=""><code>325233c</code></a> Rename internal-first sort strategy to external-last</li>
<li><a href=""><code>02a14c0</code></a> Add internal-first sort strategy</li>
<li><a href=""><code>d26f553</code></a> Use renderElement for html generation in marked plugin</li>
<li><a href=""><code>b8faaf7</code></a> Update changelog</li>
<li><a href=""><code>5305cbf</code></a> Improve destructured property support</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.25.1...v0.25.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.25.1&new-version=0.25.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `821e49284651`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.