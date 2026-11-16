# Issue

**Title:** Bump vite from 3.1.8 to 3.2.0

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.1.8 to 3.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/releases">vite's releases</a>.</em></p>
<blockquote>
<h2>create-vite@3.2.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/create-vite@3.2.0/packages/create-vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2>3.2.0 (2022-10-26)</h2>
<h3>Main Changes</h3>
<h4>Multiple Entries for Library Mode</h4>
<p>Library mode now supports multiple entries:</p>
<pre lang="js"><code>  lib: {
    entry: {
        primary: 'src/index.ts',
        secondary: 'src/secondary.ts'
    },
    formats: ['es', 'cjs']
  }
  // =&gt; primary.es.js, primary.cjs.js, secondary.es.js, secondary.cjs.js
</code></pre>
<p>Check out the PR <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/7047">#7047</a>, and the <a href="https://main.vitejs.dev/config/build-options.html#build-lib"><code>build.lib</code> config docs</a></p>
<h4><code>build.modulePreload</code> options</h4>
<p>Vite now allows filtering and modifying module preload dependencies for each entry and async chunk. <a href="https://vitejs.dev/guide/build.html#advanced-base-options"><code>experimental.renderBuiltUrl</code></a> will also get called for preload asset paths. And <code>build.modulePreload.resolveDependencies</code> will be called both for JS dynamic imports preload lists and also for HTML preload lists for chunks imported from entry HTML files. Refer to the PR for more context <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9938">#9938</a> and check out the <a href="https://vitejs.dev/config/build-options.html#build-modulepreload">modulePreload config docs</a>. Note: <code>build.modulePreloadPolyfill</code> is now deprecated, please migrate to <code>build.modulePreload.polyfill</code>.</p>
<h4>Include Duplicate Assets in the Manifest</h4>
<p>Laravel and other backends integrations will now get entries for every asset file, even if they have been de-duplicated. See <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9928">#9928</a> for more information.</p>
<h4>Customizable ErrorOverlay</h4>
<p>You can now customize the ErrorOverlay by using <a href="https://github.com/vitejs/vite/blob/main/packages/vite/developer.mozilla.org/en-US/docs/Web/CSS/::part">css parts</a>. Check out the PR for more details: <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10234">#10234</a>.</p>
<h3>Features</h3>
<ul>
<li>feat(build): experimental copyPublicDir option (<a href="">#10550</a>) (<a href="">4f4a39f</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10550">#10550</a></li>
<li>feat(css): export preprocessCSS API (<a href="">#10429</a>) (<a href="">177b427</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10429">#10429</a></li>
<li>feat(preview): support outDir option (<a href="">#10418</a>) (<a href="">15b90b3</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10418">#10418</a></li>
<li>feat: include line and column in error format (<a href="">#10529</a>) (<a href="">d806c4a</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10529">#10529</a></li>
<li>feat: reuse opening tab in chromium browsers when start dev server (<a href="">#10485</a>) (<a href="">1a2e7a8</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10485">#10485</a></li>
<li>feat: update esbuild compilation affecting fields (<a href="">#10374</a>) (<a href="">f542727</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10374">#10374</a></li>
<li>feat(proxy): Include URL of request in proxy errors (<a href="">#10508</a>) (<a href="">27e2832</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10508">#10508</a></li>
<li>refactor: delete dependent pre built proxy modules (<a href="">#10427</a>) (<a href="">b3b388d</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10427">#10427</a></li>
<li>feat(server): invalidate module with hmr (<a href="">#10333</a>) (<a href="">8328011</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10333">#10333</a></li>
<li>feat: build.modulePreload options (<a href="">#9938</a>) (<a href="">e223f84</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9938">#9938</a></li>
<li>feat: customize ErrorOverlay (<a href="">#10234</a>) (<a href="">fe4dc8d</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10234">#10234</a></li>
<li>feat: dynamic import support ?url and ?worker (<a href="">#8261</a>) (<a href="">0cb01ca</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/8261">#8261</a></li>
<li>feat: include duplicate assets in the manifest (<a href="">#9928</a>) (<a href="">42ecf37</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9928">#9928</a></li>
<li>feat: support import.meta.hot.invalidate (<a href="">#10244</a>) (<a href="">fb8ab16</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10244">#10244</a></li>
<li>feat: support postcss sugarss (<a href="">#6705</a>) (<a href="">8ede2f1</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/6705">#6705</a></li>
<li>feat(assets): allow <code>new URL</code> to resolve package assets (<a href="">#7837</a>) (<a href="">bafccf5</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/7837">#7837</a></li>
<li>feat(client): add data-vite-dev-id attribute to style elements (<a href="">#10080</a>) (<a href="">ea09fde</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10080">#10080</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4198e34</code></a> release: v3.2.0</li>
<li><a href=""><code>f7021e3</code></a> fix(config): resolve build options with fallback (<a href="">#10645</a>)</li>
<li><a href=""><code>bb95467</code></a> fix(deps): update all non-major dependencies (<a href="">#10610</a>)</li>
<li><a href=""><code>177b427</code></a> feat(css): export preprocessCSS API (<a href="">#10429</a>)</li>
<li><a href=""><code>4f4a39f</code></a> feat(build): experimental copyPublicDir option (<a href="">#10550</a>)</li>
<li><a href=""><code>15b90b3</code></a> feat(preview): support outDir option (<a href="">#10418</a>)</li>
<li><a href=""><code>ee7c28a</code></a> fix(hmr): cannot reload after missing import on server startup (<a href="">#9534</a>) (<a href="">#10602</a>)</li>
<li><a href=""><code>df86990</code></a> fix: when the file path is an absolute path, parsing causes parameter loss (#...</li>
<li><a href=""><code>9f268da</code></a> fix: add a warning if css urls not exist during build time (fix <a href="">#9800</a>) (<a href="">#10331</a>)</li>
<li><a href=""><code>cffe5c9</code></a> fix: revert es-module-lexer version (<a href="">#10614</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vitejs/vite/commits/create-vite@3.2.0/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.1.8&new-version=3.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b82e6deffeb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.