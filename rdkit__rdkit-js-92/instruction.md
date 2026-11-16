# Issue

**Title:** Bump react from 18.0.0 to 18.1.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [react](https://github.com/facebook/react/tree/HEAD/packages/react) from 18.0.0 to 18.1.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/releases">react's releases</a>.</em></p>
<blockquote>
<h2>18.1.0 (April 26, 2022)</h2>
<h3>React DOM</h3>
<ul>
<li>Fix the false positive warning about <code>react-dom/client</code> when using UMD bundle. (<a href="https://github.com/alireza-molaee"><code>@​alireza-molaee</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24274">#24274</a>)</li>
<li>Fix <code>suppressHydrationWarning</code> to work in production too. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24271">#24271</a>)</li>
<li>Fix <code>componentWillUnmount</code> firing twice inside of Suspense. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24308">#24308</a>)</li>
<li>Fix some transition updates being ignored. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24353">#24353</a>)</li>
<li>Fix <code>useDeferredValue</code> causing an infinite loop when passed an unmemoized value. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24247">#24247</a>)</li>
<li>Fix throttling of revealing Suspense fallbacks. (<a href="https://github.com/sunderls"><code>@​sunderls</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24253">#24253</a>)</li>
<li>Fix an inconsistency in whether the props object is the same between renders. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24421">#24421</a>)</li>
<li>Fix a missing warning about a <code>setState</code> loop in <code>useEffect</code>. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24298">#24298</a>)</li>
<li>Fix a spurious hydration error. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24404">#24404</a>)</li>
<li>Warn when calling <code>setState</code> in <code>useInsertionEffect</code>. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24295">#24295</a>)</li>
<li>Ensure the reason for hydration errors is always displayed. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24276">#24276</a>)</li>
</ul>
<h3>React DOM Server</h3>
<ul>
<li>Fix escaping for the <code>bootstrapScriptContent</code> contents. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24385">#24385</a>)</li>
<li>Significantly improve performance of <code>renderToPipeableStream</code>. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24291">#24291</a>)</li>
</ul>
<h3>ESLint Plugin: React Hooks</h3>
<ul>
<li>Fix false positive errors with a large number of branches. (<a href="https://github.com/scyron6"><code>@​scyron6</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24287">#24287</a>)</li>
<li>Don't consider a known dependency stable when the variable is reassigned. (<a href="https://github.com/afzalsayed96"><code>@​afzalsayed96</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24343">#24343</a>)</li>
</ul>
<h3>Use Subscription</h3>
<ul>
<li>Replace the implementation with the <code>use-sync-external-store</code> shim. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24289">#24289</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/blob/main/CHANGELOG.md">react's changelog</a>.</em></p>
<blockquote>
<h2>18.1.0 (April 26, 2022)</h2>
<h3>React DOM</h3>
<ul>
<li>Fix the false positive warning about <code>react-dom/client</code> when using UMD bundle. (<a href="https://github.com/alireza-molaee"><code>@​alireza-molaee</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24274">#24274</a>)</li>
<li>Fix <code>suppressHydrationWarning</code> to work in production too. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24271">#24271</a>)</li>
<li>Fix <code>componentWillUnmount</code> firing twice inside of Suspense. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24308">#24308</a>)</li>
<li>Fix some transition updates being ignored. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24353">#24353</a>)</li>
<li>Fix <code>useDeferredValue</code> causing an infinite loop when passed an unmemoized value. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24247">#24247</a>)</li>
<li>Fix throttling of revealing Suspense fallbacks. (<a href="https://github.com/sunderls"><code>@​sunderls</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24253">#24253</a>)</li>
<li>Fix an inconsistency in whether the props object is the same between renders. (<a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24421">#24421</a>)</li>
<li>Fix a missing warning about a <code>setState</code> loop in <code>useEffect</code>. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24298">#24298</a>)</li>
<li>Fix a spurious hydration error. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24404">#24404</a>)</li>
<li>Warn when calling <code>setState</code> in <code>useInsertionEffect</code>. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24295">#24295</a>)</li>
<li>Ensure the reason for hydration errors is always displayed. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24276">#24276</a>)</li>
</ul>
<h3>React DOM Server</h3>
<ul>
<li>Fix escaping for the <code>bootstrapScriptContent</code> contents. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24385">#24385</a>)</li>
<li>Significantly improve performance of <code>renderToPipeableStream</code>. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24291">#24291</a>)</li>
</ul>
<h3>ESLint Plugin: React Hooks</h3>
<ul>
<li>Fix false positive errors with a large number of branches. (<a href="https://github.com/scyron6"><code>@​scyron6</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24287">#24287</a>)</li>
<li>Don't consider a known dependency stable when the variable is reassigned. (<a href="https://github.com/afzalsayed96"><code>@​afzalsayed96</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24343">#24343</a>)</li>
</ul>
<h3>Use Subscription</h3>
<ul>
<li>Replace the implementation with the <code>use-sync-external-store</code> shim. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24289">#24289</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>22edb9f</code></a> React <code>version</code> field should match package.json (<a href="">#24445</a>)</li>
<li><a href=""><code>4175f05</code></a> Temporarily feature flag numeric fallback for symbols (<a href="">#24401</a>)</li>
<li><a href=""><code>e8f4a66</code></a> Fix import in example</li>
<li><a href=""><code>bb49abe</code></a> Update some READMEs (<a href="">#24290</a>)</li>
<li><a href=""><code>7e3121e</code></a> Remove unstable_createMutableSource from experimental build (<a href="">#24209</a>)</li>
<li>See full diff in <a href="https://github.com/facebook/react/commits/v18.1.0/packages/react">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=react&package-manager=npm_and_yarn&previous-version=18.0.0&new-version=18.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d28a430a50f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.