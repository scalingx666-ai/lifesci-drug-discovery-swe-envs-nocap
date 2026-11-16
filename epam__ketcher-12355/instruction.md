# Issue

**Title:** chore(deps): bump next from 16.3.8 to 16.4.1

## Description

Bumps [next](https://github.com/vercel/next.js) from 16.3.8 to 16.4.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/next.js/releases">next's releases</a>.</em></p>
<blockquote>
<h2>v16.4.1</h2>
<p>This release contains security fixes for the following advisories:</p>
<p>Critical:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-673q-mjm6-r5xr">Unauthenticated Remote Code Execution in <code>use cache</code> functions returning typed arrays</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-2464-fhr4-w9xw">Unauthenticated Remote Code Execution in Image Optimization API when SVG files are used</a></li>
</ul>
<p>High:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-p3m5-59mp-jv5r">Denial of Service in App Router using Server Actions</a></li>
</ul>
<h2>v16.4.0</h2>
<p>Check out the <a href="https://nextjs.org/blog/next-16-4">16.4 announcement post</a> to get an overview of the changes.</p>
<h3>Core Changes</h3>
<ul>
<li>Show compiler plugin warning in more situations: <a href="">#75682</a></li>
<li>fix(scripts): correct typo in rm.mjs error message: <a href="">#87015</a></li>
<li>docs: improve clarity and punctuation in README: <a href="">#86096</a></li>
<li>Fix debug build paths Pages Router support entries: <a href="">#93529</a></li>
<li>bundle-analyzer: record historical snapshots on each analyze run: <a href="">#93520</a></li>
<li>fix: detect proxy.ts correctly with compound pageExtensions: <a href="">#93246</a></li>
<li>feat(turbopack): support <code>false</code> values for <code>resolveAlias</code> config: <a href="">#93331</a></li>
</ul>
<h3>Misc Changes</h3>
<ul>
<li>docs: correction to dynamicParams migration: <a href="">#96624</a></li>
<li>docs: proxy event argument: <a href="">#96435</a></li>
<li>docs: remove experimental note from runtime prefetching: <a href="">#96615</a></li>
<li>Preserve per-segment prefetching after dynamic navigation: <a href="">#96583</a></li>
<li>Rename static generation stream option to waitForAllReady: <a href="">#96564</a></li>
<li>Remove obsolete static generation plumbing: <a href="">#96563</a></li>
<li>[turbopack] Drop dead writes to <code>exports</code>: <a href="">#96381</a></li>
<li>[turbopack] Ignore writes to <code>exports</code> after a <code>module.exports = {}</code> writes: <a href="">#96380</a></li>
<li>[turbopack] Add test for sideEffects with optimizePackageImports: <a href="">#96549</a></li>
<li>[turbopack] Strip leading BOM before parsing CSS: <a href="">#96678</a></li>
<li>Upgrade React from <code>cbb046ab-20260731</code> to <code>7dfc7ccd-20260803</code>: <a href="">#96550</a></li>
<li>docs: use relative doc links in instant-navigation error pages: <a href="">#96672</a></li>
<li>Turbopack: terminate failed plugin worker threads: <a href="">#96592</a></li>
<li>Fix HTML-limited bot matching in prerender bypass rules: <a href="">#96584</a></li>
<li>[ci] Fix create_release_branch for new repo permissions: <a href="">#96641</a></li>
<li>test: skip action module instance deploy test: <a href="">#96629</a></li>
<li>docs: quote the dynamicParams build error in a blockquote: <a href="">#96633</a></li>
<li>[react-sync] Open pull requests as the bot that authors the commits: <a href="">#96682</a></li>
<li>[Bench] Fixes for pure Fizz bench: <a href="">#96771</a></li>
<li>Derive foreground cache revalidation from the consumer: <a href="">#96731</a></li>
<li>Fix race when navigating Back before hydration: <a href="">#96252</a></li>
<li>docs: present each Skill as steps in the AI agents guide: <a href="">#96751</a></li>
<li>Reuse completed cache entries for the rest of a request: <a href="">#96727</a></li>
<li>Upgrade React from <code>7dfc7ccd-20260803</code> to <code>11eddecd-20260805</code>: <a href="">#96735</a></li>
<li>Remove WorkStore execution mode: <a href="">#96674</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7217011</code></a> v16.4.1</li>
<li><a href=""><code>1798e42</code></a> [cd] Allow branch to get published</li>
<li><a href=""><code>9571ec8</code></a> [lts-active][next/image] Bump <code>sharp</code> (<a href="">#234</a>)</li>
<li><a href=""><code>a4cea6a</code></a> [lts-active][react] Improve Server Component transport protocol (<a href="">#193</a>)</li>
<li><a href=""><code>8df0d97</code></a> [lts-active][test] Backport various deploy test fixes (<a href="">#100114</a>)</li>
<li><a href=""><code>ac9afcc</code></a> [lts-active] Fix google tag manager e2e test, assume GTM 200s instead of 404i...</li>
<li><a href=""><code>e273d5b</code></a> v16.4.0</li>
<li><a href=""><code>fdf41d6</code></a> [ai-upgrade] discover upgrade models and reasoning efforts from agent CLIs (#...</li>
<li><a href=""><code>c3e76ad</code></a> v16.4.0-canary.63</li>
<li><a href=""><code>47c6cc8</code></a> Document next analyze export in the package bundling guide (<a href="">#99735</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/next.js/compare/v16.3.8...v16.4.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=next&package-manager=npm_and_yarn&previous-version=16.3.8&new-version=16.4.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/ketcher/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `827b0196f501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.