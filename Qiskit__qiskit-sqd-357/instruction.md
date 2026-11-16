# Issue

**Title:** Bump mypy from 2.3.0 to 2.3.1

## Description

Bumps [mypy](https://github.com/python/mypy) from 2.3.0 to 2.3.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/mypy/blob/master/CHANGELOG.md">mypy's changelog</a>.</em></p>
<blockquote>
<h3>Mypy 2.3.1</h3>
<ul>
<li>Fix mypyc crash on double yielding Iterators (Daniël van Noord, PR <a href="">21826</a>)</li>
<li>Fix mypyc <code>default_factory</code> for inherited dataclass (Daniël van Noord, PR <a href="">21785</a>)</li>
<li>Clear mypyc coroutine env on coroutine completion (Piotr Sawicki, PR <a href="">21734</a>)</li>
<li>Fix crash when unpacking return value from overload (Shantanu, PR <a href="">21830</a>)</li>
</ul>
<h3>Acknowledgements</h3>
<p>Thanks to all mypy contributors who contributed to this release:</p>
<ul>
<li>Agriya Khetarpal</li>
<li>Ethan Sarp</li>
<li>Ivan Levkivskyi</li>
<li>Jingchen Ye</li>
<li>Jukka Lehtosalo</li>
<li>Piotr Sawicki</li>
<li>Shantanu</li>
<li>Tom Bannink</li>
<li>Viktor Szépe</li>
<li>ygale</li>
</ul>
<p>I'd also like to thank my employer, Dropbox, for supporting mypy development.</p>
<h2>Mypy 2.2</h2>
<p>We've just uploaded mypy 2.2.0 to the Python Package Index (<a href="https://pypi.org/project/mypy/">PyPI</a>).
Mypy is a static type checker for Python. This release includes new features, performance
improvements and bug fixes. You can install it as follows:</p>
<pre><code>python3 -m pip install -U mypy
</code></pre>
<p>You can read the full documentation for this release on <a href="http://mypy.readthedocs.io">Read the Docs</a>.</p>
<h3>Support for Closed TypedDicts (PEP 728)</h3>
<p>Mypy now supports closed TypedDicts as specified in PEP 728. A closed TypedDict cannot have extra
keys beyond those explicitly defined. This allows the type checker to determine that certain
operations are safe when they otherwise wouldn't be due to the potential presence of unknown keys.</p>
<p>You can use the <code>closed</code> keyword argument with <code>TypedDict</code>:</p>
<pre lang="python"><code>HasName = TypedDict(&quot;HasName&quot;, {&quot;name&quot;: str})
HasOnlyName = TypedDict(&quot;HasOnlyName&quot;, {&quot;name&quot;: str}, closed=True)
Movie = TypedDict(&quot;Movie&quot;, {&quot;name&quot;: str, &quot;year&quot;: int})
<p>movie: Movie = {&quot;name&quot;: &quot;Nimona&quot;, &quot;year&quot;: 2023}
has_name: HasName = movie  # OK: HasName is open (default)
has_only_name: HasOnlyName = movie  # Error: HasOnlyName is closed and Movie has extra &quot;year&quot; key
&lt;/tr&gt;&lt;/table&gt;
</code></pre></p>
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d642c44</code></a> Bump version to 2.3.1</li>
<li><a href=""><code>a392429</code></a> [mypyc] Fix crash on double yielding Iterators (<a href="">#21826</a>)</li>
<li><a href=""><code>4843e77</code></a> [mypyc] Fix <code>default_factory</code> for inherited dataclass (<a href="">#21785</a>)</li>
<li><a href=""><code>14f5df9</code></a> [mypyc] Clear coroutine env on coroutine completion (<a href="">#21734</a>)</li>
<li><a href=""><code>6dfa06d</code></a> Fix crash when unpacking return value from overload (<a href="">#21830</a>)</li>
<li><a href=""><code>a385746</code></a> Bump version to 2.3.1+dev</li>
<li>See full diff in <a href="https://github.com/python/mypy/compare/v2.3.0...v2.3.1">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08cf70fc5705`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.