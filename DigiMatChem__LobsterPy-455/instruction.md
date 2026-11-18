# Issue

**Title:** Bump mendeleev from 1.2.0 to 1.3.0

## Description

Bumps [mendeleev](https://github.com/lmmentel/mendeleev) from 1.2.0 to 1.3.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/lmmentel/mendeleev/releases">mendeleev's releases</a>.</em></p>
<blockquote>
<h2>v1.3.0</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: repair deltaN, half_life_u, warnings and fetch scales bugs by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#270</a></li>
<li>Add PEP 561 py.typed marker by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#271</a></li>
<li>deps: loosen pandas/plotly specs, fix compat for newer versions by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#273</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lmmentel/mendeleev/compare/v1.2.0...v1.3.0">https://github.com/lmmentel/mendeleev/compare/v1.2.0...v1.3.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/lmmentel/mendeleev/blob/master/CHANGES.rst">mendeleev's changelog</a>.</em></p>
<blockquote>
<h2>v1.3.0 (10.09.2026)</h2>
<ul>
<li>[MNT] Loosen <code>pandas</code> dependency to <code>&gt;=2.1</code> and <code>plotly</code> to <code>&gt;=5.0</code> to allow newer major versions by :user:<code>@lmmentel</code> in :pr:<code>273</code></li>
<li>[FIX] Replace deprecated <code>pandas.api.types.is_float_dtype()</code> with <code>np.issubdtype()</code> for pandas 3.0 compat by :user:<code>@lmmentel</code> in :pr:<code>273</code></li>
<li>[FIX] Fix <code>FutureWarning</code> in <code>vis/utils.py</code> groupby.apply by selecting column before apply by :user:<code>@lmmentel</code> in :pr:<code>273</code></li>
<li>[FIX] Fix <code>deltaN</code> that crashed with an <code>AttributeError</code> after the electronegativity refactor by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
<li>[FIX] Fix typo in <code>Isotope.half_life_u</code> (<code>half_file</code> -&gt; <code>half_life</code>) by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
<li>[FIX] Fix literal <code>{symbol}</code> placeholder in multi-allotrope phase transition warnings by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
<li>[FIX] Make <code>fetch_electronegativities</code> respect the <code>scales</code> argument by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
<li>[MNT] Consolidate missing-value handling in <code>electronegativity.mulliken</code> and <code>Element.electronegativity_mulliken</code> by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
<li>[DOC] Fix <code>fetch_electronegativities</code> quick start example and replace removed <code>en_mulliken</code> references by :user:<code>@lmmentel</code> in :pr:<code>270</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bd4716b</code></a> fix: add python&lt;3.12 marker to pandas-stubs, regenerate lock</li>
<li><a href=""><code>c48d615</code></a> Bump version: 1.2.0 → 1.3.0</li>
<li><a href=""><code>fe323a8</code></a> deps: loosen pandas/plotly specs, fix compat for newer versions (<a href="">#273</a>)</li>
<li><a href=""><code>f81e9aa</code></a> Add PEP 561 py.typed marker for type checker support (<a href="">#271</a>)</li>
<li><a href=""><code>1b916a9</code></a> fix: repair deltaN, half_life_u, warnings and fetch scales bugs (<a href="">#270</a>)</li>
<li><a href=""><code>0f27ba0</code></a> wMerge branch 'master' of github.com:lmmentel/mendeleev</li>
<li><a href=""><code>7319374</code></a> Release v1.2.0 (<a href="">#268</a>)</li>
<li>See full diff in <a href="https://github.com/lmmentel/mendeleev/compare/v1.2.0...v1.3.0">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ff91466e370`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.