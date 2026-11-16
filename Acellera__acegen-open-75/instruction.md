# Issue

**Title:** Bump the python-minor-and-patch group across 1 directory with 6 updates

## Description

Bumps the python-minor-and-patch group with 6 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [flake8](https://github.com/pycqa/flake8) | `7.3.0` | `7.4.1` |
| [pytest](https://github.com/pytest-dev/pytest) | `9.1.1` | `9.2.0` |
| [hydra-core](https://github.com/hydra-ecosystem/hydra) | `1.3.6` | `1.3.8` |
| [tqdm](https://github.com/tqdm/tqdm) | `4.70.0` | `4.70.1` |
| [wandb](https://github.com/wandb/wandb) | `0.29.0` | `0.31.0` |
| [rdkit](https://github.com/rdkit/rdkit) | `2026.3.5` | `2026.9.1` |

Updates `flake8` from 7.3.0 to 7.4.1
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7eccf20</code></a> Release 7.4.1</li>
<li><a href=""><code>fe7311d</code></a> Merge pull request <a href="">#2057</a> from PyCQA/fix-pyflakes-4</li>
<li><a href=""><code>819d5e6</code></a> fix pyflakes 4.x --builtins integration</li>
<li><a href=""><code>3140509</code></a> Release 7.4.0</li>
<li><a href=""><code>e12e231</code></a> Merge pull request <a href="">#2055</a> from PyCQA/add-315-ci</li>
<li><a href=""><code>f022536</code></a> add python 3.15 to CI</li>
<li><a href=""><code>07eb8ae</code></a> Merge pull request <a href="">#2054</a> from PyCQA/latest-pyflakes</li>
<li><a href=""><code>a9e6dc2</code></a> update to latest pyflakes</li>
<li><a href=""><code>2436eab</code></a> Merge pull request <a href="">#2053</a> from PyCQA/latest-pycodestyle</li>
<li><a href=""><code>b44ddd4</code></a> update to latest pycodestyle</li>
<li>Additional commits viewable in <a href="https://github.com/pycqa/flake8/compare/7.3.0...7.4.1">compare view</a></li>
</ul>
</details>
<br />

Updates `pytest` from 9.1.1 to 9.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>9.2.0</h2>
<h1>pytest 9.2.0 (2026-10-27)</h1>
<h2>Removals and backward incompatible breaking changes</h2>
<ul>
<li>
<p><a href="">#14716</a>: <code>-c</code> now raises a usage error for a path that does not exist, is a directory, or is in a format pytest has no loader for. Such paths were previously either ignored or reported as an unhandled <code>FileNotFoundError</code>.</p>
</li>
<li>
<p><a href="">#8593</a>: The <code>indirect</code>, <code>ids</code> and <code>scope</code> arguments of <code>Metafunc.parametrize() &lt;pytest.Metafunc.parametrize&gt;</code> -- and therefore of <code>@pytest.mark.parametrize &lt;pytest.mark.parametrize ref&gt;</code> -- are now keyword-only.</p>
<p>Passing them positionally was a common source of confusing errors, e.g. <code>parametrize(&quot;arg1&quot;, &quot;arg2&quot;, [(1, 2)])</code> made the argvalues land in <code>indirect</code> and failed with <code>indirect fixture '(1, 2)' doesn't exist</code>; such mistakes now fail with an understandable <code>TypeError</code>. The type annotations have always declared these arguments as keyword-only.</p>
</li>
<li>
<p><a href="">#993</a>: Plugin import failures at startup are now reported and classified instead of escaping as a raw traceback with the accidental exit code <code>1</code>:</p>
<ul>
<li>a plugin that cannot be found -- via <code>-p</code>, <code>pytest_plugins</code> or <code>PYTEST_PLUGINS</code> -- exits with <code>pytest.ExitCode</code> <code>USAGE_ERROR</code> (<code>4</code>), like a <code>conftest.py</code> that fails to import;</li>
<li>a plugin that is found but raises while importing -- including a broken <code>pytest11</code> entry point or a missing plugin dependency -- exits with <code>pytest.ExitCode</code> <code>INTERNAL_ERROR</code> (<code>3</code>), with the traceback preserved.</li>
</ul>
<p><code>pytest.main</code> now returns these codes instead of raising <code>ImportError</code>. Also fixed an <code>IndexError</code> from pytest's own internals when the plugin raised an exception with no arguments.</p>
</li>
</ul>
<h2>Deprecations (removal in next major release)</h2>
<ul>
<li>
<p><a href="">#14742</a>: The private <code>_pytest.python.CallSpec2</code> name has been renamed to <code>CallSpec</code>.
The old <code>CallSpec2</code> alias remains available for now and will be removed in pytest 10 or 11.</p>
</li>
<li>
<p><a href="">#14755</a>: Schedule <em>yield_fixture</em> decorator for removal in pytest 10 or 11.</p>
</li>
<li>
<p><a href="">#14774</a>: Similarly to the deprecation of class-scoped fixtures defined as instance methods in pytest 9.1,
<em>all</em> higher-scoped fixtures (<code>module</code>, <code>package</code>, and <code>session</code>) defined
as instance methods are now deprecated.</p>
<p>They suffer from the same issue the original deprecation only fixed for
class-scoped fixtures, see <code>10819</code> and <code>14011</code>.</p>
</li>
<li>
<p><a href="">#14808</a>: Passing a non-string value to a <code>string</code>-typed ini option now emits a <code>pytest.PytestRemovedIn10Warning</code>. This affects <code>[tool.pytest.ini_options]</code> in <code>pyproject.toml</code>. In pytest 10 this will raise a <code>TypeError</code>, matching the behavior of the corresponding TOML config path.</p>
</li>
<li>
<p><a href="">#7323</a>: Passing <code>bytes</code> to <code>TerminalReporter.write_line()</code> is now deprecated, pass a <code>str</code> instead.</p>
</li>
</ul>
<h2>New features</h2>
<ul>
<li><a href="">#14743</a>: <!-- raw HTML omitted -->Full diff:<!-- raw HTML omitted --> now contains a legend explaining the <!-- raw HTML omitted -->+<!-- raw HTML omitted --> &amp; <!-- raw HTML omitted -->-<!-- raw HTML omitted --> symbols in diff output.</li>
<li><a href="">#2781</a>: When <code>strict_markers</code> is enabled, marker names used in <code>-m</code> expressions are now validated against registered markers.</li>
<li><a href="">#6881</a>: Added the <code>parametrize_long_str_id_strategy</code> configuration option to control how long <code>str</code>/<code>bytes</code> parameter values are handled in auto-generated test IDs. Explicit IDs set via <code>ids=[...]</code> or <code>pytest.param(..., id=...)</code> are not affected. Available strategies: <code>short</code> (default, values over 100 chars fall back to <code>argname+index</code>), <code>sha256</code> (SHA-256 hex digest), <code>legacy</code> (keep full value), and <code>disallow</code> (error requesting explicit IDs).</li>
</ul>
<h2>Improvements in existing functionality</h2>
<ul>
<li><a href="">#10745</a>: A <code>RecursionError</code> whose recursion origin cannot be located now shows only the
first and last 10 stack frames, matching what pytest already did when locating
the origin failed outright. Previously the full traceback -- often around a
thousand near-identical frames -- was rendered, which was both slow and
unreadable. Pass <code>--full-trace</code> to see every frame.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ae1d0ff</code></a> Prepare release version 9.2.0</li>
<li><a href=""><code>143ce31</code></a> pre-commit: exclude codespell on generated release announcements</li>
<li><a href=""><code>532dc5f</code></a> tox: add attrs dependency to regen, needed in reportingdemo.rst</li>
<li><a href=""><code>a7b2446</code></a> Merge pull request <a href="">#15245</a> from pytest-dev/claude/project-thread-9jcf91</li>
<li><a href=""><code>679d09c</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#15266</a>)</li>
<li><a href=""><code>41d12cd</code></a> docs: clarify typing for yield fixtures</li>
<li><a href=""><code>b9022ba</code></a> Merge pull request <a href="">#15182</a> from 1871698/docs/improve-getting-started-description</li>
<li><a href=""><code>16f87a7</code></a> docs: improve getting-started.rst test execution description</li>
<li><a href=""><code>082ed70</code></a> Merge pull request <a href="">#15255</a> from pytest-dev/claude/project-thread-eoi3d6</li>
<li><a href=""><code>ae37a01</code></a> Merge pull request <a href="">#15227</a> from pytest-dev/claude/project-thread-4etye4</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/9.1.1...9.2.0">compare view</a></li>
</ul>
</details>
<br />

Updates `hydra-core` from 1.3.6 to 1.3.8
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/hydra-ecosystem/hydra/releases">hydra-core's releases</a>.</em></p>
<blockquote>
<h2>Hydra 1.3.8</h2>
<h3>Bug fixes</h3>
<ul>
<li>Prevent arbitrary code execution through unsafe PyYAML loaders in
<code>hydra.utils.instantiate()</code>. Safe YAML loading and dumping remain supported.</li>
</ul>
<h2>Hydra 1.3.7</h2>
<h2>What's Changed</h2>
<ul>
<li>Strengthen defense-in-depth checks for configured targets, Python runtime state, process-environment mutation, and logging formatters. These checks are not a complete security boundary. (<a href="">#3442</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/hydra-ecosystem/hydra/compare/v1.3.6...v1.3.7">https://github.com/hydra-ecosystem/hydra/compare/v1.3.6...v1.3.7</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/hydra-ecosystem/hydra/blob/v1.3.8/NEWS.md">hydra-core's changelog</a>.</em></p>
<blockquote>
<h1>1.3.8 (2026-10-25)</h1>
<h3>Bug Fixes</h3>
<ul>
<li>Prevent arbitrary code execution through unsafe PyYAML loaders in
<code>hydra.utils.instantiate()</code>. Safe YAML loading and dumping remain supported.
1.3.7 (2026-09-14)
==================</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Strengthen defense-in-depth checks for configured targets, Python runtime state,
process-environment mutation, and logging formatters. These checks are not a
complete security boundary. (<a href="">#3442</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>004658a</code></a> Clarify the Hydra 1.3.8 security release note</li>
<li><a href=""><code>2f20add</code></a> Prepare Hydra 1.3.8 security release</li>
<li><a href=""><code>de55543</code></a> Merge commit from fork</li>
<li><a href=""><code>39f3b31</code></a> Prepare Ray launcher 1.2.2 release</li>
<li><a href=""><code>ed11e57</code></a> Backport the Ray version resolver fix to Hydra 1.3 (<a href="">#3567</a>)</li>
<li><a href=""><code>d620c0b</code></a> Update Hydra 1.3 package metadata after repository transfer</li>
<li><a href=""><code>35cd89d</code></a> Support publishing 1.3 plugins</li>
<li><a href=""><code>8429daa</code></a> Prepare hydra-optuna-sweeper 1.3.0 release</li>
<li><a href=""><code>81715a5</code></a> Prepare hydra-core 1.3.7 release</li>
<li><a href=""><code>4720dfc</code></a> Merge commit from fork</li>
<li>See full diff in <a href="https://github.com/hydra-ecosystem/hydra/compare/v1.3.6...v1.3.8">compare view</a></li>
</ul>
</details>
<br />

Updates `tqdm` from 4.70.0 to 4.70.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/tqdm/tqdm/releases">tqdm's releases</a>.</em></p>
<blockquote>
<h2>tqdm v4.70.1 stable</h2>
<ul>
<li><code>contrib.concurrent</code>: fix no-len iterables (<a href="">#1830</a> &lt;- <a href="">#1828</a>)</li>
<li>tests: major overhaul (<a href="">#1819</a>)</li>
<li>update AI policy in PR template</li>
<li>misc lint &amp; tidy</li>
<li>CI: bump workflow actions &amp; pre-commit hooks</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9cf5a12</code></a> Merge pull request <a href="">#1830</a> from eaubin/master</li>
<li><a href=""><code>24b9e1e</code></a> misc tidy</li>
<li><a href=""><code>2a9e4e8</code></a> contrib.concurrent: fix no-len iterables</li>
<li><a href=""><code>8d6ff8d</code></a> Merge pull request <a href="">#1819</a> from tqdm/devel</li>
<li><a href=""><code>bed3796</code></a> tests: major overhaul</li>
<li><a href=""><code>4d3d319</code></a> AI policy</li>
<li><a href=""><code>5dcb022</code></a> minor syntax update</li>
<li><a href=""><code>309effe</code></a> tests: pre-commit coverage</li>
<li><a href=""><code>604193a</code></a> tests: slight tidy</li>
<li><a href=""><code>17f1cac</code></a> CI: bump workflow actions</li>
<li>See full diff in <a href="https://github.com/tqdm/tqdm/compare/v4.70.0...v4.70.1">compare view</a></li>
</ul>
</details>
<br />

Updates `wandb` from 0.29.0 to 0.31.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/releases">wandb's releases</a>.</em></p>
<blockquote>
<h2>v0.31.0</h2>
<h2>What's Changed</h2>
<h3>Notable Changes</h3>
<ul>
<li>The default API endpoint is now CoreWeave Forge at <code>https://api.forge.coreweave.com</code>, and run links point to <code>https://forge.coreweave.com/wandb</code>. Existing API keys stored for <code>api.wandb.ai</code> keep working without logging in again.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Python 3.15 is now supported (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13167</a>)</li>
<li><code>wandb.init(resume=&quot;must&quot;)</code> now works for offline runs. <code>wandb sync</code> fails if there is no run to resume (<a href="https://github.com/geoffhardy"><code>@​geoffhardy</code></a> in <a href="">wandb/wandb#12666</a>)</li>
<li><code>wandb sweep-scheduler [entity/project/]sweep_id</code> runs a sweep's search locally with Optuna or Ax as the optimizer, configured in a <code>scheduler</code> block of the sweep config. <code>wandb sweep</code> prints the command for sweeps that set one (<a href="https://github.com/kmikowicz-wandb"><code>@​kmikowicz-wandb</code></a> in <a href="">wandb/wandb#12900</a>)</li>
<li><code>wandb agent --max-consecutive-failed-runs N</code> shuts the agent down once N runs in a row have failed (<a href="https://github.com/nathancy-wandb"><code>@​nathancy-wandb</code></a> in <a href="">wandb/wandb#12821</a>)</li>
<li><code>wandb sync</code> warns when a run was logged with a newer version of <code>wandb</code> than the one syncing it (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12808</a>)</li>
<li>W&amp;B LEET TUI:
<ul>
<li><code>wandb leet inspect --summary</code> prints a run's state, latest metric values, config and last console lines from its local <code>.wandb</code> file, a quick way for a script or a coding agent to check on a run. <code>--json</code> prints the records, or the summary, as JSON, and <code>--follow</code> keeps printing records as a running run writes them (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12951</a>, <a href="">wandb/wandb#12952</a>)</li>
<li><code>l</code> links the console logs to the charts in the single-run view: with the logs pane focused, the charts show a crosshair at the time the selected line was logged, and inspecting a chart with the mouse selects the console line logged nearest to that point. <code>l</code> again unlinks (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12737</a>)</li>
<li><code>ctrl+a</code> selects every run matching the runs filter, and <code>x</code> deselects all runs except the pinned one (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12904</a>)</li>
<li>Selected and pinned runs are remembered per wandb directory and selected again the next time you open it. The newest run is selected as well if it started since the last session (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12887</a>)</li>
<li>The <code>CPU Core (%)</code> chart opens as a heatmap with one row per core; <code>y</code> switches it back to lines (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13014</a>)</li>
</ul>
</li>
<li><code>wandb leet symon</code>, the live system monitor:
<ul>
<li>Shows the utilization of every CPU core, the CPU temperature and swap usage on Linux, and the hostname, uptime and load average in its header (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13012</a>, <a href="">wandb/wandb#13015</a>)</li>
<li>Charts network and disk throughput in bytes per second instead of totals, and opens with the CPU, memory, network and disk charts ahead of the rest (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13013</a>, <a href="">wandb/wandb#13014</a>)</li>
<li>Has a sidebar with the machine's chip, cores, memory and GPUs, live meters for CPU, memory, swap, disk and GPU use, and the processes using the most CPU. <code>t</code> sorts the processes by memory, <code>f</code> filters them by name or PID, <code>Tab</code> moves between the process list and the charts, and <code>[</code> hides the sidebar. The sidebar can be resized by dragging its border, and <code>0</code> restores the default width (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13016</a>, <a href="">wandb/wandb#13017</a>, <a href="">wandb/wandb#13018</a>, <a href="">wandb/wandb#13021</a>)</li>
</ul>
</li>
<li>New system metrics:
<ul>
<li>PCIe throughput (<code>gpu.N.pcieTxBytes</code>, <code>gpu.N.pcieRxBytes</code>) for NVIDIA GPUs older than Hopper (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12989</a>)</li>
<li>Each GPU's cumulative energy consumption in joules as <code>gpu.N.energyJoules</code>, for NVIDIA and AMD GPUs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12991</a>)</li>
<li><code>proc.cpu.throttledPercent</code>, the percentage of CPU scheduler periods in which the container's CPU limit throttled the run (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13001</a>)</li>
<li><code>proc.memory.oomKills</code>, how many processes in the run's container the out-of-memory killer has killed since the run started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13002</a>)</li>
<li><code>network.tcpRetransmits</code>, the number of TCP segments retransmitted since the run started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13003</a>)</li>
<li>The CPU and memory used by W&amp;B's own background processes, as <code>wandb.cpu</code> and <code>wandb.memory.rssMB</code>. They are off by default; turn them on with the <code>x_stats_self_usage</code> setting (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13004</a>, <a href="">wandb/wandb#13038</a>)</li>
</ul>
</li>
<li>Run metadata now records the CPU model and, for each NVIDIA GPU, its PCI bus ID and, on Linux, its NUMA node (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13005</a>, <a href="">wandb/wandb#13157</a>)</li>
</ul>
<h3>Changed</h3>
<ul>
<li>The default W&amp;B server is now CoreWeave Forge at <code>https://api.forge.coreweave.com</code>. Run, project, sweep and login links point to <code>https://forge.coreweave.com/wandb</code>, also when <code>base_url</code> is set to <code>https://api.wandb.ai</code> or <code>https://forge.coreweave.com/api/wandb</code>. Existing API keys stored for <code>api.wandb.ai</code> keep working without logging in again (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13077</a>)</li>
<li>The helper process that collects system metrics is now <code>wandb-symon</code> instead of <code>wandb-xpu</code> (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13165</a>)</li>
<li><code>import wandb</code> and the <code>wandb</code> CLI start about twice as fast (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13144</a>, <a href="">wandb/wandb#13145</a>, <a href="">wandb/wandb#13146</a>, <a href="">wandb/wandb#13147</a>, <a href="">wandb/wandb#13148</a>)</li>
<li>The <code>wandb</code> package is smaller: <code>wandb-core</code> shrank by about a third, from 52 MB to 35 MB on Linux x86_64, and the parquet reader and the system metrics helper by more than half (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12921</a>, <a href="">wandb/wandb#12922</a>, <a href="">wandb/wandb#12923</a>, <a href="">wandb/wandb#12924</a>, <a href="">wandb/wandb#12937</a>, <a href="">wandb/wandb#12939</a>)</li>
<li>Runs write their data to the local <code>.wandb</code> file at least every 15 seconds, so <code>wandb leet</code> shows recent data sooner for runs that log infrequently (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12742</a>)</li>
<li>The <code>cpu</code> system metric reports the monitored process's CPU utilization over the sampling interval instead of its average since the process started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13101</a>)</li>
<li>NVIDIA GPM system metrics such as <code>gpu.N.smActive</code> and <code>gpu.N.dramActive</code> are now averaged over the whole interval between samples instead of a 200 ms window (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12987</a>)</li>
<li>AMD GPU system metrics are read through the ROCm SMI library (<code>librocm_smi64.so</code>) instead of running the <code>rocm-smi</code> tool on every sample. Readings a GPU does not provide are left out instead of reported as 0 (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12990</a>)</li>
<li>OpenMetrics and DCGM exporter endpoints are scraped once per sampling interval for all runs on the machine instead of once per run, and all runs use the same <code>openmetrics.&lt;endpoint&gt;.&lt;metric&gt;.&lt;index&gt;</code> index for the same metric labels (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13103</a>)</li>
</ul>
<h3>Removed</h3>
<ul>
<li>Removed the undocumented <code>wandb.set_trace()</code>. Use Python's built-in <code>breakpoint()</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12985</a>)</li>
</ul>
<h3>Fixed</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/wandb/wandb/blob/main/CHANGELOG.md">wandb's changelog</a>.</em></p>
<blockquote>
<h2>[0.31.0] - 2026-10-16</h2>
<h3>Notable Changes</h3>
<ul>
<li>The default W&amp;B server is now CoreWeave Forge at <code>https://api.forge.coreweave.com</code>, and run links point to <code>https://forge.coreweave.com/wandb</code>. Existing API keys stored for <code>api.wandb.ai</code> keep working without logging in again.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Python 3.15 is now supported (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13167</a>)</li>
<li><code>wandb.init(resume=&quot;must&quot;)</code> now works for offline runs. <code>wandb sync</code> fails if there is no run to resume (<a href="https://github.com/geoffhardy"><code>@​geoffhardy</code></a> in <a href="">wandb/wandb#12666</a>)</li>
<li><code>wandb sweep-scheduler [entity/project/]sweep_id</code> runs a sweep's search locally with Optuna or Ax as the optimizer, configured in a <code>scheduler</code> block of the sweep config. <code>wandb sweep</code> prints the command for sweeps that set one (<a href="https://github.com/kmikowicz-wandb"><code>@​kmikowicz-wandb</code></a> in <a href="">wandb/wandb#12900</a>)</li>
<li><code>wandb agent --max-consecutive-failed-runs N</code> shuts the agent down once N runs in a row have failed (<a href="https://github.com/nathancy-wandb"><code>@​nathancy-wandb</code></a> in <a href="">wandb/wandb#12821</a>)</li>
<li><code>wandb sync</code> warns when a run was logged with a newer version of <code>wandb</code> than the one syncing it (<a href="https://github.com/timoffex"><code>@​timoffex</code></a> in <a href="">wandb/wandb#12808</a>)</li>
<li>W&amp;B LEET TUI:
<ul>
<li><code>wandb leet inspect --summary</code> prints a run's state, latest metric values, config and last console lines from its local <code>.wandb</code> file, a quick way for a script or a coding agent to check on a run. <code>--json</code> prints the records, or the summary, as JSON, and <code>--follow</code> keeps printing records as a running run writes them (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12951</a>, <a href="">wandb/wandb#12952</a>)</li>
<li><code>l</code> links the console logs to the charts in the single-run view: with the logs pane focused, the charts show a crosshair at the time the selected line was logged, and inspecting a chart with the mouse selects the console line logged nearest to that point. <code>l</code> again unlinks (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12737</a>)</li>
<li><code>ctrl+a</code> selects every run matching the runs filter, and <code>x</code> deselects all runs except the pinned one (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12904</a>)</li>
<li>Selected and pinned runs are remembered per wandb directory and selected again the next time you open it. The newest run is selected as well if it started since the last session (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12887</a>)</li>
<li>The <code>CPU Core (%)</code> chart opens as a heatmap with one row per core; <code>y</code> switches it back to lines (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13014</a>)</li>
</ul>
</li>
<li><code>wandb leet symon</code>, the live system monitor:
<ul>
<li>Shows the utilization of every CPU core, the CPU temperature and swap usage on Linux, and the hostname, uptime and load average in its header (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13012</a>, <a href="">wandb/wandb#13015</a>)</li>
<li>Charts network and disk throughput in bytes per second instead of totals, and opens with the CPU, memory, network and disk charts ahead of the rest (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13013</a>, <a href="">wandb/wandb#13014</a>)</li>
<li>Has a sidebar with the machine's chip, cores, memory and GPUs, live meters for CPU, memory, swap, disk and GPU use, and the processes using the most CPU. <code>t</code> sorts the processes by memory, <code>f</code> filters them by name or PID, <code>Tab</code> moves between the process list and the charts, and <code>[</code> hides the sidebar. The sidebar can be resized by dragging its border, and <code>0</code> restores the default width (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13016</a>, <a href="">wandb/wandb#13017</a>, <a href="">wandb/wandb#13018</a>, <a href="">wandb/wandb#13021</a>)</li>
</ul>
</li>
<li>New system metrics:
<ul>
<li>PCIe throughput (<code>gpu.N.pcieTxBytes</code>, <code>gpu.N.pcieRxBytes</code>) for NVIDIA GPUs older than Hopper (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12989</a>)</li>
<li>Each GPU's cumulative energy consumption in joules as <code>gpu.N.energyJoules</code>, for NVIDIA and AMD GPUs (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12991</a>)</li>
<li><code>proc.cpu.throttledPercent</code>, the percentage of CPU scheduler periods in which the container's CPU limit throttled the run (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13001</a>)</li>
<li><code>proc.memory.oomKills</code>, how many processes in the run's container the out-of-memory killer has killed since the run started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13002</a>)</li>
<li><code>network.tcpRetransmits</code>, the number of TCP segments retransmitted since the run started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13003</a>)</li>
<li>The CPU and memory used by W&amp;B's own background processes, as <code>wandb.cpu</code> and <code>wandb.memory.rssMB</code>. They are off by default; turn them on with the <code>x_stats_self_usage</code> setting (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13004</a>, <a href="">wandb/wandb#13038</a>)</li>
</ul>
</li>
<li>Run metadata now records the CPU model and, for each NVIDIA GPU, its PCI bus ID and, on Linux, its NUMA node (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13005</a>, <a href="">wandb/wandb#13157</a>)</li>
</ul>
<h3>Changed</h3>
<ul>
<li>The default W&amp;B server is now CoreWeave Forge at <code>https://api.forge.coreweave.com</code>. Run, project, sweep and login links point to <code>https://forge.coreweave.com/wandb</code>, also when <code>base_url</code> is set to <code>https://api.wandb.ai</code> or <code>https://forge.coreweave.com/api/wandb</code>. Existing API keys stored for <code>api.wandb.ai</code> keep working without logging in again (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13077</a>)</li>
<li>The helper process that collects system metrics is now <code>wandb-symon</code> instead of <code>wandb-xpu</code> (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13165</a>)</li>
<li><code>import wandb</code> and the <code>wandb</code> CLI start about twice as fast (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13144</a>, <a href="">wandb/wandb#13145</a>, <a href="">wandb/wandb#13146</a>, <a href="">wandb/wandb#13147</a>, <a href="">wandb/wandb#13148</a>)</li>
<li>The <code>wandb</code> package is smaller: <code>wandb-core</code> shrank by about a third, from 52 MB to 35 MB on Linux x86_64, and the parquet reader and the system metrics helper by more than half (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12921</a>, <a href="">wandb/wandb#12922</a>, <a href="">wandb/wandb#12923</a>, <a href="">wandb/wandb#12924</a>, <a href="">wandb/wandb#12937</a>, <a href="">wandb/wandb#12939</a>)</li>
<li>Runs write their data to the local <code>.wandb</code> file at least every 15 seconds, so <code>wandb leet</code> shows recent data sooner for runs that log infrequently (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12742</a>)</li>
<li>The <code>cpu</code> system metric reports the monitored process's CPU utilization over the sampling interval instead of its average since the process started (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13101</a>)</li>
<li>NVIDIA GPM system metrics such as <code>gpu.N.smActive</code> and <code>gpu.N.dramActive</code> are now averaged over the whole interval between samples instead of a 200 ms window (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12987</a>)</li>
<li>AMD GPU system metrics are read through the ROCm SMI library (<code>librocm_smi64.so</code>) instead of running the <code>rocm-smi</code> tool on every sample. Readings a GPU does not provide are left out instead of reported as 0 (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12990</a>)</li>
<li>OpenMetrics and DCGM exporter endpoints are scraped once per sampling interval for all runs on the machine instead of once per run, and all runs use the same <code>openmetrics.&lt;endpoint&gt;.&lt;metric&gt;.&lt;index&gt;</code> index for the same metric labels (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#13103</a>)</li>
</ul>
<h3>Removed</h3>
<ul>
<li>Removed the undocumented <code>wandb.set_trace()</code>. Use Python's built-in <code>breakpoint()</code> instead (<a href="https://github.com/dmitryduev"><code>@​dmitryduev</code></a> in <a href="">wandb/wandb#12985</a>)</li>
</ul>
<h3>Fixed</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>15f8cbc</code></a> Bump version and update CHANGELOG for release 0.31.0</li>
<li><a href=""><code>43f5b38</code></a> chore: clean up changelog for 0.31.0 release (<a href="">#13182</a>)</li>
<li><a href=""><code>e34448a</code></a> chore(deps): update go dependencies (<a href="">#13181</a>)</li>
<li><a href=""><code>6386f39</code></a> chore(deps): update github actions (version updates) (<a href="">#13180</a>)</li>
<li><a href=""><code>445b90b</code></a> chore(sdk): make the console log filestream writer tests order-independent (#...</li>
<li><a href=""><code>b279234</code></a> chore(sdk): let pytest see PROCESSOR_ARCHITECTURE on Windows (<a href="">#13175</a>)</li>
<li><a href=""><code>c74a4d1</code></a> chore(sdk): default EvalTable back to the Weave backend (<a href="">#13172</a>)</li>
<li><a href=""><code>940d059</code></a> refactor(sdk): rename wandb-xpu to wandb-symon (<a href="">#13165</a>)</li>
<li><a href=""><code>3294377</code></a> refactor(sdk): remove the system monitor's own sampling loop (<a href="">#13158</a>)</li>
<li><a href=""><code>ee63025</code></a> feat(sdk): read the host details wandb leet symon shows from wandb-xpu (<a href="">#13157</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/wandb/wandb/compare/v0.29.0...v0.31.0">compare view</a></li>
</ul>
</details>
<br />

Updates `rdkit` from 2026.3.5 to 2026.9.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rdkit/rdkit/releases">rdkit's releases</a>.</em></p>
<blockquote>
<h2>2026_09_1 (Q3 2026) Release</h2>
<h1>Release_2026.09.1</h1>
<p>(Changes relative to Release_2026.03.1)</p>
<h2>Acknowledgements</h2>
<p>(Note: I'm no longer attempting to manually curate names. If you would like to
see your contribution acknowledged with your name, please set your name in
GitHub)</p>
<p>reza bagheri alashti, Rody Arantes, Marco Ballarotto, Chris Von Bargen, Kevin
Boyd, Katharina Buchthal, Kerim Buyukakyuz, Arthur Chan, Michael Cho, David
Cosgrove, Mike DePaulo, Eloy Félix, Peter Gedeck, Lukas Geiger, Guillaume Godin,
Huw Jones, Steven Kearnes, Brian Kelley, Jakub Klinkovský, Jimmy Kromann, Niels
Maeder, John Mayfield, Vedran Miletić, Dan Nealschneider, Dmytro Radchenko,
Emily Rhodes, Ricardo Rodriguez, Wonseok Shin, Raul Sofia, Vaibhav Srivastava,
Jon Swain, Pavel Tomanek, Paolo Tosco, Ivan Tubert-Brohman, Riccardo Vianello,
Inwan Yoo, Nic Zonta, dd, ajeyabsf, m_holmer, zengkaipeng(SII), css, reowszer,
thomp-j, vwe-ibm, ankar-dav, dpdoughe</p>
<h2>Highlights</h2>
<ul>
<li>This release includes a number of improvements to the RDKit's conformer
generator, including beta versions of ETKDGv4 and a new strategy for selecting
initial coordinates. These are not yet used by default, but we encourage people
to try them out - try the <code>rdDistGeom.ETKDGv4</code> parameters object and/or
setting <code>initialEmbeddingMode</code> to <code>rdDistGeom.INTERNAL_COORDINATE_EMBEDDING</code> -
and are looking for feedback.</li>
<li>We've created a new set of Python wrappers based on nanobind instead of
Boost::Python. The new wrappers, still in beta, are significantly faster. We
will be doing conda-forge builds of the new wrappers and would greatly
appreciate feedback from the community.</li>
<li>It's now possible to do shape-based searches in synthon spaces.</li>
</ul>
<h2>Backwards incompatible changes:</h2>
<ul>
<li>The C++ canonicalization helpers <code>Canon::initCanonAtoms()</code> and
<code>Canon::detail::initFragmentCanonAtoms()</code> now require caller-owned neighbor ID
storage. <code>Canon::canon_atom::nbrIds</code> is now a non-owning <code>std::span&lt;int&gt;</code>.</li>
<li><code>Canon::canon_atom::bonds</code> now uses <code>boost::container::small_vector</code>.</li>
<li>Since <a href="">#9208</a>, atom rings are &quot;normalized&quot; so that the first atom in the ring
definition is the one with the lowest index, and the second one is the neighbor
to the first which also has the lowest index.</li>
<li><code>MolTransforms.h</code> now includes <code>&lt;Eigen/Core&gt;</code> instead of <code>&lt;Eigen/Dense&gt;</code>. C++
code that included <code>MolTransforms.h</code> and relied on it to transitively pull in
the Eigen dense modules (LU/QR/SVD/etc.) must now include <code>&lt;Eigen/Dense&gt;</code>
directly.</li>
<li><code>PicklerOps::QueryDetails</code> (in <code>GraphMol/MolPickler.h</code>) is now a
<code>std::variant</code> instead of a <code>boost::variant</code>. C++ code that inspects this type
must use <code>std::get</code>/<code>std::holds_alternative</code> and <code>.index()</code> in place of
<code>boost::get</code> and <code>.which()</code>. <code>MolPickler.h</code> also no longer includes</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rdkit/rdkit/blob/master/ReleaseNotes.md">rdkit's changelog</a>.</em></p>
<blockquote>
<h1>Release_2027.03.1</h1>
<p>(Changes relative to Release_2026.09.1)</p>
<h2>Acknowledgements</h2>
<p>(Note: I'm no longer attempting to manually curate names. If you would like to
see your contribution acknowledged with your name, please set your name in
GitHub)</p>
<h2>Highlights</h2>
<h2>Backwards incompatible changes:</h2>
<ul>
<li><code>RingInfo</code> now stores its rings in flat, contiguous arrays, and most of its
C++ methods that returned references to <code>std::vector</code>s now return
non-owning <code>std::span</code>s or span-based views. Specifically,
<code>RingInfo::atomRings()</code> and <code>RingInfo::bondRings()</code> now return a
<code>RingInfo::RingsView</code> instead of <code>const VECT_INT_VECT &amp;</code>, and
<code>RingInfo::atomMembers()</code> and <code>RingInfo::bondMembers()</code> now return
<code>std::span&lt;const int&gt;</code> instead of <code>const INT_VECT &amp;</code>. These views are
invalidated when the <code>RingInfo</code> is modified. <code>RingInfo::addRing()</code> now takes
<code>std::span&lt;const int&gt;</code> arguments. The Python, Java, and C# APIs are unchanged.</li>
</ul>
<h2>Code removed in this release:</h2>
<h2>Deprecated code (to be removed in a future release):</h2>
<h1>Release_2026.09.1</h1>
<p>(Changes relative to Release_2026.03.1)</p>
<h2>Acknowledgements</h2>
<p>(Note: I'm no longer attempting to manually curate names. If you would like to
see your contribution acknowledged with your name, please set your name in
GitHub)</p>
<p>reza bagheri alashti, Rody Arantes, Marco Ballarotto, Chris Von Bargen, Kevin
Boyd, Katharina Buchthal, Kerim Buyukakyuz, Arthur Chan, Michael Cho, David
Cosgrove, Mike DePaulo, Eloy Félix, Peter Gedeck, Lukas Geiger, Guillaume Godin,
Huw Jones, Steven Kearnes, Brian Kelley, Jakub Klinkovský, Jimmy Kromann, Niels
Maeder, John Mayfield, Vedran Miletić, Dan Nealschneider, Dmytro Radchenko,
Emily Rhodes, Ricardo Rodriguez, Wonseok Shin, Raul Sofia, Vaibhav Srivastava,
Jon Swain, Pavel Tomanek, Paolo Tosco, Ivan Tubert-Brohman, Riccardo Vianello,
Inwan Yoo, Nic Zonta, dd, ajeyabsf, m_holmer, zengkaipeng(SII), css, reowszer,
thomp-j, vwe-ibm, ankar-dav, dpdoughe</p>
<h2>Highlights</h2>
<ul>
<li>This release includes a number of improvements to the RDKit's conformer
generator, including beta versions of ETKDGv4 and a new strategy for selecting
initial coordinates. These are not yet used by default, but we encourage people
to try them out - try the <code>rdDistGeom.ETKDGv4</code> parameters object and/or</li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7de5665007f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.