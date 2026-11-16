# Issue

**Title:** chore(deps): bump sharp from 0.35.4 to 0.35.5 in /example-ssr

## Description

Bumps [sharp](https://github.com/lovell/sharp) from 0.35.4 to 0.35.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/lovell/sharp/releases">sharp's releases</a>.</em></p>
<blockquote>
<h2>v0.35.5</h2>
<p><a href="https://github.com/lovell/sharp-libvips/releases/tag/v1.3.4">https://github.com/lovell/sharp-libvips/releases/tag/v1.3.4</a></p>
<ul>
<li>
<p>Add upper bounds check on length of <code>linear</code> and GIF <code>delay</code> arrays.</p>
</li>
<li>
<p>Improve error handing when WebAssembly fallback also fails.
<a href="">#4593</a>
<a href="https://github.com/lazerg"><code>@​lazerg</code></a></p>
</li>
<li>
<p>TypeScript: Allow multi-frame options for JXL output.
<a href="">#4602</a>
<a href="https://github.com/ramin-010"><code>@​ramin-010</code></a></p>
</li>
<li>
<p>TypeScript: Remove non-existent named export.
<a href="">#4604</a></p>
</li>
<li>
<p>Increase accepted dimensions when extending an image.
<a href="">#4605</a></p>
</li>
<li>
<p>Improve gain map support for <code>extract</code> and <code>rotate</code> operations.
<a href="">#4606</a></p>
</li>
<li>
<p>Tests: Ensure composite tests pass on big endian platforms.
<a href="">#4609</a></p>
</li>
</ul>
<h2>v0.35.5-rc.1</h2>
<p><a href="https://github.com/lovell/sharp-libvips/releases/tag/v1.3.4-rc.1">https://github.com/lovell/sharp-libvips/releases/tag/v1.3.4-rc.1</a></p>
<ul>
<li>
<p>Add upper bounds check on length of <code>linear</code> and GIF <code>delay</code> arrays.</p>
</li>
<li>
<p>Improve error handing when WebAssembly fallback also fails.
<a href="">#4593</a>
<a href="https://github.com/lazerg"><code>@​lazerg</code></a></p>
</li>
<li>
<p>TypeScript: Allow multi-frame options for JXL output.
<a href="">#4602</a>
<a href="https://github.com/ramin-010"><code>@​ramin-010</code></a></p>
</li>
<li>
<p>TypeScript: Remove non-existent named export.
<a href="">#4604</a></p>
</li>
<li>
<p>Increase accepted dimensions when extending an image.
<a href="">#4605</a></p>
</li>
<li>
<p>Improve gain map support for <code>extract</code> operation.
<a href="">#4606</a></p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>51a990f</code></a> Release v0.35.5</li>
<li><a href=""><code>96de105</code></a> Upgrade to sharp-libvips v1.3.4</li>
<li><a href=""><code>3a61390</code></a> CI: Configure Dependabot with all package.json locations</li>
<li><a href=""><code>4940c50</code></a> Improve gain map support for rotate/flip/flop ops</li>
<li><a href=""><code>20654aa</code></a> Prerelease v0.35.5-rc.1</li>
<li><a href=""><code>ef4f934</code></a> CI: Upgrade to Ubuntu 26.04</li>
<li><a href=""><code>358df95</code></a> Upgrade to libvips v8.18.7</li>
<li><a href=""><code>49f4903</code></a> Improve gain map support for rotate-then-extract <a href="">#4606</a></li>
<li><a href=""><code>0e2e55e</code></a> Silence a couple of compiler/static analysis warnings</li>
<li><a href=""><code>cef3b8c</code></a> Improve gain map support for extract operation <a href="">#4606</a></li>
<li>Additional commits viewable in <a href="https://github.com/lovell/sharp/compare/v0.35.4...v0.35.5">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `013bd1f155b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.