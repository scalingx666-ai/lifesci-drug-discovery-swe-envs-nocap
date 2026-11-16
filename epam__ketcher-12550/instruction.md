# Issue

**Title:** chore(deps): bump the github-actions group with 5 updates

## Description

Bumps the github-actions group with 5 updates:

| Package | From | To |
| --- | --- | --- |
| [actions/checkout](https://github.com/actions/checkout) | `2.8.0` | `7.0.1` |
| [actions/github-script](https://github.com/actions/github-script) | `7.1.0` | `9.0.0` |
| [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) | `0.0.63` | `1.0.264` |
| [sonarsource/sonarqube-scan-action](https://github.com/sonarsource/sonarqube-scan-action) | `7.0.0` | `8.4.0` |
| [sonarsource/sonarqube-quality-gate-action](https://github.com/sonarsource/sonarqube-quality-gate-action) | `1.2.0` | `1.2.1` |

Updates `actions/checkout` from 2.8.0 to 7.0.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/releases">actions/checkout's releases</a>.</em></p>
<blockquote>
<h2>v7.0.1</h2>
<h2>What's Changed</h2>
<ul>
<li>skip running unsafe pr check if input is default by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2518</a></li>
<li>trim only ascii whitespace for branch by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2521</a></li>
<li>escape values passed to --unset by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2530</a></li>
<li>Various dependency updates</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v7...v7.0.1">https://github.com/actions/checkout/compare/v7...v7.0.1</a></p>
<h2>v7.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>block checking out fork pr for pull_request_target and workflow_run by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2454</a></li>
<li>Bump actions/publish-immutable-action from 0.0.3 to 0.0.4 in the minor-actions-dependencies group across 1 directory by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/checkout#2458</a></li>
<li>Bump flatted from 3.3.1 to 3.4.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/checkout#2460</a></li>
<li>Bump js-yaml from 4.1.0 to 4.2.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/checkout#2461</a></li>
<li>Bump <code>@​actions/core</code> and <code>@​actions/tool-cache</code> and Remove uuid by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/checkout#2459</a></li>
<li>upgrade module to esm and update dependencies by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2463</a></li>
<li>Bump the minor-npm-dependencies group across 1 directory with 3 updates by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">actions/checkout#2462</a></li>
<li>getting ready for checkout v7 release by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2464</a></li>
<li>update error wording by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2467</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> made their first contribution in <a href="">actions/checkout#2454</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v6.0.3...v7.0.0">https://github.com/actions/checkout/compare/v6.0.3...v7.0.0</a></p>
<h2>v6.1.0</h2>
<h2>What's Changed</h2>
<ul>
<li><strong>[BREAKING]</strong> backport <code>allow-unsafe-pr-checkout</code> to v6 by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2500</a></li>
<li>backport fixes to releases-v6 by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2527</a></li>
</ul>
<p><a href="https://github.blog/changelog/2026-06-18-safer-pull_request_target-defaults-for-github-actions-checkout/">https://github.blog/changelog/2026-06-18-safer-pull_request_target-defaults-for-github-actions-checkout/</a> for more details about this breaking change</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v6.0.3...v6.1.0">https://github.com/actions/checkout/compare/v6.0.3...v6.1.0</a></p>
<h2>v6.0.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Update changelog by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2357</a></li>
<li>fix: expand merge commit SHA regex and add SHA-256 test cases by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2414</a></li>
<li>Fix checkout init for SHA-256 repositories by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2439</a></li>
<li>Update changelog for v6.0.3 by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2446</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/yaananth"><code>@​yaananth</code></a> made their first contribution in <a href="">actions/checkout#2414</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v6...v6.0.3">https://github.com/actions/checkout/compare/v6...v6.0.3</a></p>
<h2>v6.0.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Add orchestration_id to git user-agent when ACTIONS_ORCHESTRATION_ID is set by <a href="https://github.com/TingluoHuang"><code>@​TingluoHuang</code></a> in <a href="">actions/checkout#2355</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/blob/main/CHANGELOG.md">actions/checkout's changelog</a>.</em></p>
<blockquote>
<h1>Changelog</h1>
<h2>v7.0.1</h2>
<ul>
<li>Skip running unsafe pr check if input is default by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2518</a></li>
<li>Trim only ascii whitespace for branch by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2521</a></li>
<li>Escape values passed to --unset by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2530</a></li>
<li>Various dependency updates</li>
</ul>
<h2>v7.0.0</h2>
<ul>
<li>Block checking out fork PR for pull_request_target and workflow_run by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2454</a></li>
<li>Various dependency updates</li>
</ul>
<h2>v6.0.3</h2>
<ul>
<li>Fix checkout init for SHA-256 repositories by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2439</a></li>
<li>fix: expand merge commit SHA regex and add SHA-256 test cases by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2414</a></li>
</ul>
<h2>v6.0.2</h2>
<ul>
<li>Fix tag handling: preserve annotations and explicit fetch-tags by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2356</a></li>
</ul>
<h2>v6.0.1</h2>
<ul>
<li>Add worktree support for persist-credentials includeIf by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2327</a></li>
</ul>
<h2>v6.0.0</h2>
<ul>
<li>Persist creds to a separate file by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2286</a></li>
<li>Update README to include Node.js 24 support details and requirements by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2248</a></li>
</ul>
<h2>v5.0.1</h2>
<ul>
<li>Port v6 cleanup to v5 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2301</a></li>
</ul>
<h2>v5.0.0</h2>
<ul>
<li>Update actions checkout to use node 24 by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2226</a></li>
</ul>
<h2>v4.3.1</h2>
<ul>
<li>Port v6 cleanup to v4 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2305</a></li>
</ul>
<h2>v4.3.0</h2>
<ul>
<li>docs: update README.md by <a href="https://github.com/motss"><code>@​motss</code></a> in <a href="">actions/checkout#1971</a></li>
<li>Add internal repos for checking out multiple repositories by <a href="https://github.com/mouismail"><code>@​mouismail</code></a> in <a href="">actions/checkout#1977</a></li>
<li>Documentation update - add recommended permissions to Readme by <a href="https://github.com/benwells"><code>@​benwells</code></a> in <a href="">actions/checkout#2043</a></li>
<li>Adjust positioning of user email note and permissions heading by <a href="https://github.com/joshmgross"><code>@​joshmgross</code></a> in <a href="">actions/checkout#2044</a></li>
<li>Update README.md by <a href="https://github.com/nebuk89"><code>@​nebuk89</code></a> in <a href="">actions/checkout#2194</a></li>
<li>Update CODEOWNERS for actions by <a href="https://github.com/TingluoHuang"><code>@​TingluoHuang</code></a> in <a href="">actions/checkout#2224</a></li>
<li>Update package dependencies by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2236</a></li>
</ul>
<h2>v4.2.2</h2>
<ul>
<li><code>url-helper.ts</code> now leverages well-known environment variables by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1941</a></li>
<li>Expand unit test coverage for <code>isGhes</code> by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1946</a></li>
</ul>
<h2>v4.2.1</h2>
<ul>
<li>Check out other refs/* by commit if provided, fall back to ref by <a href="https://github.com/orhantoy"><code>@​orhantoy</code></a> in <a href="">actions/checkout#1924</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3d3c42e</code></a> prep v7.0.1 release (<a href="">#2531</a>)</li>
<li><a href=""><code>2880268</code></a> escape values passed to --unset (<a href="">#2530</a>)</li>
<li><a href=""><code>12cd223</code></a> trim only ascii whitespace for branch (<a href="">#2521</a>)</li>
<li><a href=""><code>62661c4</code></a> skip running unsafe pr check if input is default (<a href="">#2518</a>)</li>
<li><a href=""><code>e8d4307</code></a> Bump the minor-actions-dependencies group with 2 updates (<a href="">#2499</a>)</li>
<li><a href=""><code>631c942</code></a> eslint 9 (<a href="">#2474</a>)</li>
<li><a href=""><code>4f1f4ae</code></a> Bump actions/upload-artifact from 4 to 7 (<a href="">#2476</a>)</li>
<li><a href=""><code>ba09753</code></a> Bump actions/checkout from 6 to 7 (<a href="">#2488</a>)</li>
<li><a href=""><code>b9e0990</code></a> Bump docker/login-action from 3.3.0 to 4.2.0 (<a href="">#2479</a>)</li>
<li><a href=""><code>e8cb398</code></a> Bump docker/build-push-action from 6.5.0 to 7.2.0 (<a href="">#2478</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/checkout/compare/v2.8.0...3d3c42e5aac5ba805825da76410c181273ba90b1">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/github-script` from 7.1.0 to 9.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/github-script/releases">actions/github-script's releases</a>.</em></p>
<blockquote>
<h2>v9.0.0</h2>
<p><strong>New features:</strong></p>
<ul>
<li><strong><code>getOctokit</code> factory function</strong> — Available directly in the script context. Create additional authenticated Octokit clients with different tokens for multi-token workflows, GitHub App tokens, and cross-org access. See <a href="https://github.com/actions/github-script#creating-additional-clients-with-getoctokit">Creating additional clients with <code>getOctokit</code></a> for details and examples.</li>
<li><strong>Orchestration ID in user-agent</strong> — The <code>ACTIONS_ORCHESTRATION_ID</code> environment variable is automatically appended to the user-agent string for request tracing.</li>
</ul>
<p><strong>Breaking changes:</strong></p>
<ul>
<li><strong><code>require('@actions/github')</code> no longer works in scripts.</strong> The upgrade to <code>@actions/github</code> v9 (ESM-only) means <code>require('@actions/github')</code> will fail at runtime. If you previously used patterns like <code>const { getOctokit } = require('@actions/github')</code> to create secondary clients, use the new injected <code>getOctokit</code> function instead — it's available directly in the script context with no imports needed.</li>
<li><code>getOctokit</code> is now an injected function parameter. Scripts that declare <code>const getOctokit = ...</code> or <code>let getOctokit = ...</code> will get a <code>SyntaxError</code> because JavaScript does not allow <code>const</code>/<code>let</code> redeclaration of function parameters. Use the injected <code>getOctokit</code> directly, or use <code>var getOctokit = ...</code> if you need to redeclare it.</li>
<li>If your script accesses other <code>@actions/github</code> internals beyond the standard <code>github</code>/<code>octokit</code> client, you may need to update those references for v9 compatibility.</li>
</ul>
<h2>What's Changed</h2>
<ul>
<li>Add ACTIONS_ORCHESTRATION_ID to user-agent string by <a href="https://github.com/Copilot"><code>@​Copilot</code></a> in <a href="">actions/github-script#695</a></li>
<li>ci: use deployment: false for integration test environments by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/github-script#712</a></li>
<li>feat!: add getOctokit to script context, upgrade <code>@​actions/github</code> v9, <code>@​octokit/core</code> v7, and related packages by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/github-script#700</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Copilot"><code>@​Copilot</code></a> made their first contribution in <a href="">actions/github-script#695</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/github-script/compare/v8.0.0...v9.0.0">https://github.com/actions/github-script/compare/v8.0.0...v9.0.0</a></p>
<h2>v8.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Update Node.js version support to 24.x by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/github-script#637</a></li>
<li>README for updating actions/github-script from v7 to v8 by <a href="https://github.com/sneha-krip"><code>@​sneha-krip</code></a> in <a href="">actions/github-script#653</a></li>
</ul>
<h2>⚠️ Minimum Compatible Runner Version</h2>
<p><strong>v2.327.1</strong><br />
<a href="https://github.com/actions/runner/releases/tag/v2.327.1">Release Notes</a></p>
<p>Make sure your runner is updated to this version or newer to use this release.</p>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> made their first contribution in <a href="">actions/github-script#637</a></li>
<li><a href="https://github.com/sneha-krip"><code>@​sneha-krip</code></a> made their first contribution in <a href="">actions/github-script#653</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/github-script/compare/v7.1.0...v8.0.0">https://github.com/actions/github-script/compare/v7.1.0...v8.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3a2844b</code></a> Merge pull request <a href="">#700</a> from actions/salmanmkc/expose-getoctokit + prepare re...</li>
<li><a href=""><code>ca10bbd</code></a> fix: use <code>@​octokit/core/</code>types import for v7 compatibility</li>
<li><a href=""><code>86e48e2</code></a> merge: incorporate main branch changes</li>
<li><a href=""><code>c108472</code></a> chore: rebuild dist for v9 upgrade and getOctokit factory</li>
<li><a href=""><code>afff112</code></a> Merge pull request <a href="">#712</a> from actions/salmanmkc/deployment-false + fix user-ag...</li>
<li><a href=""><code>ff8117e</code></a> ci: fix user-agent test to handle orchestration ID</li>
<li><a href=""><code>81c6b78</code></a> ci: use deployment: false to suppress deployment noise from integration tests</li>
<li><a href=""><code>3953caf</code></a> docs: update README examples from <a href="https://github.com/v8"><code>@​v8</code></a> to <a href="https://github.com/v9"><code>@​v9</code></a>, add getOctokit docs and v9 brea...</li>
<li><a href=""><code>c17d55b</code></a> ci: add getOctokit integration test job</li>
<li><a href=""><code>a047196</code></a> test: add getOctokit integration tests via callAsyncFunction</li>
<li>Additional commits viewable in <a href="https://github.com/actions/github-script/compare/f28e40c7f34bde8b3046d885e986cb6290c5673b...3a2844b7e9c422d3c10d287c895573f7108da1b3">compare view</a></li>
</ul>
</details>
<br />

Updates `anthropics/claude-code-action` from 0.0.63 to 1.0.264
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/anthropics/claude-code-action/releases">anthropics/claude-code-action's releases</a>.</em></p>
<blockquote>
<h2>v1.0.264</h2>
<h2>What's Changed</h2>
<ul>
<li>docs: use claude-plugins-official in plugin examples by <a href="https://github.com/mhegazy"><code>@​mhegazy</code></a> in <a href="">anthropics/claude-code-action#1932</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.263...v1.0.264">https://github.com/anthropics/claude-code-action/compare/v1.0.263...v1.0.264</a></p>
<h2>v1.0.263</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.262...v1.0.263">https://github.com/anthropics/claude-code-action/compare/v1.0.262...v1.0.263</a></p>
<h2>v1.0.262</h2>
<h2>What's Changed</h2>
<ul>
<li>chore: bump Bun to 1.4.4 by <a href="https://github.com/dylan-conway"><code>@​dylan-conway</code></a> in <a href="">anthropics/claude-code-action#1916</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/dylan-conway"><code>@​dylan-conway</code></a> made their first contribution in <a href="">anthropics/claude-code-action#1916</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.261...v1.0.262">https://github.com/anthropics/claude-code-action/compare/v1.0.261...v1.0.262</a></p>
<h2>v1.0.261</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.260...v1.0.261">https://github.com/anthropics/claude-code-action/compare/v1.0.260...v1.0.261</a></p>
<h2>v1.0.260</h2>
<h2>What's Changed</h2>
<ul>
<li>Pin the PR version a run checks out by <a href="https://github.com/OctavianGuzu"><code>@​OctavianGuzu</code></a> in <a href="">anthropics/claude-code-action#1915</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.259...v1.0.260">https://github.com/anthropics/claude-code-action/compare/v1.0.259...v1.0.260</a></p>
<h2>v1.0.259</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.258...v1.0.259">https://github.com/anthropics/claude-code-action/compare/v1.0.258...v1.0.259</a></p>
<h2>v1.0.258</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.257...v1.0.258">https://github.com/anthropics/claude-code-action/compare/v1.0.257...v1.0.258</a></p>
<h2>v1.0.257</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.256...v1.0.257">https://github.com/anthropics/claude-code-action/compare/v1.0.256...v1.0.257</a></p>
<h2>v1.0.256</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.255...v1.0.256">https://github.com/anthropics/claude-code-action/compare/v1.0.255...v1.0.256</a></p>
<h2>v1.0.255</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.254...v1.0.255">https://github.com/anthropics/claude-code-action/compare/v1.0.254...v1.0.255</a></p>
<h2>v1.0.254</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.253...v1.0.254">https://github.com/anthropics/claude-code-action/compare/v1.0.253...v1.0.254</a></p>
<h2>v1.0.253</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/anthropics/claude-code-action/compare/v1.0.252...v1.0.253">https://github.com/anthropics/claude-code-action/compare/v1.0.252...v1.0.253</a></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d70510b</code></a> chore: bump Claude Code to 2.1.312 and Agent SDK to 0.3.312</li>
<li><a href=""><code>98a9e39</code></a> docs: use claude-plugins-official in plugin examples (<a href="">#1932</a>)</li>
<li><a href=""><code>8041f1d</code></a> chore: bump Claude Code to 2.1.311 and Agent SDK to 0.3.311</li>
<li><a href=""><code>925afb5</code></a> chore: bump Bun to 1.4.4 (<a href="">#1916</a>)</li>
<li><a href=""><code>16f9f71</code></a> chore: bump Claude Code to 2.1.310 and Agent SDK to 0.3.310</li>
<li><a href=""><code>8d70a0d</code></a> Pin the PR version a run checks out (<a href="">#1915</a>)</li>
<li><a href=""><code>ae68417</code></a> chore: bump Claude Code to 2.1.309 and Agent SDK to 0.3.309</li>
<li><a href=""><code>6b6870e</code></a> chore: bump Claude Code to 2.1.308 and Agent SDK to 0.3.308</li>
<li><a href=""><code>aa8a773</code></a> chore: bump Claude Code to 2.1.307 and Agent SDK to 0.3.307</li>
<li><a href=""><code>a5a423f</code></a> chore: bump Claude Code to 2.1.306 and Agent SDK to 0.3.306</li>
<li>Additional commits viewable in <a href="https://github.com/anthropics/claude-code-action/compare/v0.0.63...d70510b174a1244958df0b03166a54912811f3e6">compare view</a></li>
</ul>
</details>
<br />

Updates `sonarsource/sonarqube-scan-action` from 7.0.0 to 8.4.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sonarsource/sonarqube-scan-action/releases">sonarsource/sonarqube-scan-action's releases</a>.</em></p>
<blockquote>
<h2>v8.4.0</h2>
<h2>What's Changed</h2>
<ul>
<li>SQSCANGHA-174 NO-JIRA Bump actions/setup-node from 7.0.0 to 7.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#277</a></li>
<li>Update Rollup and preserve scanner argument compatibility by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#275</a></li>
<li>Update dependency rollup to v4.64.6 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#279</a></li>
<li>SQSCANGHA-177 Update SonarScanner CLI to 8.2.0.6438 by <a href="https://github.com/github-actions"><code>@​github-actions</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#281</a></li>
<li>SQSCANGHA-176 docs: refresh action and scanner version examples by <a href="https://github.com/zglicz"><code>@​zglicz</code></a> in <a href="">SonarSource/sonarqube-scan-action#280</a></li>
<li>Update dependency rollup to v4.64.7 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#282</a></li>
<li>[CONTENT-3798] README update for marketing by <a href="https://github.com/tom-howlett-sonarsource"><code>@​tom-howlett-sonarsource</code></a> in <a href="">SonarSource/sonarqube-scan-action#274</a></li>
<li>Update dependency rollup to v4.64.9 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#283</a></li>
<li>Update dependency rollup to v4.64.12 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#288</a></li>
<li>Update dependency rollup to v4.65.0 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#291</a></li>
<li>SQSCANGHA-185 NO-JIRA Bump madhead/semver-utils from 5.0.0 to 5.1.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#290</a></li>
<li>Update SonarScanner CLI to 8.3.0.16463 by <a href="https://github.com/github-actions"><code>@​github-actions</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#293</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/zglicz"><code>@​zglicz</code></a> made their first contribution in <a href="">SonarSource/sonarqube-scan-action#280</a></li>
<li><a href="https://github.com/tom-howlett-sonarsource"><code>@​tom-howlett-sonarsource</code></a> made their first contribution in <a href="">SonarSource/sonarqube-scan-action#274</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-scan-action/compare/v8.3.0...v8.4.0">https://github.com/SonarSource/sonarqube-scan-action/compare/v8.3.0...v8.4.0</a></p>
<h2>v8.3.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix GPG key retrieval through HTTPS proxies by <a href="https://github.com/Torbjorn-Svensson"><code>@​Torbjorn-Svensson</code></a> in <a href="">SonarSource/sonarqube-scan-action#265</a></li>
<li>Configure Renovate by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#267</a></li>
<li>SQSCANGHA-168 Update actions/cache action to v5.1.0 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#269</a></li>
<li>Update npm dependencies by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#268</a></li>
<li>Update dependency <code>@​actions/exec</code> to v3 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#270</a></li>
<li>Update GitHub Actions dependencies (major) by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#271</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Torbjorn-Svensson"><code>@​Torbjorn-Svensson</code></a> made their first contribution in <a href="">SonarSource/sonarqube-scan-action#265</a></li>
<li><a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] made their first contribution in <a href="">SonarSource/sonarqube-scan-action#267</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-scan-action/compare/v8.2.2...v8.3.0">https://github.com/SonarSource/sonarqube-scan-action/compare/v8.2.2...v8.3.0</a></p>
<h2>v8.2.2</h2>
<h2>What's Changed</h2>
<ul>
<li>SQSCANGHA-159 Bump undici from 6.24.1 to 6.28.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">SonarSource/sonarqube-scan-action#261</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-scan-action/compare/v8.2.1...v8.2.2">https://github.com/SonarSource/sonarqube-scan-action/compare/v8.2.1...v8.2.2</a></p>
<h2>v8.2.1</h2>
<h2>What's Changed</h2>
<h3>Bug fix</h3>
<ul>
<li><a href="https://sonarsource.atlassian.net/browse/SQSCANGHA-156">SQSCANGHA-156</a> GPG signature verification fails when temporary directory path is too long</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4d1dc0c</code></a> Update SonarScanner CLI to 8.3.0.16463 (<a href="">#293</a>)</li>
<li><a href=""><code>ee2d757</code></a> SQSCANGHA-185 NO-JIRA Bump madhead/semver-utils from 5.0.0 to 5.1.1 (<a href="">#290</a>)</li>
<li><a href=""><code>a7de334</code></a> Update dependency rollup to v4.65.0 (<a href="">#291</a>)</li>
<li><a href=""><code>38f0382</code></a> Update dependency rollup to v4.64.12 (<a href="">#288</a>)</li>
<li><a href=""><code>54ae8f2</code></a> Update dependency rollup to v4.64.9 (<a href="">#283</a>)</li>
<li><a href=""><code>3a63ba4</code></a> CONTENT-3798 README update for marketing (<a href="">#274</a>)</li>
<li><a href=""><code>b632445</code></a> Update dependency rollup to v4.64.7 (<a href="">#282</a>)</li>
<li><a href=""><code>c3c1d58</code></a> SQSCANGHA-176 docs: refresh action and scanner version examples (<a href="">#280</a>)</li>
<li><a href=""><code>b541427</code></a> SQSCANGHA-177 Update SonarScanner CLI to 8.2.0.6438 (<a href="">#281</a>)</li>
<li><a href=""><code>15d1d91</code></a> Update dependency rollup to v4.64.6 (<a href="">#279</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/sonarsource/sonarqube-scan-action/compare/a31c9398be7ace6bbfaf30c0bd5d415f843d45e9...4d1dc0c91ee400dcf8a6dddf2f705ac36542e304">compare view</a></li>
</ul>
</details>
<br />

Updates `sonarsource/sonarqube-quality-gate-action` from 1.2.0 to 1.2.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sonarsource/sonarqube-quality-gate-action/releases">sonarsource/sonarqube-quality-gate-action's releases</a>.</em></p>
<blockquote>
<h2>v1.2.1</h2>
<h2>What's Changed</h2>
<ul>
<li>BUILD-8875: Migrate to standardized GitHub runner names by <a href="https://github.com/SonarTech"><code>@​SonarTech</code></a> in <a href="">SonarSource/sonarqube-quality-gate-action#66</a></li>
<li>SC-32488 Add sq analysis by <a href="https://github.com/stanislavhh"><code>@​stanislavhh</code></a> in <a href="">SonarSource/sonarqube-quality-gate-action#67</a></li>
<li>SC-36243 Add sonar-secrets pre-commit hook by <a href="https://github.com/VictorSchneuwly"><code>@​VictorSchneuwly</code></a> in <a href="">SonarSource/sonarqube-quality-gate-action#68</a></li>
<li>SQQGGHA-13 SubmitReview: Use Vault token by <a href="https://github.com/pavel-mikula-sonarsource"><code>@​pavel-mikula-sonarsource</code></a> in <a href="">SonarSource/sonarqube-quality-gate-action#69</a></li>
<li>SQQGGHA-12: surface SonarQube error message on background task … by <a href="https://github.com/amaurywyart-sq"><code>@​amaurywyart-sq</code></a> in <a href="">SonarSource/sonarqube-quality-gate-action#71</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/SonarTech"><code>@​SonarTech</code></a> made their first contribution in <a href="">SonarSource/sonarqube-quality-gate-action#66</a></li>
<li><a href="https://github.com/stanislavhh"><code>@​stanislavhh</code></a> made their first contribution in <a href="">SonarSource/sonarqube-quality-gate-action#67</a></li>
<li><a href="https://github.com/VictorSchneuwly"><code>@​VictorSchneuwly</code></a> made their first contribution in <a href="">SonarSource/sonarqube-quality-gate-action#68</a></li>
<li><a href="https://github.com/amaurywyart-sq"><code>@​amaurywyart-sq</code></a> made their first contribution in <a href="">SonarSource/sonarqube-quality-gate-action#71</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-quality-gate-action/compare/v1.2.0...v1.2.1">https://github.com/SonarSource/sonarqube-quality-gate-action/compare/v1.2.0...v1.2.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7a5fffe</code></a> SQQGGHA-12: surface SonarQube error message on background task … (<a href="">#71</a>)</li>
<li><a href=""><code>8e9b0ca</code></a> SQQGGHA-13 SubmitReview: Use Vault token (<a href="">#69</a>)</li>
<li><a href=""><code>cb3ed20</code></a> SC-36243 Add sonar-secrets pre-commit hook (<a href="">#68</a>)</li>
<li><a href=""><code>95b1cc6</code></a> SC-32488 Add sq analysis (<a href="">#67</a>)</li>
<li><a href=""><code>174f836</code></a> BUILD-8875: Update GitHub Actions runners to new naming convention</li>
<li>See full diff in <a href="https://github.com/sonarsource/sonarqube-quality-gate-action/compare/cf038b0e0cdecfa9e56c198bbb7d21d751d62c3b...7a5fffe8e523c40e0c740b6bc2712ab503e52efa">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9652aca9a306`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.