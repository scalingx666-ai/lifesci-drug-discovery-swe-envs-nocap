# Issue

**Title:** Bump the python-minor-and-patch group with 2 updates

## Description

Bumps the python-minor-and-patch group with 2 updates: [hydra-core](https://github.com/facebookresearch/hydra) and [wandb](https://github.com/wandb/wandb).

Updates `hydra-core` from 1.3.5 to 1.3.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebookresearch/hydra/releases">hydra-core's releases</a>.</em></p>
<blockquote>
<h2>Hydra 1.3.6</h2>
<h2>What's Changed</h2>
<ul>
<li>Harden instantiate authorization against unsafe aliases and callable results. (<a href="">#3410</a>)</li>
<li>Apply Hydra's target blacklist to Python logging configuration. (<a href="">#3418</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/hydra-ecosystem/hydra/compare/v1.3.5...v1.3.6">https://github.com/hydra-ecosystem/hydra/compare/v1.3.5...v1.3.6</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/hydra-ecosystem/hydra/blob/v1.3.6/NEWS.md">hydra-core's changelog</a>.</em></p>
<blockquote>
<h1>1.3.6 (2026-08-29)</h1>
<h3>Bug Fixes</h3>
<ul>
<li>Harden instantiate authorization against unsafe aliases and callable results.
(<a href="">#3410</a>)</li>
<li>Apply Hydra's target blocklist to Python logging configuration.
(<a href="">#3418</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>27df755</code></a> Prepare Hydra 1.3.6 release</li>
<li><a href=""><code>ff3e4db</code></a> Harden logging target resolution on 1.3 (<a href="">#3420</a>)</li>
<li><a href=""><code>aa102ea</code></a> Harden deferred instantiate dispatch on 1.3</li>
<li><a href=""><code>2c82bbb</code></a> Backport instantiate target authorization hardening to 1.3 (<a href="">#3413</a>)</li>
<li><a href=""><code>06613ce</code></a> Bump Hydra to 1.3.6.dev0</li>
<li>See full diff in <a href="https://github.com/facebookresearch/hydra/compare/v1.3.5...v1.3.6">compare view</a></li>
</ul>
</details>
<br />

Updates `wandb` from 0.28.2 to 0.29.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/releases">wandb's releases</a>.</em></p>
<blockquote>
<h2>v0.29.0</h2>
<h2>What's Changed</h2>
<h3>Notable Changes</h3>
<ul>
<li>Removed the deprecated <code>start_method</code> setting that already had no effect.</li>
<li>The <code>.length</code> property on paginated objects (e.g. <code>Api.runs()</code>, <code>Api.sweeps()</code>, <code>run.files()</code>) has been removed. Use <code>len(...)</code> instead.
<code>wandb.Video()</code> now requires the <code>format</code> argument when initializing from a numpy array or raw bytes.</li>
<li>Removed the deprecated <code>summary=&quot;best&quot;</code> option and <code>goal</code> argument of <code>run.define_metric()</code>. Use <code>summary=&quot;min&quot;</code> or <code>summary=&quot;max&quot;</code> instead.</li>
<li>Removed the deprecated <code>quiet</code> argument of <code>run.finish()</code> and <code>wandb.finish()</code>. Use <code>wandb.Settings(quiet=...)</code> instead.</li>
<li>Removed the deprecated <code>run.project_name()</code>, <code>run.get_url()</code>, <code>run.get_project_url()</code>, and <code>run.get_sweep_url()</code> methods. Use the <code>run.project</code>, <code>run.url</code>, <code>run.project_url</code>, and <code>run.sweep_url</code> properties instead.</li>
<li><code>wandb.Image</code> no longer normalizes pixel values. Callers must now ensure their data already falls within the range [0, 255].</li>
<li>On macOS, <code>wandb</code> now requires macOS 13 (Ventura) or newer.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Added <code>run.console_logs()</code> to the public API for reading the console output that W&amp;B captured for a run — the whole log, or only the last N lines with <code>run.console_logs(last=N)</code>, for finished and still-running runs alike. Reading from the beginning requires W&amp;B Server 0.77 or newer (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12442</a>)</li>
<li>The automations API now supports team and organization scopes. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12197</a>, <a href="">wandb/wandb#12194</a>)</li>
<li>The automations API now supports creating and editing automations whose scope is a <code>Registry</code> object (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#10867</a>)</li>
<li>Press <code>g</code> in LEET to draw guides behind line charts: a dotted background or horizontal lines aligned with the axis ticks. The choice is saved and can also be set with <code>chart_guides</code> in <code>wandb leet config</code>. (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12463</a>)</li>
<li>Drag the separator lines between LEET's run overview sections to resize them with the mouse. The proportions are saved per view; press <code>0</code> to reset them along with the other pane sizes (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12525</a>)</li>
<li>Registry API version queries (<code>Api.registries().versions()</code>, <code>Api.registries().collections().versions()</code>, <code>Registry.versions()</code>, <code>Registry.collections().versions()</code>) now accept an optional <code>order</code> string as a keyword argument for organizations with advanced search. The API supports ordering versions by <code>created_at</code>, <code>artifact_size</code>, and <code>linked_at</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12489</a>)</li>
<li>Added <code>Artifact.linked_at</code> which returns when the version was linked to the relevant portfolio. This is valid only for linked versions, and for source artifacts returns <code>None</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12490</a>)</li>
<li><code>wandb.Artifact</code> now accepts a <code>digest_algorithm</code> argument (<code>&quot;MD5&quot;</code> or <code>&quot;XXH128&quot;</code>, defaulting to <code>&quot;MD5&quot;</code>). Passing <code>digest_algorithm=&quot;XXH128&quot;</code> opts the artifact into XXH128 hashing when possible. For artifacts created with <code>digest_algorithm=&quot;XXH128&quot;</code>, <code>artifact.verify()</code> will fail for SDK versions older than 0.29.0. (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12564</a>)</li>
<li><code>wandb leet inspect [PATH]</code> browses the raw records in a run's <code>.wandb</code> transaction log: a filterable list of every record next to a text view of the selected one, following live runs as they write. Press <code>i</code> in LEET's single-run view to open it for the current run, and pipe or redirect to print the records instead, e.g. <code>wandb leet inspect | less</code>. (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12547</a>, <a href="">wandb/wandb#12548</a>, <a href="">wandb/wandb#12549</a>)</li>
</ul>
<h3>Changed</h3>
<ul>
<li>The run overview sections in LEET (Environment, Config, Summary) now share the sidebar height proportionally and use all of the available space; previously they stopped growing at fixed sizes, leaving the bottom of tall terminals empty (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12523</a>)</li>
<li><code>Api.{create,update}_automation()</code> now raise <code>UnsupportedError</code> instead of <code>CommError</code> when the server doesn't support the given automation (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12194</a>)</li>
<li>The message format used to communicate between internal processes has slightly changed. If you use <code>wandb beta core</code>, restart the service after upgrading <code>wandb</code>, as some operations may fail if the SDK and service versions differ. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12374</a>)</li>
<li><code>wandb.sandbox</code> now allows GPU resource requests for sandboxes instead of rejecting <code>resources.gpu</code> client-side (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12455</a>)</li>
<li>Registry search methods (<code>Api.registries()</code>, <code>.collections()</code>, <code>.versions()</code>) now validate filter field names, rejecting unsupported field names. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12182</a>)</li>
<li><code>wandb.Video()</code> now requires the <code>format</code> argument when initializing from a numpy array or an io object. (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12579</a>)</li>
<li>The macOS wheels now require macOS 13 (Ventura) or newer; macOS 12 reached end of life in 2024 (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12599</a>)</li>
</ul>
<h3>Removed</h3>
<ul>
<li>Removed <code>wandb.tensorboard.log()</code> / <code>wandb.tensorflow.log()</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12423</a>)</li>
<li>The deprecated <code>start_method</code> setting that already had no effect (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12581</a>)</li>
<li>Removed the deprecated <code>.length</code> property from <code>wandb.apis.paginator.SizedPaginator</code>. Use <code>len(...)</code> instead (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12575</a>)</li>
<li>The deprecated <code>summary=&quot;best&quot;</code> option and <code>goal</code> argument of <code>run.define_metric()</code>; use <code>summary=&quot;min&quot;</code> or <code>summary=&quot;max&quot;</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12583</a>)</li>
<li>The deprecated <code>quiet</code> argument of <code>run.finish()</code> and <code>wandb.finish()</code>; use <code>wandb.Settings(quiet=...)</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12584</a>)</li>
<li>The deprecated <code>run.project_name()</code>, <code>run.get_url()</code>, <code>run.get_project_url()</code>, and <code>run.get_sweep_url()</code> methods; use the <code>run.project</code>, <code>run.url</code>, <code>run.project_url</code>, and <code>run.sweep_url</code> properties instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12585</a>)</li>
<li>Removed deprecated <code>normalize</code> argument from <code>wandb.Image</code>; callers should ensure pixel values for NumPy arrays and PyTorch tensors already fall in the range [0, 255] (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12574</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li><code>Artifact.new_file</code> now works for artifacts uploaded with <code>wandb sync</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12437</a>)</li>
<li>At certain pane widths, such as while dragging a sidebar edge, LEET drew metric charts wider than the space available, pushing the right sidebar off screen (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12513</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/blob/main/CHANGELOG.md">wandb's changelog</a>.</em></p>
<blockquote>
<h2>[0.29.0] - 2026-08-26</h2>
<h3>Notable Changes</h3>
<ul>
<li>Removed the deprecated <code>start_method</code> setting that already had no effect.</li>
<li>The <code>.length</code> property on paginated objects (e.g. <code>Api.runs()</code>, <code>Api.sweeps()</code>, <code>run.files()</code>) has been removed. Use <code>len(...)</code> instead.
<code>wandb.Video()</code> now requires the <code>format</code> argument when initializing from a numpy array or raw bytes.</li>
<li>Removed the deprecated <code>summary=&quot;best&quot;</code> option and <code>goal</code> argument of <code>run.define_metric()</code>. Use <code>summary=&quot;min&quot;</code> or <code>summary=&quot;max&quot;</code> instead.</li>
<li>Removed the deprecated <code>quiet</code> argument of <code>run.finish()</code> and <code>wandb.finish()</code>. Use <code>wandb.Settings(quiet=...)</code> instead.</li>
<li>Removed the deprecated <code>run.project_name()</code>, <code>run.get_url()</code>, <code>run.get_project_url()</code>, and <code>run.get_sweep_url()</code> methods. Use the <code>run.project</code>, <code>run.url</code>, <code>run.project_url</code>, and <code>run.sweep_url</code> properties instead.</li>
<li><code>wandb.Image</code> no longer normalizes pixel values. Callers must now ensure their data already falls within the range [0, 255].</li>
<li>On macOS, <code>wandb</code> now requires macOS 13 (Ventura) or newer.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Added <code>run.console_logs()</code> to the public API for reading the console output that W&amp;B captured for a run — the whole log, or only the last N lines with <code>run.console_logs(last=N)</code>, for finished and still-running runs alike. Reading from the beginning requires W&amp;B Server 0.77 or newer (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12442</a>)</li>
<li>The automations API now supports team and organization scopes. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12197</a>, <a href="">wandb/wandb#12194</a>)</li>
<li>The automations API now supports creating and editing automations whose scope is a <code>Registry</code> object (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#10867</a>)</li>
<li>Press <code>g</code> in LEET to draw guides behind line charts: a dotted background or horizontal lines aligned with the axis ticks. The choice is saved and can also be set with <code>chart_guides</code> in <code>wandb leet config</code>. (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12463</a>)</li>
<li>Drag the separator lines between LEET's run overview sections to resize them with the mouse. The proportions are saved per view; press <code>0</code> to reset them along with the other pane sizes (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12525</a>)</li>
<li>Registry API version queries (<code>Api.registries().versions()</code>, <code>Api.registries().collections().versions()</code>, <code>Registry.versions()</code>, <code>Registry.collections().versions()</code>) now accept an optional <code>order</code> string as a keyword argument for organizations with advanced search. The API supports ordering versions by <code>created_at</code>, <code>artifact_size</code>, and <code>linked_at</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12489</a>)</li>
<li>Added <code>Artifact.linked_at</code> which returns when the version was linked to the relevant portfolio. This is valid only for linked versions, and for source artifacts returns <code>None</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12490</a>)</li>
<li><code>wandb.Artifact</code> now accepts a <code>digest_algorithm</code> argument (<code>&quot;MD5&quot;</code> or <code>&quot;XXH128&quot;</code>, defaulting to <code>&quot;MD5&quot;</code>). Passing <code>digest_algorithm=&quot;XXH128&quot;</code> opts the artifact into XXH128 hashing when possible. For artifacts created with <code>digest_algorithm=&quot;XXH128&quot;</code>, <code>artifact.verify()</code> will fail for SDK versions older than 0.29.0. (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12564</a>)</li>
<li><code>wandb leet inspect [PATH]</code> browses the raw records in a run's <code>.wandb</code> transaction log: a filterable list of every record next to a text view of the selected one, following live runs as they write. Press <code>i</code> in LEET's single-run view to open it for the current run, and pipe or redirect to print the records instead, e.g. <code>wandb leet inspect | less</code>. (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12547</a>, <a href="">wandb/wandb#12548</a>, <a href="">wandb/wandb#12549</a>)</li>
</ul>
<h3>Changed</h3>
<ul>
<li>The run overview sections in LEET (Environment, Config, Summary) now share the sidebar height proportionally and use all of the available space; previously they stopped growing at fixed sizes, leaving the bottom of tall terminals empty (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12523</a>)</li>
<li><code>Api.{create,update}_automation()</code> now raise <code>UnsupportedError</code> instead of <code>CommError</code> when the server doesn't support the given automation (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12194</a>)</li>
<li>The message format used to communicate between internal processes has slightly changed. If you use <code>wandb beta core</code>, restart the service after upgrading <code>wandb</code>, as some operations may fail if the SDK and service versions differ. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12374</a>)</li>
<li><code>wandb.sandbox</code> now allows GPU resource requests for sandboxes instead of rejecting <code>resources.gpu</code> client-side (<a href="https://github.com/nicholaspun-wandb"><code>@​nicholaspun-wandb</code></a> in <a href="">wandb/wandb#12455</a>)</li>
<li>Registry search methods (<code>Api.registries()</code>, <code>.collections()</code>, <code>.versions()</code>) now validate filter field names, rejecting unsupported field names. (<a href="https://github.com/tonyyli-wandb"><code>@​tonyyli-wandb</code></a> in <a href="">wandb/wandb#12182</a>)</li>
<li><code>wandb.Video()</code> now requires the <code>format</code> argument when initializing from a numpy array or an io object. (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12579</a>)</li>
<li>The macOS wheels now require macOS 13 (Ventura) or newer; macOS 12 reached end of life in 2024 (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12599</a>)</li>
</ul>
<h3>Removed</h3>
<ul>
<li>Removed <code>wandb.tensorboard.log()</code> / <code>wandb.tensorflow.log()</code> (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12423</a>)</li>
<li>The deprecated <code>start_method</code> setting that already had no effect (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12581</a>)</li>
<li>Removed the deprecated <code>.length</code> property from <code>wandb.apis.paginator.SizedPaginator</code>. Use <code>len(...)</code> instead (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12575</a>)</li>
<li>The deprecated <code>summary=&quot;best&quot;</code> option and <code>goal</code> argument of <code>run.define_metric()</code>; use <code>summary=&quot;min&quot;</code> or <code>summary=&quot;max&quot;</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12583</a>)</li>
<li>The deprecated <code>quiet</code> argument of <code>run.finish()</code> and <code>wandb.finish()</code>; use <code>wandb.Settings(quiet=...)</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12584</a>)</li>
<li>The deprecated <code>run.project_name()</code>, <code>run.get_url()</code>, <code>run.get_project_url()</code>, and <code>run.get_sweep_url()</code> methods; use the <code>run.project</code>, <code>run.url</code>, <code>run.project_url</code>, and <code>run.sweep_url</code> properties instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12585</a>)</li>
<li>Removed deprecated <code>normalize</code> argument from <code>wandb.Image</code>; callers should ensure pixel values for NumPy arrays and PyTorch tensors already fall in the range [0, 255] (<a href="https://github.com/jacobromero"><code>@​jacobromero</code></a> in <a href="">wandb/wandb#12574</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li><code>Artifact.new_file</code> now works for artifacts uploaded with <code>wandb sync</code> (<a href="https://github.com/amusipatla-wandb"><code>@​amusipatla-wandb</code></a> in <a href="">wandb/wandb#12437</a>)</li>
<li>At certain pane widths, such as while dragging a sidebar edge, LEET drew metric charts wider than the space available, pushing the right sidebar off screen (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12513</a>)</li>
<li><code>wandb leet config</code> now works on short terminal windows: the field list scrolls with the selection and Space toggles boolean settings (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12529</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7872fd9</code></a> Bump version and update CHANGELOG for release 0.29.0</li>
<li><a href=""><code>7f3dbc0</code></a> chore: raise macOS wheel deployment target to 13 (<a href="">#12599</a>)</li>
<li><a href=""><code>8b43e26</code></a> chore: update go deps (<a href="">#12598</a>)</li>
<li><a href=""><code>451f45d</code></a> fix(leet): make ansi media view letterbox transparent (<a href="">#12569</a>)</li>
<li><a href=""><code>85ac37f</code></a> feat(leet): open the record inspector from the single-run view (<a href="">#12549</a>)</li>
<li><a href=""><code>7e0c1b0</code></a> feat(leet): add wandb leet inspect, remove tools/inspect_tool.py (<a href="">#12548</a>)</li>
<li><a href=""><code>fb2df2c</code></a> feat(leet): add a record inspector for .wandb transaction logs (<a href="">#12547</a>)</li>
<li><a href=""><code>41edfc2</code></a> chore: remove deprecated image normalization parameter (<a href="">#12574</a>)</li>
<li><a href=""><code>367110d</code></a> chore: remove deprecated <code>quiet</code> argument from <code>run.finish()</code> (<a href="">#12584</a>)</li>
<li><a href=""><code>32ef245</code></a> chore: remove deprecated <code>define_metric(summary='best', goal=...)</code> (<a href="">#12583</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/wandb/wandb/compare/v0.28.2...v0.29.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58daa00e78fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.