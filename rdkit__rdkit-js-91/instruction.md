# Issue

**Title:** Bump react-dom from 18.0.0 to 18.1.0

## Description

Bumps [react-dom](https://github.com/facebook/react/tree/HEAD/packages/react-dom) from 18.0.0 to 18.1.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/releases">react-dom's releases</a>.</em></p>
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
<p><em>Sourced from <a href="https://github.com/facebook/react/blob/main/CHANGELOG.md">react-dom's changelog</a>.</em></p>
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
<li><a href=""><code>bd4784c</code></a> Revert <a href="">#24236</a> (Don't recreate the same fallback on the client if hydrating su...</li>
<li><a href=""><code>9ae80d6</code></a> Suppress hydration warnings when a preceding sibling suspends (<a href="">#24404</a>)</li>
<li><a href=""><code>0dc4e66</code></a> Land enableClientRenderFallbackOnHydrationMismatch (<a href="">#24410</a>)</li>
<li><a href=""><code>3547729</code></a> Land enableSelectiveHydration flag (<a href="">#24406</a>)</li>
<li><a href=""><code>392808a</code></a> Land enableClientRenderFallbackOnTextMismatch flag (<a href="">#24405</a>)</li>
<li><a href=""><code>a6d53f3</code></a> Revert &quot;Clean up Selective Hydration / Event Replay flag (<a href="">#24156</a>)&quot; (<a href="">#24402</a>)</li>
<li><a href=""><code>2bf5eba</code></a> explain the rationale for the chosen escaping implemenation in a comment (<a href="">#24</a>...</li>
<li><a href=""><code>d40dc73</code></a> Escape bootstrapScriptContent for javascript embedding into HTML (<a href="">#24385</a>)</li>
<li><a href=""><code>ea7b2ec</code></a> Remove wrong return pointer warning</li>
<li><a href=""><code>8dcedba</code></a> Add fallback shim for AbortController (<a href="">#24285</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/facebook/react/commits/v18.1.0/packages/react-dom">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=react-dom&package-manager=npm_and_yarn&previous-version=18.0.0&new-version=18.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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