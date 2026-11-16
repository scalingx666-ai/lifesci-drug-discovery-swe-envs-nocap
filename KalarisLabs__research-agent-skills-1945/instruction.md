# Issue

**Title:** ci: bump the actions group across 1 directory with 9 updates

## Description

Bumps the actions group with 9 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [step-security/harden-runner](https://github.com/step-security/harden-runner) | `2.21.1` | `2.22.1` |
| [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv) | `10.2.0` | `10.3.0` |
| [actions/upload-artifact](https://github.com/actions/upload-artifact) | `7.0.1` | `7.0.2` |
| [actions/setup-node](https://github.com/actions/setup-node) | `7.0.0` | `7.1.0` |
| [github/codeql-action/init](https://github.com/github/codeql-action) | `4.38.2` | `4.39.0` |
| [github/codeql-action/analyze](https://github.com/github/codeql-action) | `4.38.2` | `4.39.0` |
| [ossf/scorecard-action](https://github.com/ossf/scorecard-action) | `2.4.4` | `2.5.0` |
| [github/codeql-action/upload-sarif](https://github.com/github/codeql-action) | `4.38.2` | `4.39.0` |
| [trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog) | `3.97.9` | `3.99.2` |

Updates `step-security/harden-runner` from 2.21.1 to 2.22.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/step-security/harden-runner/releases">step-security/harden-runner's releases</a>.</em></p>
<blockquote>
<h2>v2.22.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Fixed security rules not initializing on GHES self-hosted runners</li>
<li>Fixed GHES connectivity in block mode by implicitly allowing the GHES hostname</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/step-security/harden-runner/compare/v2.22.0...v2.22.1">https://github.com/step-security/harden-runner/compare/v2.22.0...v2.22.1</a></p>
<h2>v2.22.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Linux ARM64 support for community tier</li>
<li>GHES support for self-hosted VMs (enterprise tier)</li>
<li>MacOS and Windows runner deny list support for block policy (enterprise tier).</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/step-security/harden-runner/compare/v2.21.1...v2.22.0">https://github.com/step-security/harden-runner/compare/v2.21.1...v2.22.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ccd8616</code></a> Merge pull request <a href="">#704</a> from h0x0er/jatin/ghes-endp</li>
<li><a href=""><code>037ccfd</code></a> implicitly add ghes endpoint in allowList</li>
<li><a href=""><code>e7438c7</code></a> Merge pull request <a href="">#703</a> from h0x0er/jatin/ghes-codebuild-fixes</li>
<li><a href=""><code>afb0b33</code></a> fixes for armour rules not getting initialised</li>
<li><a href=""><code>351661c</code></a> Merge pull request <a href="">#701</a> from step-security/rc-44</li>
<li><a href=""><code>1dc7f2e</code></a> Merge pull request <a href="">#702</a> from h0x0er/jatin/ghes-changes-up</li>
<li><a href=""><code>af5ca38</code></a> simplified ghes config creation</li>
<li><a href=""><code>9a6d710</code></a> fix2</li>
<li><a href=""><code>74c65ea</code></a> fix</li>
<li><a href=""><code>ceac816</code></a> resovled comments</li>
<li>Additional commits viewable in <a href="https://github.com/step-security/harden-runner/compare/e14015d583714f6e62063499dc959a02595150a1...ccd8616d44fd3846e67624a50d5aad6d37bf2d25">compare view</a></li>
</ul>
</details>
<br />

Updates `astral-sh/setup-uv` from 10.2.0 to 10.3.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.3.0 🌈 Add Python architecture selection</h2>
<h2>Changes</h2>
<p>This release adds the <code>python-arch</code> input to select a Python architecture independently of the Python version. With <code>uv</code> 0.13.0 or later, set <code>python-arch: x86_64</code> to use x64 Python on Windows ARM64 runners.</p>
<p>It also includes embedded checksums for <code>uv</code> releases through 0.13.0.</p>
<ul>
<li>Use macOS 15 runners for tests <a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a> (<a href="">#1081</a>)</li>
</ul>
<h2>🚀 Enhancements</h2>
<ul>
<li>Add <code>python-arch</code> support <a href="https://github.com/zanieb"><code>@​zanieb</code></a> (<a href="">#1079</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.0 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1089</a>)</li>
<li>chore: update known checksums for 0.12.24 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1084</a>)</li>
<li>chore: update known checksums for 0.12.23 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1082</a>)</li>
<li>chore: update known checksums for 0.12.22 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1080</a>)</li>
<li>chore: update known checksums for 0.12.21 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1078</a>)</li>
<li>chore: update known checksums for 0.12.20 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1076</a>)</li>
<li>chore: update known checksums for 0.12.19 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1068</a>)</li>
<li>chore: update known checksums for 0.12.18 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1065</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): bump zizmorcore/zizmor-action from 0.6.2 to 0.6.3 @<a href="https://github.com/apps/dependabot">dependabot[bot]</a> (<a href="">#1077</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1c37ad0</code></a> chore: update known checksums for 0.13.0 (<a href="">#1089</a>)</li>
<li><a href=""><code>b3c9b5f</code></a> chore: update known checksums for 0.12.24 (<a href="">#1084</a>)</li>
<li><a href=""><code>b06acff</code></a> Add <code>python-arch</code> support (<a href="">#1079</a>)</li>
<li><a href=""><code>c84232c</code></a> chore: update known checksums for 0.12.23 (<a href="">#1082</a>)</li>
<li><a href=""><code>51fdd26</code></a> Use macOS 15 runners for tests (<a href="">#1081</a>)</li>
<li><a href=""><code>a96208b</code></a> chore: update known checksums for 0.12.22 (<a href="">#1080</a>)</li>
<li><a href=""><code>0e3884b</code></a> chore: update known checksums for 0.12.21 (<a href="">#1078</a>)</li>
<li><a href=""><code>bcf0580</code></a> chore: update known checksums for 0.12.20 (<a href="">#1076</a>)</li>
<li><a href=""><code>b92a892</code></a> chore(deps): bump zizmorcore/zizmor-action from 0.6.2 to 0.6.3 (<a href="">#1077</a>)</li>
<li><a href=""><code>227a0f6</code></a> chore: update known checksums for 0.12.19 (<a href="">#1068</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/setup-uv/compare/c18668ad3cf93ea998bef934396af7bb5c839dc7...1c37ad07a6a961277cf70c0d37d6f313000f5884">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/upload-artifact` from 7.0.1 to 7.0.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/upload-artifact/releases">actions/upload-artifact's releases</a>.</em></p>
<blockquote>
<h2>v7.0.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Improves artifact download retries when the service returns HTTP 429 (rate limiting), including honoring valid Retry-After headers.</li>
<li>Updates <code>@​actions/artifact</code> to v6.3.1.</li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/tunc-d"><code>@​tunc-d</code></a> made their first contribution in <a href="">actions/upload-artifact#821</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/upload-artifact/compare/v7.0.1...v7.0.2">https://github.com/actions/upload-artifact/compare/v7.0.1...v7.0.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cf430e0</code></a> Merge pull request <a href="">#822</a> from actions/tunc-d-prepare-upload-v7-0-2</li>
<li><a href=""><code>c2acded</code></a> chore: prepare v7.0.2 release</li>
<li><a href=""><code>4687c1b</code></a> Merge pull request <a href="">#821</a> from actions/tunc-d-upload-artifact-package-bump</li>
<li><a href=""><code>8cbe1be</code></a> Bump <code>@​actions/artifact</code> to 6.3.1</li>
<li>See full diff in <a href="https://github.com/actions/upload-artifact/compare/043fb46d1a93c77aae656e7c1c64a875d1fc6a0a...cf430e030ddbb5b0abf93d22962f4752f3646cd9">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/setup-node` from 7.0.0 to 7.1.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/setup-node/releases">actions/setup-node's releases</a>.</em></p>
<blockquote>
<h2>v7.1.0</h2>
<h2>What's Changed</h2>
<h3>Enhancements:</h3>
<ul>
<li>Add support for mise.toml file by <a href="https://github.com/gperdomor"><code>@​gperdomor</code></a> in <a href="">actions/setup-node#1421</a></li>
<li>Support absolute paths in node-version-file by <a href="https://github.com/v-mahabaleshwars"><code>@​v-mahabaleshwars</code></a> in <a href="">actions/setup-node#1633</a></li>
</ul>
<h3>Bug fixes:</h3>
<ul>
<li>Add Node version validation and manifest fetch retry by <a href="https://github.com/v-jitenderpalsingh"><code>@​v-jitenderpalsingh</code></a> in <a href="">actions/setup-node#1580</a></li>
</ul>
<h3>Documentation updates:</h3>
<ul>
<li>README.md: bump actions/checkout to latest version 7 by <a href="https://github.com/deining"><code>@​deining</code></a> in <a href="">actions/setup-node#1578</a></li>
<li>docs: add V7 ESM migration and NODE_AUTH_TOKEN behavior change by <a href="https://github.com/v-gowridurgad"><code>@​v-gowridurgad</code></a> in <a href="">actions/setup-node#1593</a></li>
<li>Fixed cache recommendation syntax by <a href="https://github.com/SubJunk"><code>@​SubJunk</code></a> in <a href="">actions/setup-node#1603</a></li>
</ul>
<h3>Dependency updates:</h3>
<ul>
<li>Update workflow pins and migrate Node matrices to modern versions by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-node#1583</a></li>
<li>Upgrade  <code>@​actions/cache</code> to 6.2.0 by <a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> in <a href="">actions/setup-node#1584</a></li>
<li>Pin <code>@​types/node</code> to v24 by <a href="https://github.com/v-priyagupta108"><code>@​v-priyagupta108</code></a> in <a href="">actions/setup-node#1585</a></li>
<li>Override brace-expansion to 5.0.8 by <a href="https://github.com/v-priyagupta108"><code>@​v-priyagupta108</code></a> with <a href="https://github.com/Copilot"><code>@​Copilot</code></a> in <a href="">actions/setup-node#1599</a></li>
<li>Upgrade  actions/checkout from 7.0.0 to 7.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1598</a></li>
<li>Upgrade  prettier from 3.8.4 to 3.9.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1590</a></li>
<li>Upgrade  <code>@​vercel/ncc</code> from 0.44.0 to 0.45.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1610</a></li>
<li>Upgrade  pnpm/action-setup from 6.0.9 to 6.0.10 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1602</a></li>
<li>Upgrade  baseline-browser-mapping from 2.10.38 to 2.11.22 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1629</a></li>
<li>Upgrade <code>@​types/semver</code> from 7.7.1 to 7.8.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1616</a></li>
<li>Upgrade <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1615</a></li>
<li>Upgrade pnpm/action-setup from 6.0.10 to 6.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1631</a></li>
<li>Upgrade jest-each from 30.4.1 to 30.5.2 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1636</a></li>
<li>Upgrade eslint-plugin-n from 18.1.0 to 18.3.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1638</a></li>
<li>Update dependencies and add license files by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-node#1642</a></li>
<li>Upgrade eslint from 10.5.0 to 10.11.0 and package.json from 7.0.0 to 7.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-node#1635</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/v-jitenderpalsingh"><code>@​v-jitenderpalsingh</code></a> made their first contribution in <a href="">actions/setup-node#1580</a></li>
<li><a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> made their first contribution in <a href="">actions/setup-node#1584</a></li>
<li><a href="https://github.com/gperdomor"><code>@​gperdomor</code></a> made their first contribution in <a href="">actions/setup-node#1421</a></li>
<li><a href="https://github.com/SubJunk"><code>@​SubJunk</code></a> made their first contribution in <a href="">actions/setup-node#1603</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-node/compare/v7.0.0...v7.1.0">https://github.com/actions/setup-node/compare/v7.0.0...v7.1.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>949feb2</code></a> Bump eslint from 10.5.0 to 10.11.0 and package.json from 7.0.0 to 7.1.0 (<a href="">#1635</a>)</li>
<li><a href=""><code>7207c4f</code></a> chore: update dependencies and add license files (<a href="">#1642</a>)</li>
<li><a href=""><code>54337e0</code></a> Bump eslint-plugin-n from 18.1.0 to 18.3.0 (<a href="">#1638</a>)</li>
<li><a href=""><code>fb54fa8</code></a> Bump jest-each from 30.4.1 to 30.5.2 (<a href="">#1636</a>)</li>
<li><a href=""><code>7f84f1d</code></a> Bump pnpm/action-setup from 6.0.10 to 6.1.0 (<a href="">#1631</a>)</li>
<li><a href=""><code>0c54c7b</code></a> Bump <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 (<a href="">#1615</a>)</li>
<li><a href=""><code>a829419</code></a> Bump <code>@​types/semver</code> from 7.7.1 to 7.8.0 (<a href="">#1616</a>)</li>
<li><a href=""><code>680d1e4</code></a> Support absolute paths in node-version-file (<a href="">#1633</a>)</li>
<li><a href=""><code>db0fb3a</code></a> Bump baseline-browser-mapping from 2.10.38 to 2.11.22 (<a href="">#1629</a>)</li>
<li><a href=""><code>94196ee</code></a> Bump pnpm/action-setup from 6.0.9 to 6.0.10 (<a href="">#1602</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/setup-node/compare/820762786026740c76f36085b0efc47a31fe5020...949feb2413d6458794dcd2491c4babbbce0c15c1">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/init` from 4.38.2 to 4.39.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/init's releases</a>.</em></p>
<blockquote>
<h2>v4.39.0</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>v4.38.3</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/blob/main/CHANGELOG.md">github/codeql-action/init's changelog</a>.</em></p>
<blockquote>
<h1>CodeQL Action Changelog</h1>
<p>See the <a href="https://github.com/github/codeql-action/releases">releases page</a> for the relevant changes to the CodeQL CLI and language packs.</p>
<h2>[UNRELEASED]</h2>
<p>No user facing changes.</p>
<h2>4.39.0 - 15 Oct 2026</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>4.38.3 - 08 Oct 2026</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
<h2>4.38.2 - 24 Sept 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.1">2.27.1</a>. <a href="">#4160</a></li>
</ul>
<h2>4.38.1 - 18 Sept 2026</h2>
<ul>
<li>The CodeQL Action now has experimental support for CodeQL releases for which per-language bundles are available. Per-language bundles support analysis for a single language and are therefore smaller than the combined bundles that allow analysis for all supported languages. As a result, per-language bundles take up less space on disk and are faster to download. We expect to roll this change out to everyone in the coming weeks. <a href="">#4146</a></li>
</ul>
<h2>4.38.0 - 09 Sept 2026</h2>
<ul>
<li>On GitHub-hosted runners, the CodeQL Action now deletes unused CodeQL bundles from the toolcache before downloading a different bundle, which frees up disk space for the analysis. We expect to roll this change out to everyone in September. <a href="">#4124</a></li>
<li>The CodeQL Action now supports CodeQL releases that are compatible with Linux Arm64 and downloads the native <code>linux-arm64</code> CodeQL bundle when available. <a href="">#4072</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.0">2.27.0</a>. <a href="">#4129</a></li>
</ul>
<h2>4.37.9 - 26 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.4">2.26.4</a>. <a href="">#4106</a></li>
</ul>
<h2>4.37.8 - 21 Aug 2026</h2>
<p>No user facing changes.</p>
<h2>4.37.7 - 13 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.3">2.26.3</a>. <a href="">#4085</a></li>
</ul>
<h2>4.37.6 - 04 Aug 2026</h2>
<ul>
<li>Changed the default filepath for the new remote file address format that was introduced in CodeQL Action 4.37.0 / 3.37.0 to <code>.github/codeql-config.yml</code> to align it with the suggested path that is used elsewhere. <a href="">#4070</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6f2ac81</code></a> Merge pull request <a href="">#4239</a> from github/update-v4.39.0-d63383a73</li>
<li><a href=""><code>eb1c428</code></a> Trigger workflows</li>
<li><a href=""><code>4443333</code></a> Update changelog for v4.39.0</li>
<li><a href=""><code>d63383a</code></a> Merge pull request <a href="">#4233</a> from github/mbg/start-proxy/report-version</li>
<li><a href=""><code>8dec0b9</code></a> Rename <code>path</code> to <code>result</code> in tests</li>
<li><a href=""><code>4eabea6</code></a> Merge remote-tracking branch 'origin/main' into mbg/start-proxy/report-version</li>
<li><a href=""><code>57938b8</code></a> Merge pull request <a href="">#4201</a> from github/mario-campos/automate-changenotes-assemble</li>
<li><a href=""><code>ee07b50</code></a> Merge pull request <a href="">#4236</a> from github/mbg/add-missing-changenotes</li>
<li><a href=""><code>a897ed5</code></a> Add change note for <a href="">#4206</a></li>
<li><a href=""><code>c8bd019</code></a> Add change note for <a href="">#4198</a></li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/2892aa5e19bbd11bc0cff5427e3b750a04d9e3c2...6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/analyze` from 4.38.2 to 4.39.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/analyze's releases</a>.</em></p>
<blockquote>
<h2>v4.39.0</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>v4.38.3</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/blob/main/CHANGELOG.md">github/codeql-action/analyze's changelog</a>.</em></p>
<blockquote>
<h1>CodeQL Action Changelog</h1>
<p>See the <a href="https://github.com/github/codeql-action/releases">releases page</a> for the relevant changes to the CodeQL CLI and language packs.</p>
<h2>[UNRELEASED]</h2>
<p>No user facing changes.</p>
<h2>4.39.0 - 15 Oct 2026</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>4.38.3 - 08 Oct 2026</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
<h2>4.38.2 - 24 Sept 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.1">2.27.1</a>. <a href="">#4160</a></li>
</ul>
<h2>4.38.1 - 18 Sept 2026</h2>
<ul>
<li>The CodeQL Action now has experimental support for CodeQL releases for which per-language bundles are available. Per-language bundles support analysis for a single language and are therefore smaller than the combined bundles that allow analysis for all supported languages. As a result, per-language bundles take up less space on disk and are faster to download. We expect to roll this change out to everyone in the coming weeks. <a href="">#4146</a></li>
</ul>
<h2>4.38.0 - 09 Sept 2026</h2>
<ul>
<li>On GitHub-hosted runners, the CodeQL Action now deletes unused CodeQL bundles from the toolcache before downloading a different bundle, which frees up disk space for the analysis. We expect to roll this change out to everyone in September. <a href="">#4124</a></li>
<li>The CodeQL Action now supports CodeQL releases that are compatible with Linux Arm64 and downloads the native <code>linux-arm64</code> CodeQL bundle when available. <a href="">#4072</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.0">2.27.0</a>. <a href="">#4129</a></li>
</ul>
<h2>4.37.9 - 26 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.4">2.26.4</a>. <a href="">#4106</a></li>
</ul>
<h2>4.37.8 - 21 Aug 2026</h2>
<p>No user facing changes.</p>
<h2>4.37.7 - 13 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.3">2.26.3</a>. <a href="">#4085</a></li>
</ul>
<h2>4.37.6 - 04 Aug 2026</h2>
<ul>
<li>Changed the default filepath for the new remote file address format that was introduced in CodeQL Action 4.37.0 / 3.37.0 to <code>.github/codeql-config.yml</code> to align it with the suggested path that is used elsewhere. <a href="">#4070</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6f2ac81</code></a> Merge pull request <a href="">#4239</a> from github/update-v4.39.0-d63383a73</li>
<li><a href=""><code>eb1c428</code></a> Trigger workflows</li>
<li><a href=""><code>4443333</code></a> Update changelog for v4.39.0</li>
<li><a href=""><code>d63383a</code></a> Merge pull request <a href="">#4233</a> from github/mbg/start-proxy/report-version</li>
<li><a href=""><code>8dec0b9</code></a> Rename <code>path</code> to <code>result</code> in tests</li>
<li><a href=""><code>4eabea6</code></a> Merge remote-tracking branch 'origin/main' into mbg/start-proxy/report-version</li>
<li><a href=""><code>57938b8</code></a> Merge pull request <a href="">#4201</a> from github/mario-campos/automate-changenotes-assemble</li>
<li><a href=""><code>ee07b50</code></a> Merge pull request <a href="">#4236</a> from github/mbg/add-missing-changenotes</li>
<li><a href=""><code>a897ed5</code></a> Add change note for <a href="">#4206</a></li>
<li><a href=""><code>c8bd019</code></a> Add change note for <a href="">#4198</a></li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/2892aa5e19bbd11bc0cff5427e3b750a04d9e3c2...6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee">compare view</a></li>
</ul>
</details>
<br />

Updates `ossf/scorecard-action` from 2.4.4 to 2.5.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ossf/scorecard-action/releases">ossf/scorecard-action's releases</a>.</em></p>
<blockquote>
<h2>v2.5.0</h2>
<h2>What's Changed</h2>
<p>This release moves the action to Scorecard v5.6.0, the first Scorecard release since its hosted
services moved to new infrastructure.</p>
<p>For changes to checks and results, and what the infrastructure move means for you, see the
<a href="https://github.com/ossf/scorecard/releases/tag/v5.6.0">Scorecard v5.6.0 release notes</a>.</p>
<ul>
<li>The action's container image is built with Go 1.27.2 on a refreshed distroless base. by
<a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>The installer (<code>cmd/installer</code>) now creates <code>.github/workflows/scorecard.yml</code>, and still
recognizes existing <code>scorecards.yml</code> and <code>scorecards-analysis.yml</code> workflows. by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>The Scorecard version in results now always matches the Scorecard release the action is built
with. by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1718</a></li>
<li>The action no longer prints the GitHub token variable while validating its options. by
<a href="https://github.com/arpitjain099"><code>@​arpitjain099</code></a> in <a href="">ossf/scorecard-action#1709</a></li>
<li><code>results_format</code> accepts <code>intoto</code>, which wraps the JSON results in an in-toto attestation
statement. by <a href="https://github.com/puerco"><code>@​puerco</code></a> in <a href="">ossf/scorecard-action#1702</a></li>
</ul>
<h3>Other</h3>
<ul>
<li>Add a daily canary against Scorecard main by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1711</a></li>
<li>Bump Scorecard to the v5.6.0 candidate and fix the canary toolchain by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1714</a></li>
<li>Run Scorecard on every merge, add a zizmor presubmit, analyze workflows with CodeQL, and update
RELEASE.md by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>Bump Scorecard to v5.6.0 by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1719</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/arpitjain099"><code>@​arpitjain099</code></a> made their first contribution in <a href="">ossf/scorecard-action#1709</a></li>
<li><a href="https://github.com/puerco"><code>@​puerco</code></a> made their first contribution in <a href="">ossf/scorecard-action#1702</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/ossf/scorecard-action/compare/v2.4.4...v2.5.0">https://github.com/ossf/scorecard-action/compare/v2.4.4...v2.5.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>fa7117d</code></a> Bump action tag for v2.5.0 release (<a href="">#1720</a>)</li>
<li><a href=""><code>cef4eb5</code></a> :seedling: Bump Scorecard to v5.6.0 (<a href="">#1719</a>)</li>
<li><a href=""><code>bedb16e</code></a> :sparkles: Add intoto results format (<a href="">#1702</a>)</li>
<li><a href=""><code>de70347</code></a> Remove the leftover debug print of the auth token (<a href="">#1709</a>)</li>
<li><a href=""><code>950873d</code></a> :seedling: Derive the reported Scorecard version from go.mod (<a href="">#1718</a>)</li>
<li><a href=""><code>2ce8ee4</code></a> :seedling: Bump github.com/sigstore/cosign/v2 from 2.6.4 to 2.6.5 (<a href="">#1695</a>)</li>
<li><a href=""><code>aabdf5a</code></a> :seedling: Bump the github-actions group across 1 directory with 7 updates (#...</li>
<li><a href=""><code>b4b9adf</code></a> :seedling: CodeQL: Analyze workflows instead of a placeholder JavaScript file</li>
<li><a href=""><code>4e9f2a2</code></a> :book: RELEASE.md: Document drafting release notes</li>
<li><a href=""><code>f618e8b</code></a> :seedling: Build the image with Go 1.27.2 and refresh distroless</li>
<li>Additional commits viewable in <a href="https://github.com/ossf/scorecard-action/compare/2d1146689b8cda280b9bc96326124645441f03bc...fa7117db83c52d787ae5a89f350999701505d78e">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/upload-sarif` from 4.38.2 to 4.39.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/upload-sarif's releases</a>.</em></p>
<blockquote>
<h2>v4.39.0</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>v4.38.3</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/blob/main/CHANGELOG.md">github/codeql-action/upload-sarif's changelog</a>.</em></p>
<blockquote>
<h1>CodeQL Action Changelog</h1>
<p>See the <a href="https://github.com/github/codeql-action/releases">releases page</a> for the relevant changes to the CodeQL CLI and language packs.</p>
<h2>[UNRELEASED]</h2>
<p>No user facing changes.</p>
<h2>4.39.0 - 15 Oct 2026</h2>
<ul>
<li><em>Breaking change</em>: Bump the minimum required CodeQL bundle version to 2.20.7. <a href="">#4205</a></li>
<li>The <code>codeql-action/analyze</code> step now validates that a correct argument for the <code>checkout_path</code> input has been provided. The <code>checkout_path</code> input must be set to the path where the repository that is being analyzed is checked out at on the runner, if that path is something other than the workspace root. If the path does not point to a repository checkout or is different from the path that was used by <code>codeql-action/init</code>, then the CodeQL Action now produces a warning. <a href="">#4148</a></li>
<li>Resolved an issue with third-party caching implementations that prevented caches from being restored correctly. <a href="">#4206</a></li>
<li>The <code>codeql-action/start-proxy</code> step that is used in Code Scanning Default Setup now finds CodeQL releases using the same logic as <code>codeql-action/init</code>. This primarily benefits customers who are using GitHub instances other than <code>github.com</code> where the <code>codeql-action/start-proxy</code> step may previously have been unable to locate recent releases and ended up using outdated versions of the private registry authentication proxy as a result. <a href="">#4198</a></li>
</ul>
<h2>4.38.3 - 08 Oct 2026</h2>
<ul>
<li><em>Upcoming breaking change</em>: CodeQL version 2.21.2 and earlier were discontinued on 24 September 2026 alongside GitHub Enterprise Server 3.17, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4188</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.2">2.27.2</a>. <a href="">#4203</a></li>
<li>Fixed a bug where the decision of whether to use a per-language bundle did not account for custom configurations that reference queries outside of compiled CodeQL packs. This issue was caught during internal testing and did not affect any customer repositories. We will resume the roll out of per-language bundles in the coming weeks. <a href="">#4184</a></li>
</ul>
<h2>4.38.2 - 24 Sept 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.1">2.27.1</a>. <a href="">#4160</a></li>
</ul>
<h2>4.38.1 - 18 Sept 2026</h2>
<ul>
<li>The CodeQL Action now has experimental support for CodeQL releases for which per-language bundles are available. Per-language bundles support analysis for a single language and are therefore smaller than the combined bundles that allow analysis for all supported languages. As a result, per-language bundles take up less space on disk and are faster to download. We expect to roll this change out to everyone in the coming weeks. <a href="">#4146</a></li>
</ul>
<h2>4.38.0 - 09 Sept 2026</h2>
<ul>
<li>On GitHub-hosted runners, the CodeQL Action now deletes unused CodeQL bundles from the toolcache before downloading a different bundle, which frees up disk space for the analysis. We expect to roll this change out to everyone in September. <a href="">#4124</a></li>
<li>The CodeQL Action now supports CodeQL releases that are compatible with Linux Arm64 and downloads the native <code>linux-arm64</code> CodeQL bundle when available. <a href="">#4072</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.0">2.27.0</a>. <a href="">#4129</a></li>
</ul>
<h2>4.37.9 - 26 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.4">2.26.4</a>. <a href="">#4106</a></li>
</ul>
<h2>4.37.8 - 21 Aug 2026</h2>
<p>No user facing changes.</p>
<h2>4.37.7 - 13 Aug 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.26.3">2.26.3</a>. <a href="">#4085</a></li>
</ul>
<h2>4.37.6 - 04 Aug 2026</h2>
<ul>
<li>Changed the default filepath for the new remote file address format that was introduced in CodeQL Action 4.37.0 / 3.37.0 to <code>.github/codeql-config.yml</code> to align it with the suggested path that is used elsewhere. <a href="">#4070</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6f2ac81</code></a> Merge pull request <a href="">#4239</a> from github/update-v4.39.0-d63383a73</li>
<li><a href=""><code>eb1c428</code></a> Trigger workflows</li>
<li><a href=""><code>4443333</code></a> Update changelog for v4.39.0</li>
<li><a href=""><code>d63383a</code></a> Merge pull request <a href="">#4233</a> from github/mbg/start-proxy/report-version</li>
<li><a href=""><code>8dec0b9</code></a> Rename <code>path</code> to <code>result</code> in tests</li>
<li><a href=""><code>4eabea6</code></a> Merge remote-tracking branch 'origin/main' into mbg/start-proxy/report-version</li>
<li><a href=""><code>57938b8</code></a> Merge pull request <a href="">#4201</a> from github/mario-campos/automate-changenotes-assemble</li>
<li><a href=""><code>ee07b50</code></a> Merge pull request <a href="">#4236</a> from github/mbg/add-missing-changenotes</li>
<li><a href=""><code>a897ed5</code></a> Add change note for <a href="">#4206</a></li>
<li><a href=""><code>c8bd019</code></a> Add change note for <a href="">#4198</a></li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/2892aa5e19bbd11bc0cff5427e3b750a04d9e3c2...6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee">compare view</a></li>
</ul>
</details>
<br />

Updates `trufflesecurity/trufflehog` from 3.97.9 to 3.99.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/trufflesecurity/trufflehog/releases">trufflesecurity/trufflehog's releases</a>.</em></p>
<blockquote>
<h2>v3.99.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Copy over dedupe cache size into the engine from the config by <a href="https://github.com/camgunz"><code>@​camgunz</code></a> in <a href="">trufflesecurity/trufflehog#5402</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.99.1...v3.99.2">https://github.com/trufflesecurity/trufflehog/compare/v3.99.1...v3.99.2</a></p>
<h2>v3.99.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Update github-actions by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5363</a></li>
<li>[INT-1084] Make the results deduplication cache size configurable by <a href="https://github.com/camgunz"><code>@​camgunz</code></a> in <a href="">trufflesecurity/trufflehog#5399</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.99.0...v3.99.1">https://github.com/trufflesecurity/trufflehog/compare/v3.99.0...v3.99.1</a></p>
<h2>v3.99.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix Sumo Logic detector ignoring configured verifier endpoints by <a href="https://github.com/unsmith"><code>@​unsmith</code></a> in <a href="">trufflesecurity/trufflehog#5395</a></li>
<li>Add OAuth2 (ROPC) auth for verification requests by <a href="https://github.com/unsmith"><code>@​unsmith</code></a> in <a href="">trufflesecurity/trufflehog#5392</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.98.1...v3.99.0">https://github.com/trufflesecurity/trufflehog/compare/v3.98.1...v3.99.0</a></p>
<h2>v3.98.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Add postman source documentation by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5389</a></li>
<li>Add a TruffleHog dectector for Kong Konnect Platform  by <a href="https://github.com/mrwanny"><code>@​mrwanny</code></a> in <a href="">trufflesecurity/trufflehog#5305</a></li>
<li>Add api_timeout_seconds to Gerrit source proto by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5394</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/mrwanny"><code>@​mrwanny</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5305</a></li>
</ul>
<p...

_Description has been truncated_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `257c9a721a83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.