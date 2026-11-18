# Issue

**Title:** chore(deps): bump webpack from 5.98.0 to 5.105.0 in /frontend

## Description

Bumps [webpack](https://github.com/webpack/webpack) from 5.98.0 to 5.105.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/webpack/webpack/releases">webpack's releases</a>.</em></p>
<blockquote>
<h2>v5.105.0</h2>
<h3>Minor Changes</h3>
<ul>
<li>
<p>Allow resolving worker module by export condition name when using <code>new Worker()</code> (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20353</a>)</p>
</li>
<li>
<p>Detect conditional imports to avoid compile-time linking errors for non-existent exports. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20320</a>)</p>
</li>
<li>
<p>Added the <code>tsconfig</code> option for the <code>resolver</code> options (replacement for <code>tsconfig-paths-webpack-plugin</code>). Can be <code>false</code> (disabled), <code>true</code> (use the default <code>tsconfig.json</code> file to search for it), a string path to <code>tsconfig.json</code>, or an object with <code>configFile</code> and <code>references</code> options. (by <a href="https://github.com/alexander-akait"><code>@​alexander-akait</code></a> in <a href="">#20400</a>)</p>
</li>
<li>
<p>Support <code>import.defer()</code> for context modules. (by <a href="https://github.com/ahabhgk"><code>@​ahabhgk</code></a> in <a href="">#20399</a>)</p>
</li>
<li>
<p>Added support for array values ​​to the <code>devtool</code> option. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20191</a>)</p>
</li>
<li>
<p>Improve rendering node built-in modules for ECMA module output. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20255</a>)</p>
</li>
<li>
<p>Unknown import.meta properties are now determined at runtime instead of being statically analyzed at compile time. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20312</a>)</p>
</li>
</ul>
<h3>Patch Changes</h3>
<ul>
<li>
<p>Fixed ESM default export handling for <code>.mjs</code> files in Module Federation (by <a href="https://github.com/y-okt"><code>@​y-okt</code></a> in <a href="">#20189</a>)</p>
</li>
<li>
<p>Optimized <code>import.meta.env</code> handling in destructuring assignments by using cached stringified environment definitions. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20313</a>)</p>
</li>
<li>
<p>Respect the <code>stats.errorStack</code> option in stats output. (by <a href="https://github.com/samarthsinh2660"><code>@​samarthsinh2660</code></a> in <a href="">#20258</a>)</p>
</li>
<li>
<p>Fixed a bug where declaring a <code>module</code> variable in module scope would conflict with the default <code>moduleArgument</code>. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20265</a>)</p>
</li>
<li>
<p>Fix VirtualUrlPlugin to set resourceData.context for proper module resolution. Previously, when context was not set, it would fallback to the virtual scheme path (e.g., <code>virtual:routes</code>), which is not a valid filesystem path, causing subsequent resolve operations to fail. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20390</a>)</p>
</li>
<li>
<p>Fixed Worker self-import handling to support various URL patterns (e.g., <code>import.meta.url</code>, <code>new URL(import.meta.url)</code>, <code>new URL(import.meta.url, import.meta.url)</code>, <code>new URL(&quot;./index.js&quot;, import.meta.url)</code>). Workers that resolve to the same module are now properly deduplicated, regardless of the URL syntax used. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20381</a>)</p>
</li>
<li>
<p>Reuse the same async entrypoint for the same Worker URL within a module to avoid circular dependency warnings when multiple Workers reference the same resource. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20345</a>)</p>
</li>
<li>
<p>Fixed a bug where a self-referencing dependency would have an unused export name when imported inside a web worker. (by <a href="https://github.com/samarthsinh2660"><code>@​samarthsinh2660</code></a> in <a href="">#20251</a>)</p>
</li>
<li>
<p>Fix missing export generation when concatenated modules in different chunks share the same runtime in module library bundles. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20346</a>)</p>
</li>
<li>
<p>Fixed <code>import.meta.env.xxx</code> behavior: when accessing a non-existent property, it now returns empty object instead of full object at runtime. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20289</a>)</p>
</li>
<li>
<p>Improved parsing error reporting by adding a link to the loader documentation. (by <a href="https://github.com/gaurav10gg"><code>@​gaurav10gg</code></a> in <a href="">#20244</a>)</p>
</li>
<li>
<p>Fix typescript types. (by <a href="https://github.com/alexander-akait"><code>@​alexander-akait</code></a> in <a href="">#20305</a>)</p>
</li>
<li>
<p>Add declaration for unused harmony import specifier. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20286</a>)</p>
</li>
<li>
<p>Fix compressibility of modules while retaining portability. (by <a href="https://github.com/dmichon-msft"><code>@​dmichon-msft</code></a> in <a href="">#20287</a>)</p>
</li>
<li>
<p>Optimize source map generation: only include <code>ignoreList</code> property when it has content, avoiding empty arrays in source maps. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20319</a>)</p>
</li>
<li>
<p>Preserve star exports for dependencies in ECMA module output. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20293</a>)</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/webpack/webpack/blob/main/CHANGELOG.md">webpack's changelog</a>.</em></p>
<blockquote>
<h2>5.105.0</h2>
<h3>Minor Changes</h3>
<ul>
<li>
<p>Allow resolving worker module by export condition name when using <code>new Worker()</code> (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20353</a>)</p>
</li>
<li>
<p>Detect conditional imports to avoid compile-time linking errors for non-existent exports. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20320</a>)</p>
</li>
<li>
<p>Added the <code>tsconfig</code> option for the <code>resolver</code> options (replacement for <code>tsconfig-paths-webpack-plugin</code>). Can be <code>false</code> (disabled), <code>true</code> (use the default <code>tsconfig.json</code> file to search for it), a string path to <code>tsconfig.json</code>, or an object with <code>configFile</code> and <code>references</code> options. (by <a href="https://github.com/alexander-akait"><code>@​alexander-akait</code></a> in <a href="">#20400</a>)</p>
</li>
<li>
<p>Support <code>import.defer()</code> for context modules. (by <a href="https://github.com/ahabhgk"><code>@​ahabhgk</code></a> in <a href="">#20399</a>)</p>
</li>
<li>
<p>Added support for array values ​​to the <code>devtool</code> option. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20191</a>)</p>
</li>
<li>
<p>Improve rendering node built-in modules for ECMA module output. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20255</a>)</p>
</li>
<li>
<p>Unknown import.meta properties are now determined at runtime instead of being statically analyzed at compile time. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20312</a>)</p>
</li>
</ul>
<h3>Patch Changes</h3>
<ul>
<li>
<p>Fixed ESM default export handling for <code>.mjs</code> files in Module Federation (by <a href="https://github.com/y-okt"><code>@​y-okt</code></a> in <a href="">#20189</a>)</p>
</li>
<li>
<p>Optimized <code>import.meta.env</code> handling in destructuring assignments by using cached stringified environment definitions. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20313</a>)</p>
</li>
<li>
<p>Respect the <code>stats.errorStack</code> option in stats output. (by <a href="https://github.com/samarthsinh2660"><code>@​samarthsinh2660</code></a> in <a href="">#20258</a>)</p>
</li>
<li>
<p>Fixed a bug where declaring a <code>module</code> variable in module scope would conflict with the default <code>moduleArgument</code>. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20265</a>)</p>
</li>
<li>
<p>Fix VirtualUrlPlugin to set resourceData.context for proper module resolution. Previously, when context was not set, it would fallback to the virtual scheme path (e.g., <code>virtual:routes</code>), which is not a valid filesystem path, causing subsequent resolve operations to fail. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20390</a>)</p>
</li>
<li>
<p>Fixed Worker self-import handling to support various URL patterns (e.g., <code>import.meta.url</code>, <code>new URL(import.meta.url)</code>, <code>new URL(import.meta.url, import.meta.url)</code>, <code>new URL(&quot;./index.js&quot;, import.meta.url)</code>). Workers that resolve to the same module are now properly deduplicated, regardless of the URL syntax used. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20381</a>)</p>
</li>
<li>
<p>Reuse the same async entrypoint for the same Worker URL within a module to avoid circular dependency warnings when multiple Workers reference the same resource. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20345</a>)</p>
</li>
<li>
<p>Fixed a bug where a self-referencing dependency would have an unused export name when imported inside a web worker. (by <a href="https://github.com/samarthsinh2660"><code>@​samarthsinh2660</code></a> in <a href="">#20251</a>)</p>
</li>
<li>
<p>Fix missing export generation when concatenated modules in different chunks share the same runtime in module library bundles. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20346</a>)</p>
</li>
<li>
<p>Fixed <code>import.meta.env.xxx</code> behavior: when accessing a non-existent property, it now returns empty object instead of full object at runtime. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20289</a>)</p>
</li>
<li>
<p>Improved parsing error reporting by adding a link to the loader documentation. (by <a href="https://github.com/gaurav10gg"><code>@​gaurav10gg</code></a> in <a href="">#20244</a>)</p>
</li>
<li>
<p>Fix typescript types. (by <a href="https://github.com/alexander-akait"><code>@​alexander-akait</code></a> in <a href="">#20305</a>)</p>
</li>
<li>
<p>Add declaration for unused harmony import specifier. (by <a href="https://github.com/hai-x"><code>@​hai-x</code></a> in <a href="">#20286</a>)</p>
</li>
<li>
<p>Fix compressibility of modules while retaining portability. (by <a href="https://github.com/dmichon-msft"><code>@​dmichon-msft</code></a> in <a href="">#20287</a>)</p>
</li>
<li>
<p>Optimize source map generation: only include <code>ignoreList</code> property when it has content, avoiding empty arrays in source maps. (by <a href="https://github.com/xiaoxiaojx"><code>@​xiaoxiaojx</code></a> in <a href="">#20319</a>)</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1486f9a</code></a> chore(release): new release</li>
<li><a href=""><code>1a517f6</code></a> feat: added the <code>tsconfig</code> option for the <code>resolver</code> options (<a href="">#20400</a>)</li>
<li><a href=""><code>7b3b0f7</code></a> feat: support <code>import.defer()</code> for context modules</li>
<li><a href=""><code>c4a6a92</code></a> refactor: more types and increase types coverage</li>
<li><a href=""><code>5ecc58d</code></a> feat: consider asset module as side-effect-free (<a href="">#20352</a>)</li>
<li><a href=""><code>cce0f69</code></a> test: avoid comma operator in BinaryMiddleware test (<a href="">#20398</a>)</li>
<li><a href=""><code>cd4793d</code></a> feat: support import specifier guard (<a href="">#20320</a>)</li>
<li><a href=""><code>fe48655</code></a> docs: update examples (<a href="">#20397</a>)</li>
<li><a href=""><code>de107f8</code></a> fix(VirtualUrlPlugin): set resourceData.context to avoid invalid fallback (<a href="">#2</a>...</li>
<li><a href=""><code>a656ab1</code></a> test: add self-import test case for dynamic import (<a href="">#20389</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/webpack/webpack/compare/v5.98.0...v5.105.0">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by [GitHub Actions](<a href="https://www.npmjs.com/~GitHub">https://www.npmjs.com/~GitHub</a> Actions), a new releaser for webpack since your current version.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=webpack&package-manager=npm_and_yarn&previous-version=5.98.0&new-version=5.105.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `345d36b2e027`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.