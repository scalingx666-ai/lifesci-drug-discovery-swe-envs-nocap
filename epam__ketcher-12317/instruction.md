# Issue

**Title:** chore(deps-dev): bump vite from 8.0.16 to 8.1.6

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 8.0.16 to 8.1.6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/releases">vite's releases</a>.</em></p>
<blockquote>
<h2>v8.1.6</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.6/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.5</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.5/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.4</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.4/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.3</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.3/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.2</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.2/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.1</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.1/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>plugin-legacy@8.1.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/plugin-legacy@8.1.0/packages/plugin-legacy/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.0/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>plugin-legacy@8.1.0-beta.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/plugin-legacy@8.1.0-beta.0/packages/plugin-legacy/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
<h2>v8.1.0-beta.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/v8.1.0-beta.0/packages/vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/v8.1.6/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted --><a href="https://github.com/vitejs/vite/compare/v8.1.5...v8.1.6">8.1.6</a> (2026-10-06)<!-- raw HTML omitted --></h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> update launch-editor to v2.14.2 (<a href="">#23654</a>) (<a href="">e46fc9c</a>)</li>
<li><strong>html:</strong> filename passed to transformIndexHtml should not include queries (<a href="">#23653</a>) (<a href="">4ff2522</a>)</li>
<li><strong>server:</strong> store ids to <code>safeModulePaths</code> rather than URLs (<a href="">#23656</a>) (<a href="">170b927</a>)</li>
</ul>
<h2><!-- raw HTML omitted --><a href="https://github.com/vitejs/vite/compare/v8.1.4...v8.1.5">8.1.5</a> (2026-07-16)<!-- raw HTML omitted --></h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>bundled-dev:</strong> avoid duplicated <code>buildEnd</code> (<a href="">#22931</a>) (<a href="">8100320</a>)</li>
<li><strong>client:</strong> overlay error message format align rolldown (<a href="">#22869</a>) (<a href="">5a72b87</a>)</li>
<li><strong>deps:</strong> update all non-major dependencies (<a href="">#22921</a>) (<a href="">fef682d</a>)</li>
<li><strong>deps:</strong> update rolldown-related dependencies (<a href="">#22922</a>) (<a href="">3c345e4</a>)</li>
<li><strong>module-runner:</strong> don't crash stack-trace source mapping when globalThis.Buffer is absent (<a href="">#22945</a>) (<a href="">f8b38e3</a>)</li>
<li><strong>optimizer:</strong> respect importer module format for dynamic import interop with CJS deps (<a href="">#22951</a>) (<a href="">6c08c39</a>)</li>
<li><strong>ssr:</strong> scope switch-case declarations to the switch, not the function (<a href="">#22893</a>) (<a href="">b59a73f</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li><strong>build:</strong> fix incorrect <code>@default</code> for build.cssMinify (<a href="">#22948</a>) (<a href="">c88c236</a>)</li>
<li><strong>build:</strong> fix incorrect <code>@default</code> for build.lib.formats (<a href="">#22911</a>) (<a href="">369ed60</a>)</li>
</ul>
<h3>Tests</h3>
<ul>
<li>avoid scanner scanning all files under <code>__tests__</code> (<a href="">#22912</a>) (<a href="">c961cae</a>)</li>
</ul>
<h2><!-- raw HTML omitted --><a href="https://github.com/vitejs/vite/compare/v8.1.3...v8.1.4">8.1.4</a> (2026-07-09)<!-- raw HTML omitted --></h2>
<h3>Features</h3>
<ul>
<li><strong>legacy:</strong> prefer oxc as minifier (fix <a href="">#21973</a>) (<a href="">#22468</a>) (<a href="">ab5dafa</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><strong>build:</strong> add workaround for building on stackblitz (<a href="">#22840</a>) (<a href="">575c32c</a>)</li>
<li><strong>build:</strong> keep <code>import.meta.url</code> in preload function as-is (<a href="">#22839</a>) (<a href="">f1f90ed</a>)</li>
<li><strong>deps:</strong> update all non-major dependencies (<a href="">#22865</a>) (<a href="">d4295a9</a>)</li>
<li><strong>deps:</strong> update rolldown-related dependencies (<a href="">#22866</a>) (<a href="">7cf07e4</a>)</li>
<li><strong>html:</strong> avoid backtracking in import-only check (<a href="">#22848</a>) (<a href="">b5868c0</a>)</li>
<li><strong>optimizer:</strong> avoid optimizer run for transform request before init (<a href="">#22852</a>) (<a href="">72a5e21</a>)</li>
<li><strong>ssr:</strong> align named export function call stacktrace column with Node (<a href="">#22829</a>) (<a href="">173a1b6</a>)</li>
<li>strip pure CSS chunk imports when chunkImportMap is enabled (<a href="">#22841</a>) (<a href="">648bd04</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix incorrect <code>@default</code> for <code>server.cors</code> (<a href="">#22859</a>) (<a href="">70435b2</a>)</li>
</ul>
<h3>Miscellaneous Chores</h3>
<ul>
<li><strong>deps:</strong> update dependency postcss-modules to v9 (<a href="">#22867</a>) (<a href="">a9539d6</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dade886</code></a> release: v8.1.6</li>
<li><a href=""><code>170b927</code></a> fix(server): store ids to <code>safeModulePaths</code> rather than URLs (<a href="">#23656</a>)</li>
<li><a href=""><code>e46fc9c</code></a> fix(deps): update launch-editor to v2.14.2 (<a href="">#23654</a>)</li>
<li><a href=""><code>4ff2522</code></a> fix(html): filename passed to transformIndexHtml should not include queries (...</li>
<li><a href=""><code>5e7fe12</code></a> release: v8.1.5</li>
<li><a href=""><code>6c08c39</code></a> fix(optimizer): respect importer module format for dynamic import interop wit...</li>
<li><a href=""><code>5a72b87</code></a> fix(client): overlay error message format align rolldown (<a href="">#22869</a>)</li>
<li><a href=""><code>f8b38e3</code></a> fix(module-runner): don't crash stack-trace source mapping when globalThis.Bu...</li>
<li><a href=""><code>8100320</code></a> fix(bundled-dev): avoid duplicated <code>buildEnd</code> (<a href="">#22931</a>)</li>
<li><a href=""><code>c88c236</code></a> docs(build): fix incorrect <code>@default</code> for build.cssMinify (<a href="">#22948</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vitejs/vite/commits/v8.1.6/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=8.0.16&new-version=8.1.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c36175d39f09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.