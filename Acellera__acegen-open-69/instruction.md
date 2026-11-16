# Issue

**Title:** Bump the python-minor-and-patch group with 3 updates

## Description

Bumps the python-minor-and-patch group with 3 updates: [hydra-core](https://github.com/facebookresearch/hydra), [wandb](https://github.com/wandb/wandb) and [rdkit](https://github.com/rdkit/rdkit).

Updates `hydra-core` from 1.3.4 to 1.3.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebookresearch/hydra/releases">hydra-core's releases</a>.</em></p>
<blockquote>
<h2>Hydra 1.3.5</h2>
<h2>What's Changed</h2>
<ul>
<li>Warn Hydra 1.3 users relying on Hydra 1.1 behavior  (<a href="">#3347</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/facebookresearch/hydra/compare/v1.3.4...v1.3.5">https://github.com/facebookresearch/hydra/compare/v1.3.4...v1.3.5</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/hydra-ecosystem/hydra/blob/v1.3.5/NEWS.md">hydra-core's changelog</a>.</em></p>
<blockquote>
<h1>1.3.5 (2026-08-06)</h1>
<h3>API Change (Renames, deprecations and removals)</h3>
<ul>
<li>Warn Hydra 1.3 applications that rely on Hydra 1.1 compatibility before
upgrading to Hydra 1.4. (<a href="">#3334</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>51647a2</code></a> Release Hydra 1.3.5</li>
<li><a href=""><code>445b0a7</code></a> Warn Hydra 1.3 users relying on 1.1 compatibility (<a href="">#3347</a>)</li>
<li>See full diff in <a href="https://github.com/facebookresearch/hydra/compare/v1.3.4...v1.3.5">compare view</a></li>
</ul>
</details>
<br />

Updates `wandb` from 0.28.1 to 0.28.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/releases">wandb's releases</a>.</em></p>
<blockquote>
<h2>v0.28.2</h2>
<h2>What's Changed</h2>
<h2>Notable Changes</h2>
<p>The <code>wandb sync --clean</code> command now exits with code 1 and prints a hint to use <code>wandb clean</code>, which is the replacement.
<code>wandb login</code> now verifies credentials by default. This can be disabled with <code>wandb login --no-verify</code> or programmatically with <code>wandb.login(verify=False)</code>.</p>
<h2>Added</h2>
<ul>
<li>Added support for gzip compression of filestream requests, reducing network traffic when logging metrics. It is currently opt-in and requires server support: set <code>x_file_stream_no_gzip=False</code> in <code>wandb.Settings</code> to enable it. Compression will become the default in a future release (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12262</a>)</li>
<li>Added a <code>--term-timeout</code> flag to <code>wandb agent</code> (<a href="https://github.com/nathancy-wandb"><code>@​nathancy-wandb</code></a> in <a href="">wandb/wandb#12246</a>)</li>
<li>Added <code>run.sync_dir</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12319</a>)</li>
</ul>
<h2>Changed</h2>
<ul>
<li>The new <code>wandb clean</code> command replaces <code>wandb sync --clean</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12238</a>)</li>
<li>Hardened argument handling in <code>wandb launch</code> for the local-process resource so that job-supplied values are always shell-quoted (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12220</a>)</li>
<li>The launch agent now restricts a job's git source URL to https/ssh remotes and pins git's protocol allowlist when fetching it and updating submodules (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12221</a>)</li>
<li>Response parsing is now faster for many <code>wandb.Api</code> operations, including artifact and registry queries (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12213</a>)</li>
<li><code>wandb.init()</code> now reports the error it was retrying (such as a network error) when it times out, instead of a generic timeout message. The <code>init_timeout</code> setting now also bounds the backend's retries during run initialization (<a href="https://github.com/skhanna-cw"><code>@​skhanna-cw</code></a> in <a href="">wandb/wandb#12216</a>)</li>
<li><code>wandb.Api().create_run_queue()</code>, <code>wandb.Api().create_custom_chart()</code>, and <code>wandb.Api().upsert_run_queue()</code> now raise <code>WandbApiFailedError</code> when the operation fails on the backend. (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12307</a>)</li>
<li>Paginated artifact and registry query methods (<code>Api.artifacts()</code>, <code>Api.artifact_collections()</code>, <code>Api.registries()</code>, <code>Registries.collections()</code>, <code>Registries.versions()</code>, <code>Collections.versions()</code>, <code>Registry.collections()</code>, <code>Registry.versions()</code>, <code>Project.collections()</code>) now perform client-side validation of pagination arguments before attempting to fetch any results (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12101</a>)</li>
<li>Ordered registry search now scopes per-registry collection and version queries to the current registry's internal id for more reliable pagination and filtering (<a href="https://github.com/ibindlish"><code>@​ibindlish</code></a> in <a href="">wandb/wandb#12188</a>)</li>
</ul>
<h2>Deprecated</h2>
<ul>
<li><code>wandb sync --sync-tensorboard</code> is deprecated and will be removed in a later release (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12419</a>)</li>
</ul>
<h2>Removed</h2>
<ul>
<li>Releases no longer include 32-bit Windows (<code>win32</code>) wheels; use 64-bit Python on Windows (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12267</a>)</li>
</ul>
<h2>Fixed</h2>
<ul>
<li>Registry search <code>registries(order=...).collections(order=...).versions()</code> now returns artifact versions in registry and/or collection order. (<a href="https://github.com/ibindlish"><code>@​ibindlish</code></a> in <a href="">wandb/wandb#12154</a>)</li>
<li>macOS x86_64 wheels now contain x86_64 builds of the <code>wandb-xpu</code> binary and the Rust parquet library, which previously shipped as arm64 and could not run or be loaded on Intel Macs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12267</a>)</li>
<li><code>wandb.login(verify=True)</code> and <code>wandb login --verify</code> now verify federated identity (identity token) credentials, which were previously not verified (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12294</a>)</li>
<li><code>wandb login</code> and <code>wandb verify</code> no longer update the system host settings when failing to login (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12332</a>)</li>
<li><code>wandb verify</code> now reports a failed check instead of crashing when an operation still fails after retries (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12360</a>)</li>
<li>Calling Sweeps agent with a custom <code>WANDB_DIR</code> will now respect it when dumping JSON output (<a href="https://github.com/kelu-wandb"><code>@​kelu-wandb</code></a> in <a href="">wandb/wandb#12344</a>)</li>
<li>Fixed <code>wandb.Api(overrides={&quot;base_url&quot;: ...})</code> failing to authenticate with federated identity (identity token) credentials when the specified server was not the default one, such as a dedicated cloud deployment, unless <code>WANDB_BASE_URL</code> was also set (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12340</a>)</li>
<li>When using federated identity, the identity token file is now re-read for each access token exchange instead of once at startup, so short-lived identity tokens re-minted to the same path keep working for runs that outlive them (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12341</a>)</li>
<li>When using federated identity, requests now fail immediately with the server's error message when the server rejects the identity token exchange, such as for an invalid or expired identity token. Previously, the rejected exchange was retried until requests timed out with a generic error (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12366</a>)</li>
<li><code>wandb login</code> validates api keys prior to saving to the <code>.netrc</code> file (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12347</a>)</li>
<li>The <code>global_step</code> metric created when syncing TensorBoard files is no longer prefixed, like <code>train/global_step</code>, so that it is easier to compare training and validation metrics (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12372</a>)</li>
<li>The TensorBoard integration now produces fewer W&amp;B steps by merging data for the same <code>global_step</code> into one W&amp;B step when possible (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12414</a>)</li>
<li><code>wandb sync</code> no longer hangs on a run that set its name, tags, or notes after starting (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12380</a>)</li>
<li><code>wandb login</code> no longer removes or corrupts credentials belonging to other machines in your <code>.netrc</code> file (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12386</a>)</li>
<li>Log messages captured from Python loggers no longer add blank lines to a run's logs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12387</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/blob/main/CHANGELOG.md">wandb's changelog</a>.</em></p>
<blockquote>
<h2>[0.28.2] - 2026-08-12</h2>
<h2>Notable Changes</h2>
<p>The <code>wandb sync --clean</code> command now exits with code 1 and prints a hint to use <code>wandb clean</code>, which is the replacement.
<code>wandb login</code> now verifies credentials by default. This can be disabled with <code>wandb login --no-verify</code> or programmatically with <code>wandb.login(verify=False)</code>.</p>
<h2>Added</h2>
<ul>
<li>Added support for gzip compression of filestream requests, reducing network traffic when logging metrics. It is currently opt-in and requires server support: set <code>x_file_stream_no_gzip=False</code> in <code>wandb.Settings</code> to enable it. Compression will become the default in a future release (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12262</a>)</li>
<li>Added a <code>--term-timeout</code> flag to <code>wandb agent</code> (<a href="https://github.com/nathancy-wandb"><code>@​nathancy-wandb</code></a> in <a href="">wandb/wandb#12246</a>)</li>
<li>Added <code>run.sync_dir</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12319</a>)</li>
</ul>
<h2>Changed</h2>
<ul>
<li>The new <code>wandb clean</code> command replaces <code>wandb sync --clean</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12238</a>)</li>
<li>Hardened argument handling in <code>wandb launch</code> for the local-process resource so that job-supplied values are always shell-quoted (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12220</a>)</li>
<li>The launch agent now restricts a job's git source URL to https/ssh remotes and pins git's protocol allowlist when fetching it and updating submodules (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12221</a>)</li>
<li>Response parsing is now faster for many <code>wandb.Api</code> operations, including artifact and registry queries (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12213</a>)</li>
<li><code>wandb.init()</code> now reports the error it was retrying (such as a network error) when it times out, instead of a generic timeout message. The <code>init_timeout</code> setting now also bounds the backend's retries during run initialization (<a href="https://github.com/skhanna-cw"><code>@​skhanna-cw</code></a> in <a href="">wandb/wandb#12216</a>)</li>
<li><code>wandb.Api().create_run_queue()</code>, <code>wandb.Api().create_custom_chart()</code>, and <code>wandb.Api().upsert_run_queue()</code> now raise <code>WandbApiFailedError</code> when the operation fails on the backend. (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12307</a>)</li>
<li>Paginated artifact and registry query methods (<code>Api.artifacts()</code>, <code>Api.artifact_collections()</code>, <code>Api.registries()</code>, <code>Registries.collections()</code>, <code>Registries.versions()</code>, <code>Collections.versions()</code>, <code>Registry.collections()</code>, <code>Registry.versions()</code>, <code>Project.collections()</code>) now perform client-side validation of pagination arguments before attempting to fetch any results (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12101</a>)</li>
<li>Ordered registry search now scopes per-registry collection and version queries to the current registry's internal id for more reliable pagination and filtering (<a href="https://github.com/ibindlish"><code>@​ibindlish</code></a> in <a href="">wandb/wandb#12188</a>)</li>
</ul>
<h2>Deprecated</h2>
<ul>
<li><code>wandb sync --sync-tensorboard</code> is deprecated and will be removed in a later release (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12419</a>)</li>
</ul>
<h2>Removed</h2>
<ul>
<li>Releases no longer include 32-bit Windows (<code>win32</code>) wheels; use 64-bit Python on Windows (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12267</a>)</li>
</ul>
<h2>Fixed</h2>
<ul>
<li>Registry search <code>registries(order=...).collections(order=...).versions()</code> now returns artifact versions in registry and/or collection order. (<a href="https://github.com/ibindlish"><code>@​ibindlish</code></a> in <a href="">wandb/wandb#12154</a>)</li>
<li>macOS x86_64 wheels now contain x86_64 builds of the <code>wandb-xpu</code> binary and the Rust parquet library, which previously shipped as arm64 and could not run or be loaded on Intel Macs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12267</a>)</li>
<li><code>wandb.login(verify=True)</code> and <code>wandb login --verify</code> now verify federated identity (identity token) credentials, which were previously not verified (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12294</a>)</li>
<li><code>wandb login</code> and <code>wandb verify</code> no longer update the system host settings when failing to login (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12332</a>)</li>
<li><code>wandb verify</code> now reports a failed check instead of crashing when an operation still fails after retries (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12360</a>)</li>
<li>Calling Sweeps agent with a custom <code>WANDB_DIR</code> will now respect it when dumping JSON output (<a href="https://github.com/kelu-wandb"><code>@​kelu-wandb</code></a> in <a href="">wandb/wandb#12344</a>)</li>
<li>Fixed <code>wandb.Api(overrides={&quot;base_url&quot;: ...})</code> failing to authenticate with federated identity (identity token) credentials when the specified server was not the default one, such as a dedicated cloud deployment, unless <code>WANDB_BASE_URL</code> was also set (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12340</a>)</li>
<li>When using federated identity, the identity token file is now re-read for each access token exchange instead of once at startup, so short-lived identity tokens re-minted to the same path keep working for runs that outlive them (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12341</a>)</li>
<li>When using federated identity, requests now fail immediately with the server's error message when the server rejects the identity token exchange, such as for an invalid or expired identity token. Previously, the rejected exchange was retried until requests timed out with a generic error (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12366</a>)</li>
<li><code>wandb login</code> validates api keys prior to saving to the <code>.netrc</code> file (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12347</a>)</li>
<li>The <code>global_step</code> metric created when syncing TensorBoard files is no longer prefixed, like <code>train/global_step</code>, so that it is easier to compare training and validation metrics (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12372</a>)</li>
<li>The TensorBoard integration now produces fewer W&amp;B steps by merging data for the same <code>global_step</code> into one W&amp;B step when possible (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12414</a>)</li>
<li><code>wandb sync</code> no longer hangs on a run that set its name, tags, or notes after starting (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12380</a>)</li>
<li><code>wandb login</code> no longer removes or corrupts credentials belonging to other machines in your <code>.netrc</code> file (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12386</a>)</li>
<li>Log messages captured from Python loggers no longer add blank lines to a run's logs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12387</a>)</li>
<li><code>del run.summary[key]</code> now removes metrics that were logged as nested values, which it previously ignored (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12389</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dc1ef8b</code></a> Bump version and update CHANGELOG for release 0.28.2</li>
<li><a href=""><code>e6acdac</code></a> chore: use opentelemetry proxy to record equivalent sentry events (<a href="">#12022</a>)</li>
<li><a href=""><code>385dc26</code></a> chore(registries): replace registry name filter with registry id (aka project...</li>
<li><a href=""><code>4af0cba</code></a> chore: update go deps (<a href="">#12448</a>)</li>
<li><a href=""><code>4db85e5</code></a> security: keep API key out of the process list when running docker commands (...</li>
<li><a href=""><code>83546c8</code></a> fix: allow deleting summary entries for metrics logged as nested values (<a href="">#12389</a>)</li>
<li><a href=""><code>3352bf5</code></a> fix: carefully remove streams from mux at teardown (<a href="">#12388</a>)</li>
<li><a href=""><code>7bfcfbf</code></a> fix: stop captured log lines from adding blank lines to the run log (<a href="">#12387</a>)</li>
<li><a href=""><code>e8dbc41</code></a> fix: keep other machines' credentials intact when saving login info to .netrc...</li>
<li><a href=""><code>2e79d68</code></a> security: stop writing cw cluster credentials to the debug log (<a href="">#12385</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/wandb/wandb/compare/v0.28.1...v0.28.2">compare view</a></li>
</ul>
</details>
<br />

Updates `rdkit` from 2026.3.4 to 2026.3.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rdkit/rdkit/releases">rdkit's releases</a>.</em></p>
<blockquote>
<h2>2026_03_5 (Q1 2026) Release</h2>
<h1>Release_2026.03.5</h1>
<p>(Changes relative to Release_2026.03.4)</p>
<h2>Acknowledgements</h2>
<p>(Note: I'm no longer attempting to manually curate names. If you would like to
see your contribution acknowledged with your name, please set your name in
GitHub)</p>
<p>Katharina Buchthal, Kerim Buyukakyuz, David Cosgrove, Peter Gedeck, Tad Hurst,
Egor Lyfar, Niels Maeder, Vedran Miletić, Yakov Pechersky, Emily Rhodes Jake
Robson-Tull, Ricardo Rodriguez, Pavel Tomanek, Paolo Tosco, Ivan Tubert-Brohman,
m_holmer</p>
<h2>New Features and Enhancements:</h2>
<ul>
<li>Add ROMol name accessors
(github pull <a href="">#9384</a> from i-tub)</li>
<li>Handle Data SGroups with no &quot;fieldname&quot;
(github pull <a href="">#9390</a> from tadhurst-cdd)</li>
<li>Validate coordinate map entries before distance geometry embedding
(github pull <a href="">#9420</a> from lyfar)</li>
</ul>
<h2>Documentation:</h2>
<ul>
<li>Add stub for rdGaussianShape docs.
(github pull <a href="">#9440</a> from DavidACosgrove)</li>
</ul>
<h2>Bug Fixes:</h2>
<ul>
<li>TautomerEnumerator.Canonicalize() raises pre-condition violation when <code>SetRemoveBondStereo(False)</code> on a molecule with atropisomer bond
(github issue <a href="">#9338</a> from pechersky)</li>
<li>CDXML reading doesn't retain Z/E bonds
(github issue <a href="">#9356</a> from pechersky)</li>
<li>RuntimeError while extracting a fragment from a molecule that cuts after an E/Z double bond
(github issue <a href="">#9368</a> from MalteHolmer)</li>
<li>Fix race in MinimalLib test_substruct_library JS test
(github pull <a href="">#9392</a> from emilyrrhodes)</li>
<li>Aromaticity perception in polycyclic conjugated system
(github issue <a href="">#9398</a> from nmaeder)</li>
<li>Inconsistent stereochemistry of ring-bonds in BoundsMatrixBuilder
(github issue <a href="">#9403</a> from kabu00002)</li>
<li>Inconsistent bounds for 1-4 distances of 6-membered rings
(github issue <a href="">#9404</a> from kabu00002)</li>
<li>RDKit 2026.03.4: testDistGeomHelpers fails
(github issue <a href="">#9406</a> from pavelToman)</li>
<li>Fix 64-bit fingerprint bit ID truncation in AdditionalOutput on 32-bit targets
(github pull <a href="">#9411</a> from gedeck)</li>
<li>Rascal FindMCES crash when time out reached and maxFragSeparation set
(github issue <a href="">#9418</a> from jrobsontull)</li>
<li>Out-of-bounds read in Mol2 bond parser due to incorrect bounds check
(github issue <a href="">#9421</a> from buyukakyuz)</li>
<li>Fix maeparser warning suppression with GCC</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/rdkit/rdkit/commits">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbd649d663b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.