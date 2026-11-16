# Issue

**Title:** ci: bump the actions group across 1 directory with 9 updates

## Description

Bumps the actions group with 9 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [step-security/harden-runner](https://github.com/step-security/harden-runner) | `2.22.2` | `2.22.3` |
| [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv) | `10.2.0` | `10.3.3` |
| [actions/upload-artifact](https://github.com/actions/upload-artifact) | `7.0.1` | `7.0.2` |
| [github/codeql-action/init](https://github.com/github/codeql-action) | `4.39.1` | `4.39.3` |
| [github/codeql-action/analyze](https://github.com/github/codeql-action) | `4.39.1` | `4.39.3` |
| [actions/setup-python](https://github.com/actions/setup-python) | `5.4.0` | `7.1.0` |
| [sigstore/cosign-installer](https://github.com/sigstore/cosign-installer) | `4.1.2` | `4.1.3` |
| [github/codeql-action/upload-sarif](https://github.com/github/codeql-action) | `4.39.1` | `4.39.3` |
| [trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog) | `3.99.7` | `3.99.8` |

Updates `step-security/harden-runner` from 2.22.2 to 2.22.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/step-security/harden-runner/releases">step-security/harden-runner's releases</a>.</em></p>
<blockquote>
<h2>v2.22.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Added support for Avrea-hosted runners (enterprise tier)</li>
<li>Fixed unexpected blocking of allowed connections caused by GitHub’s DNS resolver and outbound proxy experiment on GitHub-hosted Linux runners</li>
<li>Added a feature flag to disable implicit AWS endpoint allowances on self-hosted Linux runners (enterprise tier)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/step-security/harden-runner/compare/v2.22.2...v2.22.3">https://github.com/step-security/harden-runner/compare/v2.22.2...v2.22.3</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>46b06ce</code></a> Merge pull request <a href="">#711</a> from step-security/rc-46</li>
<li><a href=""><code>f82eb4b</code></a> Merge pull request <a href="">#710</a> from h0x0er/jatin/tp-avrea</li>
<li><a href=""><code>665b85a</code></a> update agent-self-hosted, agent-bravo to v1.9.5 and agent to v0.18.0</li>
<li><a href=""><code>80fffe1</code></a> detect avrea runners</li>
<li>See full diff in <a href="https://github.com/step-security/harden-runner/compare/dc2769abcc0fcfbadfc1df54081c1608579ef6b2...46b06cea07f9e64621fdf066ba77ac6915163d43">compare view</a></li>
</ul>
</details>
<br />

Updates `astral-sh/setup-uv` from 10.2.0 to 10.3.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.3.3 🌈 Use Astral mirror for version manifests with GitHub fallback</h2>
<h2>Changes</h2>
<p>This release contains something that should have been included a very long time ago. Sorry for sleeping on that.</p>
<p>This action now retrieves the release manifest that contains the available versions, their download links and checksums from the Astral mirror, rather than trying GitHub first. This should present much more stable.
(Known checksums are still checked, so the security impact does not change)</p>
<p>Also a big thank you to <a href="https://github.com/soujasK"><code>@​soujasK</code></a> for a set of bugfixes 👏</p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>Use Astral mirror for version manifests with GitHub fallback <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1119</a>)</li>
<li>fix: allow whitespace in uv requirement specifiers <a href="https://github.com/soujasK"><code>@​soujasK</code></a> (<a href="">#1112</a>)</li>
<li>fix: resolve ~= specifiers with PEP 440 semantics <a href="https://github.com/soujasK"><code>@​soujasK</code></a> (<a href="">#1111</a>)</li>
<li>fix: only report a saved cache when saving succeeded <a href="https://github.com/soujasK"><code>@​soujasK</code></a> (<a href="">#1110</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.6 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1117</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: use JSDoc for compatible release specifier comment <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1113</a>)</li>
<li>docs: update version references to v10.3.2 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1104</a>)</li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>68559e9</code></a> Use Astral mirror for version manifests with GitHub fallback (<a href="">#1119</a>)</li>
<li><a href=""><code>0192b69</code></a> chore: update known checksums for 0.13.6 (<a href="">#1117</a>)</li>
<li><a href=""><code>2f29784</code></a> docs: use JSDoc for compatible release specifier comment (<a href="">#1113</a>)</li>
<li><a href=""><code>9c73321</code></a> fix: allow whitespace in uv requirement specifiers (<a href="">#1112</a>)</li>
<li><a href=""><code>80fbe01</code></a> fix: resolve ~= specifiers with PEP 440 semantics (<a href="">#1111</a>)</li>
<li><a href=""><code>36b7b57</code></a> fix: only report a saved cache when saving succeeded (<a href="">#1110</a>)</li>
<li><a href=""><code>56618ca</code></a> docs: update version references to v10.3.2 (<a href="">#1104</a>)</li>
<li><a href=""><code>07a047e</code></a> chore: update known checksums for 0.13.5 (<a href="">#1103</a>)</li>
<li><a href=""><code>e1b8536</code></a> docs: update version references to v10.3.1 (<a href="">#1102</a>)</li>
<li><a href=""><code>18d369b</code></a> chore(deps): roll up Dependabot updates (<a href="">#1101</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/setup-uv/compare/v10.2.0...68559e99cc807c1eb7e9238fd43a15bba460eec2">compare view</a></li>
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
<li>See full diff in <a href="https://github.com/actions/upload-artifact/compare/v7.0.1...cf430e030ddbb5b0abf93d22962f4752f3646cd9">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/init` from 4.39.1 to 4.39.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/init's releases</a>.</em></p>
<blockquote>
<h2>v4.39.3</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>v4.39.2</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
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
<h2>4.39.3 - 04 Nov 2026</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>4.39.2 - 03 Nov 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>33d7b85</code></a> Merge pull request <a href="">#4299</a> from github/update-v4.39.3-064910ba2</li>
<li><a href=""><code>24393f8</code></a> Update changelog for v4.39.3</li>
<li><a href=""><code>064910b</code></a> Merge pull request <a href="">#4297</a> from github/mbg/update-glob</li>
<li><a href=""><code>f532ac5</code></a> Update <code>glob</code> to <code>14.0.3</code></li>
<li><a href=""><code>8cd4dfa</code></a> Merge pull request <a href="">#4280</a> from github/mbg/ci/validate-yaml</li>
<li><a href=""><code>cea289b</code></a> Return different exit code when a language is not recognised</li>
<li><a href=""><code>7287bb3</code></a> Remove <code>exclude</code> entry that's no longer needed</li>
<li><a href=""><code>8eb7cdf</code></a> Use normal <code>.editorconfig</code> pattern</li>
<li><a href=""><code>160e547</code></a> Merge remote-tracking branch 'origin/main' into mbg/ci/validate-yaml</li>
<li><a href=""><code>913e1bb</code></a> Merge pull request <a href="">#4283</a> from github/sam-robson/decode-diff-informed-sarif-uris</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/9b3254085494b55a0f7c4c2b3d2d52cc712ce370...33d7b85da1a04171e211befe2c739303b9a4c066">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/analyze` from 4.39.1 to 4.39.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/analyze's releases</a>.</em></p>
<blockquote>
<h2>v4.39.3</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>v4.39.2</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
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
<h2>4.39.3 - 04 Nov 2026</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>4.39.2 - 03 Nov 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>33d7b85</code></a> Merge pull request <a href="">#4299</a> from github/update-v4.39.3-064910ba2</li>
<li><a href=""><code>24393f8</code></a> Update changelog for v4.39.3</li>
<li><a href=""><code>064910b</code></a> Merge pull request <a href="">#4297</a> from github/mbg/update-glob</li>
<li><a href=""><code>f532ac5</code></a> Update <code>glob</code> to <code>14.0.3</code></li>
<li><a href=""><code>8cd4dfa</code></a> Merge pull request <a href="">#4280</a> from github/mbg/ci/validate-yaml</li>
<li><a href=""><code>cea289b</code></a> Return different exit code when a language is not recognised</li>
<li><a href=""><code>7287bb3</code></a> Remove <code>exclude</code> entry that's no longer needed</li>
<li><a href=""><code>8eb7cdf</code></a> Use normal <code>.editorconfig</code> pattern</li>
<li><a href=""><code>160e547</code></a> Merge remote-tracking branch 'origin/main' into mbg/ci/validate-yaml</li>
<li><a href=""><code>913e1bb</code></a> Merge pull request <a href="">#4283</a> from github/sam-robson/decode-diff-informed-sarif-uris</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/9b3254085494b55a0f7c4c2b3d2d52cc712ce370...33d7b85da1a04171e211befe2c739303b9a4c066">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/setup-python` from 5.4.0 to 7.1.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/setup-python/releases">actions/setup-python's releases</a>.</em></p>
<blockquote>
<h2>v7.1.0</h2>
<h2>What's Changed</h2>
<h3>Enhancements</h3>
<ul>
<li>Add <code>mirror</code> and <code>mirror-token</code> inputs for custom Python distribution sources by <a href="https://github.com/luhenry"><code>@​luhenry</code></a> in <a href="">actions/setup-python#1302</a></li>
<li>Improve error message clarity by <a href="https://github.com/v-lmvysakh"><code>@​v-lmvysakh</code></a> in <a href="">actions/setup-python#1351</a></li>
</ul>
<h3>Dependency Upgrade</h3>
<ul>
<li>Upgrade browserslist from 4.28.2 to 4.28.9 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1353</a></li>
<li>Upgrade <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1343</a></li>
<li>Upgrade eslint-plugin-jest from 29.15.2 to 29.16.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1342</a></li>
<li>Upgrade <code>@​vercel/ncc</code> from 0.44.0 to 0.45.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1357</a></li>
<li>Upgrade <code>@​types/semver</code> from 7.7.1 to 7.8.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1359</a></li>
<li>Upgrade undici from 6.28.0 to 6.29.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1364</a></li>
<li>Upgrade ts-jest from 29.4.11 to 29.4.14 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1361</a></li>
<li>Upgrade brace-expansion from 5.0.9 to 5.0.12 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1365</a></li>
<li>Upgrade prettier from 3.8.4 to 3.9.9 and package.json from 7.0.0 to 7.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1363</a></li>
<li>Upgrade <code>@​typescript-eslint/eslint-plugin</code> from 8.62.0 to 8.71.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1369</a></li>
<li>Upgrade actions/checkout from 7.0.0 to 7.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1345</a></li>
<li>Upgrade cache to 6.3.0 by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1370</a></li>
<li>Resolve Basic Validation audit failures by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1347</a></li>
<li>Resolve npm audit failures by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1350</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/luhenry"><code>@​luhenry</code></a> made their first contribution in <a href="">actions/setup-python#1302</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-python/compare/v7.0.0...v7.1.0">https://github.com/actions/setup-python/compare/v7.0.0...v7.1.0</a></p>
<h2>v7.0.0</h2>
<h2>What's Changed</h2>
<h3>Enhancements</h3>
<ul>
<li>Migrate to ESM and upgrade dependencies by <a href="https://github.com/priyagupta108"><code>@​priyagupta108</code></a> in <a href="">actions/setup-python#1330</a></li>
<li>Pin SHA commits and update docs with latest versions by <a href="https://github.com/HarithaVattikuti"><code>@​HarithaVattikuti</code></a> in <a href="">actions/setup-python#1338</a></li>
<li>Remove the pip-install input by <a href="https://github.com/gowridurgad"><code>@​gowridurgad</code></a> in <a href="">actions/setup-python#1336</a></li>
</ul>
<h3>Bug Fix</h3>
<ul>
<li>Fix to Classify stderr warning messages as warnings instead of errors in annotations by <a href="https://github.com/lmvysakh"><code>@​lmvysakh</code></a> in <a href="">actions/setup-python#1335</a></li>
<li>Validate and retry manifest fetch to prevent silent failures by <a href="https://github.com/priyagupta108"><code>@​priyagupta108</code></a> in <a href="">actions/setup-python#1332</a></li>
</ul>
<h3>Dependency Upgrade</h3>
<ul>
<li>Bump certifi from 2020.6.20 to 2024.7.4 in /<strong>tests</strong>/data by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1328</a></li>
<li>Remove EOL Python versions and Bumps numpy text fixture by <a href="https://github.com/priya-kinthali"><code>@​priya-kinthali</code></a> in <a href="">actions/setup-python#1333</a></li>
<li>Upgrade <code>@​actions/cache</code> to 6.2.0 by <a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> in <a href="">actions/setup-python#1337</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/lmvysakh"><code>@​lmvysakh</code></a> made their first contribution in <a href="">actions/setup-python#1335</a></li>
<li><a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> made their first contribution in <a href="">actions/setup-python#1337</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6d4fd22</code></a> Cache upgrade to 6.3.0 (<a href="">#1370</a>)</li>
<li><a href=""><code>ec52d0a</code></a> Bump <code>@​typescript-eslint/eslint-plugin</code> from 8.62.0 to 8.71.1 (<a href="">#1369</a>)</li>
<li><a href=""><code>ff73b24</code></a> Bump prettier from 3.8.4 to 3.9.9 and package.json from 7.0.0 to 7.1.0 (<a href="">#1363</a>)</li>
<li><a href=""><code>0e40890</code></a> Bump brace-expansion from 5.0.9 to 5.0.12 (<a href="">#1365</a>)</li>
<li><a href=""><code>3892123</code></a> Bump ts-jest from 29.4.11 to 29.4.14 (<a href="">#1361</a>)</li>
<li><a href=""><code>6609657</code></a> Bump undici from 6.28.0 to 6.29.0 (<a href="">#1364</a>)</li>
<li><a href=""><code>e1be392</code></a> Bump <code>@​types/semver</code> from 7.7.1 to 7.8.0 (<a href="">#1359</a>)</li>
<li><a href=""><code>06da627</code></a> Bump <code>@​vercel/ncc</code> from 0.44.0 to 0.45.0 (<a href="">#1357</a>)</li>
<li><a href=""><code>af9bcc7</code></a> Bump eslint-plugin-jest from 29.15.2 to 29.16.6 (<a href="">#1342</a>)</li>
<li><a href=""><code>7aeabeb</code></a> Bump <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 (<a href="">#1343</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/setup-python/compare/42375524e23c412d93fb67b49958b491fce71c38...6d4fd22b20465ccc0f7354476588e8df7c9ca0e0">compare view</a></li>
</ul>
</details>
<br />

Updates `sigstore/cosign-installer` from 4.1.2 to 4.1.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sigstore/cosign-installer/releases">sigstore/cosign-installer's releases</a>.</em></p>
<blockquote>
<h2>v4.1.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Bump Cosign to v3.1.4 (latest release) in <a href="">sigstore/cosign-installer#257</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/sigstore/cosign-installer/compare/v4.1.2...v4.1.3">https://github.com/sigstore/cosign-installer/compare/v4.1.2...v4.1.3</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>756fe2d</code></a> Bump Cosign to v3.1.4 (latest release) (<a href="">#257</a>)</li>
<li><a href=""><code>b9c3539</code></a> Bump actions/setup-go from 6.4.0 to 7.0.0 (<a href="">#249</a>)</li>
<li><a href=""><code>84205a0</code></a> close race on windows due to reusing filename (<a href="">#253</a>)</li>
<li><a href=""><code>af595e6</code></a> Bump cosign to 3.1.3 (<a href="">#252</a>)</li>
<li><a href=""><code>828df1e</code></a> fix: harden curl download retries against transient GitHub CDN 504s (<a href="">#240</a>)</li>
<li><a href=""><code>874852d</code></a> Bump actions/checkout from 6.0.2 to 7.0.1 (<a href="">#250</a>)</li>
<li><a href=""><code>3094a48</code></a> wrap path in quotes for powershell (<a href="">#246</a>)</li>
<li><a href=""><code>e246ae3</code></a> test minimum of 1.26 given cosign requirement (<a href="">#247</a>)</li>
<li>See full diff in <a href="https://github.com/sigstore/cosign-installer/compare/6f9f17788090df1f26f669e9d70d6ae9567deba6...756fe2d284c7292c4e9b62c8a28f1e5629c59532">compare view</a></li>
</ul>
</details>
<br />

Updates `github/codeql-action/upload-sarif` from 4.39.1 to 4.39.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action/upload-sarif's releases</a>.</em></p>
<blockquote>
<h2>v4.39.3</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>v4.39.2</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
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
<h2>4.39.3 - 04 Nov 2026</h2>
<ul>
<li>Fixed diff-informed alert filtering incorrectly removing alerts in changed files whose paths contain spaces, special characters, or non-ASCII characters. <a href="">#4283</a></li>
</ul>
<h2>4.39.2 - 03 Nov 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.27.4">2.27.4</a>. <a href="">#4284</a></li>
<li><em>Upcoming breaking change</em>: CodeQL version 2.22.3 and earlier were discontinued on 16 October 2026 alongside GitHub Enterprise Server 3.18, and will be unsupported by the next minor release of the CodeQL Action. Added a deprecation warning for customers using these versions of CodeQL. <a href="">#4266</a></li>
<li>Starting with macOS 27 and Xcode 27, traced analyses are unsupported. See <a href="https://github.blog/changelog/2026-10-19-codeql-changes-for-macos-27-xcode-27-and-swift-6-4/">this blog post for more information</a>. The CodeQL Action will now try to identify if a workflow is about to perform a traced analysis on version 27 or above of macOS or Xcode. If so, the CodeQL Action will emit a corresponding warning that will also be visible on the <a href="https://docs.github.com/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/use-the-tools-status-page-for-code-scanning">Tool Status Page</a>. This check will be rolled out following this release of the CodeQL Action. <a href="">#4221</a></li>
<li>The undocumented TRAP cache cleanup feature that could be enabled using the <code>CODEQL_ACTION_CLEANUP_TRAP_CACHES</code> environment variable has been removed, as announced in the release notes for CodeQL Action 4.35.2. The <code>analyze</code> Action now warns if this environment variable is set. If you used TRAP cache cleanup to limit Actions cache usage, we recommend disabling TRAP caching by passing the <code>trap-caching: false</code> input to the <code>init</code> Action. <a href="">#4243</a></li>
</ul>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>33d7b85</code></a> Merge pull request <a href="">#4299</a> from github/update-v4.39.3-064910ba2</li>
<li><a href=""><code>24393f8</code></a> Update changelog for v4.39.3</li>
<li><a href=""><code>064910b</code></a> Merge pull request <a href="">#4297</a> from github/mbg/update-glob</li>
<li><a href=""><code>f532ac5</code></a> Update <code>glob</code> to <code>14.0.3</code></li>
<li><a href=""><code>8cd4dfa</code></a> Merge pull request <a href="">#4280</a> from github/mbg/ci/validate-yaml</li>
<li><a href=""><code>cea289b</code></a> Return different exit code when a language is not recognised</li>
<li><a href=""><code>7287bb3</code></a> Remove <code>exclude</code> entry that's no longer needed</li>
<li><a href=""><code>8eb7cdf</code></a> Use normal <code>.editorconfig</code> pattern</li>
<li><a href=""><code>160e547</code></a> Merge remote-tracking branch 'origin/main' into mbg/ci/validate-yaml</li>
<li><a href=""><code>913e1bb</code></a> Merge pull request <a href="">#4283</a> from github/sam-robson/decode-diff-informed-sarif-uris</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/9b3254085494b55a0f7c4c2b3d2d52cc712ce370...33d7b85da1a04171e211befe2c739303b9a4c066">compare view</a></li>
</ul>
</details>
<br />

Updates `trufflesecurity/trufflehog` from 3.99.7 to 3.99.8
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/trufflesecurity/trufflehog/releases">trufflesecurity/trufflehog's releases</a>.</em></p>
<blockquote>
<h2>v3.99.8</h2>
<h2>What's Changed</h2>
<ul>
<li>Skip GitHub comment errors when issues or PRs are off by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5467</a></li>
<li>[SCAN-180]: Populate SecretParts for custom detector results by <a href="https://github.com/casey-tran"><code>@​casey-tran</code></a> in <a href="">trufflesecurity/trufflehog#5470</a></li>
<li>Clean up S3 source logging for per-source debug by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5481</a></li>
<li>Clean up GitHub source logging for per-source debug by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5457</a></li>
<li>feat(detectors): add Composio API key detector by <a href="https://github.com/groovyBugify"><code>@​groovyBugify</code></a> in <a href="">trufflesecurity/trufflehog#5322</a></li>
<li>Clean up Docker source logging for per-source debug by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5494</a></li>
<li>Add source fields to Init logs in single-source CLI commands by <a href="https://github.com/kashifkhan0771"><code>@​kashifkhan0771</code></a> in <a href="">trufflesecurity/trufflehog#5466</a></li>
<li>Close Couchbase clusters after verification and honor the context by <a href="https://github.com/unsmith"><code>@​unsmith</code></a> in <a href="">trufflesecurity/trufflehog#5489</a></li>
<li>[SCAN-317] Recover from detector panics in the verification overlap worker by <a href="https://github.com/dipto-truffle"><code>@​dipto-truffle</code></a> in <a href="">trufflesecurity/trufflehog#5495</a></li>
<li>Cap 7z LZMA and LZMA2 dictionary sizes and keep scanning past refused entries by <a href="https://github.com/bryanbeverly"><code>@​bryanbeverly</code></a> in <a href="">trufflesecurity/trufflehog#5483</a></li>
<li>Update module github.com/go-git/go-git/v5 to v5.19.3 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5480</a></li>
<li>Update module github.com/jlaffaye/ftp to v0.2.4 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="">trufflesecurity/trufflehog#5365</a></li>
<li>Update module github.com/mattn/go-isatty to v0.0.24 by <a href="https://github.com/renovate"><code>@​renovate</code></a>[bot] in <a href="...

_Description has been truncated_

<!-- codesmith:footer -->
---
<a href="https://backend.blacksmith.sh/track/enable-autofix?expires=1796628167&installation_model_id=444357&pr_number=2018&ref=codesmith_pr_footer&repository=KalarisLabs%2Fresearch-agent-skills&return_to=https%3A%2F%2Fgithub.com%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2018&signature=92a2ea5a27d93b1b3c76775b98eb2942815611474d11871173a13548fadac74f"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-light.svg"><img alt="Autofix with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark-3x.png" width="190" height="28"></picture></a>
<sup><a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/2018?autoLogin=true&ref=codesmith_pr_footer">Open in [code]smith</a> · Need help on this PR? Tag <code>@codesmith-bot</code> with what you need.</sup>

<!-- codesmith:autofix:disabled -->
<!-- /codesmith:footer -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29fe36d26127`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.