# Issue

**Title:** ci: bump the actions group across 1 directory with 6 updates

## Description

Bumps the actions group with 6 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [step-security/harden-runner](https://github.com/step-security/harden-runner) | `2.22.1` | `2.22.2` |
| [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv) | `10.3.0` | `10.3.2` |
| [github/codeql-action/init](https://github.com/github/codeql-action) | `4.39.0` | `4.39.1` |
| [github/codeql-action/analyze](https://github.com/github/codeql-action) | `4.39.0` | `4.39.1` |
| [github/codeql-action/upload-sarif](https://github.com/github/codeql-action) | `4.39.0` | `4.39.1` |
| [trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog) | `3.99.2` | `3.99.7` |

Updates `step-security/harden-runner` from 2.22.1 to 2.22.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/step-security/harden-runner/releases">step-security/harden-runner's releases</a>.</em></p>
<blockquote>
<h2>v2.22.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Fixed inbound (ingress) network traffic being incorrectly classified as outbound (egress) traffic on macOS</li>
<li>Fixed implicit endpoints intended for self-hosted runners being applied to custom VM environments on Linux (enterprise tier)</li>
<li>Improved network and DNS tracing, enforcement logic, and process information correlation on Linux (enterprise tier)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/step-security/harden-runner/compare/v2.22.1...v2.22.2">https://github.com/step-security/harden-runner/compare/v2.22.1...v2.22.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dc2769a</code></a> Merge pull request <a href="">#707</a> from step-security/rc-45</li>
<li><a href=""><code>ab0b273</code></a> Merge pull request <a href="">#706</a> from h0x0er/rc-45</li>
<li><a href=""><code>03ccff8</code></a> Remove agent-preinstalled skip for third-party runners</li>
<li><a href=""><code>815e48d</code></a> Skip agent install and post-step cleanup when agent is already installed</li>
<li>See full diff in <a href="https://github.com/step-security/harden-runner/compare/ccd8616d44fd3846e67624a50d5aad6d37bf2d25...dc2769abcc0fcfbadfc1df54081c1608579ef6b2">compare view</a></li>
</ul>
</details>
<br />

Updates `astral-sh/setup-uv` from 10.3.0 to 10.3.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.3.2 🌈 update known checksums for 0.13.5</h2>
<h2>Changes</h2>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.5 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1103</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: update version references to v10.3.1 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1102</a>)</li>
</ul>
<h2>v10.3.1 🌈 preserve cache error class names in save-cache bundle</h2>
<h2>Changes</h2>
<p>This release includes a fix so that multiple concurrent workflows trying to upload the same cache no longer warn</p>
<p><code>##[warning]Failed to save: Unable to reserve cache with key ..., another job may be creating this cache.</code></p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>fix: preserve cache error class names in save-cache bundle <a href="https://github.com/dannyward630"><code>@​dannyward630</code></a> (<a href="">#1093</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.4 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1099</a>)</li>
<li>chore: update known checksums for 0.13.2/0.13.3 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1098</a>)</li>
<li>chore: update known checksums for 0.13.1 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1094</a>)</li>
<li>Verify npm dependency signatures before builds <a href="https://github.com/zaniebot"><code>@​zaniebot</code></a> (<a href="">#1027</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: cache-dependency-glob matches relative to the working directory <a href="https://github.com/flange-ipb"><code>@​flange-ipb</code></a> (<a href="">#1092</a>)</li>
<li>docs: update version references to v10.3.0 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1090</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1101</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>07a047e</code></a> chore: update known checksums for 0.13.5 (<a href="">#1103</a>)</li>
<li><a href=""><code>e1b8536</code></a> docs: update version references to v10.3.1 (<a href="">#1102</a>)</li>
<li><a href=""><code>18d369b</code></a> chore(deps): roll up Dependabot updates (<a href="">#1101</a>)</li>
<li><a href=""><code>4ad2329</code></a> chore: update known checksums for 0.13.4 (<a href="">#1099</a>)</li>
<li><a href=""><code>4bc6759</code></a> chore: update known checksums for 0.13.2/0.13.3 (<a href="">#1098</a>)</li>
<li><a href=""><code>c97f06e</code></a> fix: preserve cache error class names in save-cache bundle (<a href="">#1093</a>)</li>
<li><a href=""><code>8ca4be0</code></a> chore: update known checksums for 0.13.1 (<a href="">#1094</a>)</li>
<li><a href=""><code>b627d85</code></a> docs: cache-dependency-glob matches relative to the working directory (<a href="">#1092</a>)</li>
<li><a href=""><code>f8c8897</code></a> Verify npm dependency signatures before builds (<a href="">#1027</a>)</li>
<li><a href=""><code>f64d32b</code></a> docs: update version references to v10.3.0 (<a href="">#1090</a>)</li>
<li>See full diff in <a href="https://github.com/astral-sh/setup-uv/compare/1c37ad07a6a961277cf70c0d37d6f313000f5884...07a047e608db84b3d8c06cd9a7c7dcc9c355c18e">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/init` from 4.39.0 to 4.39.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/init's releases</a>.</em></p>
<blockquote>
<h2>v4.39.1</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
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
<h2>4.39.1 - 21 Oct 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9b32540</code></a> Merge pull request <a href="">#4257</a> from github/update-v4.39.1-c5a2f4b0f</li>
<li><a href=""><code>b5e1ed9</code></a> Trigger workflows</li>
<li><a href=""><code>20f5ec3</code></a> Update changelog for v4.39.1</li>
<li><a href=""><code>c5a2f4b</code></a> Merge pull request <a href="">#4245</a> from github/henrymercer/graduate-overlay-trap-caching</li>
<li><a href=""><code>61a5a80</code></a> Merge pull request <a href="">#4256</a> from github/update-bundle/codeql-bundle-v2.27.3</li>
<li><a href=""><code>3dd33f8</code></a> Merge pull request <a href="">#4249</a> from github/mbg/upload-improvements-for-4223</li>
<li><a href=""><code>b96e339</code></a> Change comment for <code>getConfig</code> call in <code>upload-sarif</code></li>
<li><a href=""><code>7fa4518</code></a> Use <code>shouldSkipSarifUpload</code> in <code>analyze-action.ts</code></li>
<li><a href=""><code>a69c7cb</code></a> Document that setting the env vars to <code>false</code> takes precedence</li>
<li><a href=""><code>74ddcd9</code></a> Fix typo in comment</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee...9b3254085494b55a0f7c4c2b3d2d52cc712ce370">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/analyze` from 4.39.0 to 4.39.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/analyze's releases</a>.</em></p>
<blockquote>
<h2>v4.39.1</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
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
<h2>4.39.1 - 21 Oct 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9b32540</code></a> Merge pull request <a href="">#4257</a> from github/update-v4.39.1-c5a2f4b0f</li>
<li><a href=""><code>b5e1ed9</code></a> Trigger workflows</li>
<li><a href=""><code>20f5ec3</code></a> Update changelog for v4.39.1</li>
<li><a href=""><code>c5a2f4b</code></a> Merge pull request <a href="">#4245</a> from github/henrymercer/graduate-overlay-trap-caching</li>
<li><a href=""><code>61a5a80</code></a> Merge pull request <a href="">#4256</a> from github/update-bundle/codeql-bundle-v2.27.3</li>
<li><a href=""><code>3dd33f8</code></a> Merge pull request <a href="">#4249</a> from github/mbg/upload-improvements-for-4223</li>
<li><a href=""><code>b96e339</code></a> Change comment for <code>getConfig</code> call in <code>upload-sarif</code></li>
<li><a href=""><code>7fa4518</code></a> Use <code>shouldSkipSarifUpload</code> in <code>analyze-action.ts</code></li>
<li><a href=""><code>a69c7cb</code></a> Document that setting the env vars to <code>false</code> takes precedence</li>
<li><a href=""><code>74ddcd9</code></a> Fix typo in comment</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee...9b3254085494b55a0f7c4c2b3d2d52cc712ce370">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/upload-sarif` from 4.39.0 to 4.39.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/upload-sarif's releases</a>.</em></p>
<blockquote>
<h2>v4.39.1</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
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
<h2>4.39.1 - 21 Oct 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.3">2.27.3</a>. <a href="">#4256</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9b32540</code></a> Merge pull request <a href="">#4257</a> from github/update-v4.39.1-c5a2f4b0f</li>
<li><a href=""><code>b5e1ed9</code></a> Trigger workflows</li>
<li><a href=""><code>20f5ec3</code></a> Update changelog for v4.39.1</li>
<li><a href=""><code>c5a2f4b</code></a> Merge pull request <a href="">#4245</a> from github/henrymercer/graduate-overlay-trap-caching</li>
<li><a href=""><code>61a5a80</code></a> Merge pull request <a href="">#4256</a> from github/update-bundle/codeql-bundle-v2.27.3</li>
<li><a href=""><code>3dd33f8</code></a> Merge pull request <a href="">#4249</a> from github/mbg/upload-improvements-for-4223</li>
<li><a href=""><code>b96e339</code></a> Change comment for <code>getConfig</code> call in <code>upload-sarif</code></li>
<li><a href=""><code>7fa4518</code></a> Use <code>shouldSkipSarifUpload</code> in <code>analyze-action.ts</code></li>
<li><a href=""><code>a69c7cb</code></a> Document that setting the env vars to <code>false</code> takes precedence</li>
<li><a href=""><code>74ddcd9</code></a> Fix typo in comment</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/6f2ac81f5cd81fe351a197ba0b00d91d03cd2aee...9b3254085494b55a0f7c4c2b3d2d52cc712ce370">compare view</a></li>
</ul>
</details>
<br />

Updates `trufflesecurity/trufflehog` from 3.99.2 to 3.99.7
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/trufflesecurity/trufflehog/releases">trufflesecurity/trufflehog's releases</a>.</em></p>
<blockquote>
<h2>v3.99.7</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix --include-wikis help typo and huggingface README description by <a href="https://github.com/protonnegativo"><code>@​protonnegativo</code></a> in <a href="">trufflesecurity/trufflehog#5471</a></li>
<li>fix(detectors/anypointoauth2): stop treating HTTP 422 as verified by <a href="https://github.com/jamesgol"><code>@​jamesgol</code></a> in <a href="">trufflesecurity/trufflehog#5386</a></li>
<li>Add xAI analyzer by <a href="https://github.com/serval-frenchie"><code>@​serval-frenchie</code></a> in <a href="">trufflesecurity/trufflehog#5456</a></li>
<li>ci(lint): pin the semgrep container image by digest by <a href="https://github.com/Portll"><code>@​Portll</code></a> in <a href="">trufflesecurity/trufflehog#5245</a></li>
<li>feat(detectors): add Fireworks AI API key detector by <a href="https://github.com/sudo-a-man"><code>@​sudo-a-man</code></a> in <a href="">trufflesecurity/trufflehog#5447</a></li>
<li>feat(detectors): add Infisical service token detector by <a href="https://github.com/Varshith-Kali"><code>@​Varshith-Kali</code></a> in <a href="">trufflesecurity/trufflehog#5445</a></li>
<li>Fix 7z and rar panics in the archive handler and log recovered panic stacks by <a href="https://github.com/dustin-decker"><code>@​dustin-decker</code></a> in <a href="">trufflesecurity/trufflehog#5474</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/protonnegativo"><code>@​protonnegativo</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5471</a></li>
<li><a href="https://github.com/serval-frenchie"><code>@​serval-frenchie</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5456</a></li>
<li><a href="https://github.com/Portll"><code>@​Portll</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5245</a></li>
<li><a href="https://github.com/sudo-a-man"><code>@​sudo-a-man</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5447</a></li>
<li><a href="https://github.com/Varshith-Kali"><code>@​Varshith-Kali</code></a> made their first contribution in <a href="">trufflesecurity/trufflehog#5445</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.99.6...v3.99.7">https://github.com/trufflesecurity/trufflehog/compare/v3.99.6...v3.99.7</a></p>
<h2>v3.99.6</h2>
<p>v3.99.5 was tagged but never published because its release build failed. v3.99.6 supersedes it and includes all of the changes below.</p>
<h2>What's Changed</h2>
<ul>
<li>Update github-actions by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5414</a></li>
<li>Prefer nearest client/tenant IDs for Azure SP secrets by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5449</a></li>
<li>Clean up Filesystem source logging for per-source debug by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5465</a></li>
<li>security: bump andybalholm/brotli to v1.2.7 (CVE-2026-111497) by <a href="https://github.com/dustin-decker"><code>@​dustin-decker</code></a> in <a href="">trufflesecurity/trufflehog#5472</a></li>
<li>Keep GoReleaser temp files off the tmpfs /tmp in releases by <a href="https://github.com/dustin-decker"><code>@​dustin-decker</code></a> in <a href="">trufflesecurity/trufflehog#5473</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.99.4...v3.99.6">https://github.com/trufflesecurity/trufflehog/compare/v3.99.4...v3.99.6</a></p>
<h2>v3.99.4</h2>
<h2>What's Changed</h2>
<ul>
<li>Add per-source debug option and hide sensitive data in debug logs by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5446</a></li>
<li>Mark results whose verification was skipped by <a href="https://github.com/unsmith"><code>@​unsmith</code></a> in <a href="">trufflesecurity/trufflehog#5448</a></li>
<li>Clean up Git source logging for per-source debug by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5451</a></li>
<li>Add Lambda Cloud API key detector by <a href="https://github.com/lukem-ts"><code>@​lukem-ts</code></a> in <a href="">trufflesecurity/trufflehog#5435</a></li>
<li>Update github.com/trufflesecurity/ldap-verify digest to 4a15faf by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5441</a></li>
<li>Update dependency trufflesecurity/.github to v1.0.5 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5442</a></li>
<li>Update module golang.org/x/crypto to v0.56.0 [SECURITY] by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5462</a></li>
<li>Update module golang.org/x/net to v0.60.0 [SECURITY] by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5464</a></li>
<li>Update module github.com/yuin/goldmark to v1.7.17 [SECURITY] by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5460</a></li>
<li>github: check App installation grants before listing comments by <a href="https://github.com/unsmith"><code>@​unsmith</code></a> in <a href="">trufflesecurity/trufflehog#5454</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/trufflesecurity/trufflehog/compare/v3.99.3...v3.99.4">https://github.com/trufflesecurity/trufflehog/compare/v3.99.3...v3.99.4</a></p>
<h2>v3.99.3</h2>
<h2>What's Changed</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>31ce31e</code></a> Fix 7z and rar panics in the archive handler and log recovered panic stacks (...</li>
<li><a href=""><code>50bc667</code></a> feat(detectors): add Infisical service token detector (<a href="">#5445</a>)</li>
<li><a href=""><code>4723140</code></a> feat(detectors): add Fireworks AI API key detector (<a href="">#5447</a>)</li>
<li><a href=""><code>8276bc4</code></a> ci(lint): pin the semgrep container image by digest (<a href="">#5245</a>)</li>
<li><a href=""><code>f6984be</code></a> Add xAI analyzer (<a href="">#5456</a>)</li>
<li><a href=""><code>282085c</code></a> fix(detectors/anypointoauth2): stop treating HTTP 422 as verified (<a href="">#5386</a>)</li>
<li><a href=""><code>b1bb823</code></a> Fix --include-wikis help typo and huggingface README description (<a href="">#5471</a>)</li>
<li><a href=""><code>fd43a88</code></a> Keep GoReleaser temp files off the tmpfs /tmp in releases (<a href="">#5473</a>)</li>
<li><a href=""><code>3bd461f</code></a> security: bump andybalholm/brotli to v1.2.7 (CVE-2026-111497) (<a href="">#5472</a>)</li>
<li><a href=""><code>d6ea4a5</code></a> Clean up Filesystem source logging for per-source debug (<a href="">#5465</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/trufflesecurity/trufflehog/compare/e76dff8a7e57d6df0c60ad8cbf5d5cba505a8fc9...31ce31ee1abbcc7dc8eee5764c17121c3044c8b2">compare view</a></li>
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

<!-- codesmith:footer -->
---
<a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/1955?autoLogin=true&ref=codesmith_pr_footer"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/view-with-codesmith-dark-v3.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/view-with-codesmith-light-v3.svg"><img alt="View with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/view-with-codesmith-dark-v3-3x.png" width="162" height="28"></picture></a> <a href="https://backend.blacksmith.sh/track/enable-autofix?expires=1795880986&installation_model_id=444357&pr_number=1955&ref=codesmith_pr_footer&repository=KalarisLabs%2Fresearch-agent-skills&return_to=https%3A%2F%2Fgithub.com%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F1955&signature=bc6841c320620db1ce5a8a65a52134f021caacae74ce5e1e099dc93c5a00c8e7"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-light.svg"><img alt="Autofix with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark-3x.png" width="190" height="28"></picture></a>
<sup>Need help on this PR? Tag <code>@codesmith-bot</code> with what you need.</sup>

<!-- codesmith:autofix:disabled -->
<!-- /codesmith:footer -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0ee35abfd7e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.