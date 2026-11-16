# Issue

**Title:** chore(deps): bump the minor-and-patch group across 1 directory with 26 updates

## Description

Bumps the minor-and-patch group with 24 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [@ai-sdk/anthropic](https://github.com/vercel/ai/tree/HEAD/packages/anthropic) | `3.0.64` | `3.0.76` |
| [@ai-sdk/openai](https://github.com/vercel/ai/tree/HEAD/packages/openai) | `3.0.49` | `3.0.63` |
| [@ai-sdk/react](https://github.com/vercel/ai/tree/HEAD/packages/react) | `3.0.145` | `3.0.179` |
| [@codemirror/view](https://github.com/codemirror/view) | `6.41.0` | `6.42.1` |
| [@huggingface/hub](https://github.com/huggingface/huggingface.js) | `2.11.0` | `2.11.2` |
| [@larksuiteoapi/node-sdk](https://github.com/larksuite/node-sdk) | `1.60.0` | `1.63.1` |
| [better-sqlite3](https://github.com/WiseLibs/better-sqlite3) | `12.8.0` | `12.9.0` |
| [katex](https://github.com/KaTeX/KaTeX) | `0.16.44` | `0.16.45` |
| [lucide-react](https://github.com/lucide-icons/lucide/tree/HEAD/packages/lucide-react) | `1.7.0` | `1.14.0` |
| [nanoid](https://github.com/ai/nanoid) | `5.1.7` | `5.1.11` |
| [next](https://github.com/vercel/next.js) | `16.2.2` | `16.2.6` |
| [next-intl](https://github.com/amannn/next-intl) | `4.9.0` | `4.11.1` |
| [react](https://github.com/facebook/react/tree/HEAD/packages/react) | `19.2.4` | `19.2.6` |
| [react-dom](https://github.com/facebook/react/tree/HEAD/packages/react-dom) | `19.2.4` | `19.2.6` |
| [react-resizable-panels](https://github.com/bvaughn/react-resizable-panels) | `4.8.0` | `4.11.0` |
| [tailwind-merge](https://github.com/dcastil/tailwind-merge) | `3.5.0` | `3.6.0` |
| [three](https://github.com/mrdoob/three.js) | `0.183.2` | `0.184.0` |
| [zod](https://github.com/colinhacks/zod) | `4.3.6` | `4.4.3` |
| [@tailwindcss/postcss](https://github.com/tailwindlabs/tailwindcss/tree/HEAD/packages/@tailwindcss-postcss) | `4.2.2` | `4.3.0` |
| [@types/node](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/HEAD/types/node) | `25.5.0` | `25.6.2` |
| [@types/three](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/HEAD/types/three) | `0.183.1` | `0.184.1` |
| [eslint-config-next](https://github.com/vercel/next.js/tree/HEAD/packages/eslint-config-next) | `16.2.2` | `16.2.6` |
| [shadcn](https://github.com/shadcn-ui/ui/tree/HEAD/packages/shadcn) | `4.1.2` | `4.7.0` |
| [vitest](https://github.com/vitest-dev/vitest/tree/HEAD/packages/vitest) | `4.1.2` | `4.1.5` |

Updates `@ai-sdk/anthropic` from 3.0.64 to 3.0.76
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/releases">@​ai-sdk/anthropic's releases</a>.</em></p>
<blockquote>
<h2><code>@​ai-sdk/google</code><a href="https://github.com/3"><code>@​3</code></a>.0.71</h2>
<h3>Patch Changes</h3>
<ul>
<li>
<p>59530cf: fix(google): emit Vertex no-args streaming tool calls and preserve thoughtSignature</p>
<p>Vertex emits a no-args function call as a single chunk shaped <code>{ functionCall: { name: 'X' } }</code> with no <code>args</code>, no <code>partialArgs</code>, and no <code>willContinue</code>. The streaming parser had no branch for this shape, so the call was dropped along with any <code>thoughtSignature</code> it carried. For Gemini 3 thinking models this caused the next multi-turn step to 400 with <code>missing thought_signature</code>. The unary (<code>doGenerate</code>) path had the same drop.</p>
<p>Both paths now emit the call as a complete tool call with <code>'{}'</code> input and propagate <code>thoughtSignature</code> provider metadata.</p>
<p>Fixes <a href="">#14847</a>.</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/blob/@ai-sdk/anthropic@3.0.76/packages/anthropic/CHANGELOG.md">@​ai-sdk/anthropic's changelog</a>.</em></p>
<blockquote>
<h2>3.0.76</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [f591416]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.27</li>
</ul>
</li>
</ul>
<h2>3.0.75</h2>
<h3>Patch Changes</h3>
<ul>
<li>3f06680: Remove stale <code>effort-2025-11-24</code> beta header — the extended thinking effort parameter is GA and no longer requires the beta flag. Vertex AI's strict validator was actively rejecting requests with this header.</li>
</ul>
<h2>3.0.74</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [7beadf0]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.26</li>
</ul>
</li>
</ul>
<h2>3.0.73</h2>
<h3>Patch Changes</h3>
<ul>
<li>f8c9ae4: feat(anthropic): sanitize the unsupported JSON schema validation properties</li>
<li>a727da4: chore: ensure consistent import handling and avoid import duplicates or cycles</li>
<li>Updated dependencies [a727da4]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.25</li>
<li><code>@​ai-sdk/provider</code><a href="https://github.com/3"><code>@​3</code></a>.0.10</li>
</ul>
</li>
</ul>
<h2>3.0.72</h2>
<h3>Patch Changes</h3>
<ul>
<li>a7f3c72: trigger release for all packages after provenance setup</li>
<li>Updated dependencies [a7f3c72]
<ul>
<li><code>@​ai-sdk/provider</code><a href="https://github.com/3"><code>@​3</code></a>.0.9</li>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.24</li>
</ul>
</li>
</ul>
<h2>3.0.71</h2>
<h3>Patch Changes</h3>
<ul>
<li>95b4fe0: fix(provider/anthropic): stop adding <code>fine-grained-tool-streaming-2025-05-14</code> beta for <code>claude-opus-4-7</code></li>
</ul>
<h2>3.0.70</h2>
<h3>Patch Changes</h3>
<ul>
<li>2ff8d57: feat(provider/anthropic): add support for Opus 4.7 and relevant API enhancements</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e3ccdb5</code></a> Version Packages (<a href="">#15094</a>)</li>
<li><a href=""><code>74a7a20</code></a> Version Packages (<a href="">#15012</a>)</li>
<li><a href=""><code>3f06680</code></a> Backport: fix(anthropic): remove stale effort-2025-11-24 beta header (<a href="">#15011</a>)</li>
<li><a href=""><code>8a46a3c</code></a> Version Packages (<a href="">#14875</a>)</li>
<li><a href=""><code>8e650ab</code></a> Version Packages (<a href="">#14824</a>)</li>
<li><a href=""><code>a727da4</code></a> backport of chore: ensure consistent import handling and avoid import duplica...</li>
<li><a href=""><code>f8c9ae4</code></a> backport v6: feat (provider/anthropic): sanitize unsupported json schema vali...</li>
<li><a href=""><code>77a4e05</code></a> Version Packages (<a href="">#14802</a>)</li>
<li><a href=""><code>a7f3c72</code></a> Re-enable v6 releases (<a href="">#14799</a>)</li>
<li><a href=""><code>f93eca6</code></a> Version Packages (<a href="">#14564</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/ai/commits/@ai-sdk/anthropic@3.0.76/packages/anthropic">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for <code>@​ai-sdk/anthropic</code> since your current version.</p>
</details>
<br />

Updates `@ai-sdk/openai` from 3.0.49 to 3.0.63
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/blob/@ai-sdk/openai@3.0.63/packages/openai/CHANGELOG.md">@​ai-sdk/openai's changelog</a>.</em></p>
<blockquote>
<h2>3.0.63</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [f591416]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.27</li>
</ul>
</li>
</ul>
<h2>3.0.62</h2>
<h3>Patch Changes</h3>
<ul>
<li>65edcca: feat: add allowedTools provider option for OpenAI Responses</li>
</ul>
<h2>3.0.61</h2>
<h3>Patch Changes</h3>
<ul>
<li>b93f9b4: feat(provider/openai): forward imageDetail providerOptions on tool-result image content</li>
</ul>
<h2>3.0.60</h2>
<h3>Patch Changes</h3>
<ul>
<li>6dcd8e6: feat(openai): add GPT-5.5 chat model IDs</li>
</ul>
<h2>3.0.59</h2>
<h3>Patch Changes</h3>
<ul>
<li>38966ab: fix(openai, openai-compatible): only send null content for assistant messages with tool calls</li>
</ul>
<h2>3.0.58</h2>
<h3>Patch Changes</h3>
<ul>
<li>2370948: feat(openai): preserve <code>namespace</code> on function_call output items</li>
</ul>
<h2>3.0.57</h2>
<h3>Patch Changes</h3>
<ul>
<li>d33e7cc: chore(provider/openai): add type for image model options for type-safe processing</li>
</ul>
<h2>3.0.56</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [7beadf0]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.26</li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e3ccdb5</code></a> Version Packages (<a href="">#15094</a>)</li>
<li><a href=""><code>bf9de31</code></a> Version Packages (<a href="">#15046</a>)</li>
<li><a href=""><code>65edcca</code></a> Backport: feat(openai): add allowedTools provider option for Responses (<a href="">#15044</a>)</li>
<li><a href=""><code>ee37690</code></a> Version Packages (<a href="">#15020</a>)</li>
<li><a href=""><code>b93f9b4</code></a> Backport: feat(provider/openai): forward imageDetail providerOptions on tool-...</li>
<li><a href=""><code>c706111</code></a> Version Packages (<a href="">#14971</a>)</li>
<li><a href=""><code>6dcd8e6</code></a> Backport: feat(openai): add GPT-5.5 chat model IDs (<a href="">#14965</a>)</li>
<li><a href=""><code>a1dddcc</code></a> Version Packages (<a href="">#14954</a>)</li>
<li><a href=""><code>38966ab</code></a> backport v6: fix(openai, openai-compatible): only send null content for assis...</li>
<li><a href=""><code>0129eb6</code></a> Version Packages (<a href="">#14912</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/ai/commits/@ai-sdk/openai@3.0.63/packages/openai">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for <code>@​ai-sdk/openai</code> since your current version.</p>
</details>
<br />

Updates `@ai-sdk/react` from 3.0.145 to 3.0.179
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/releases">@​ai-sdk/react's releases</a>.</em></p>
<blockquote>
<h2><code>@​ai-sdk/react</code><a href="https://github.com/3"><code>@​3</code></a>.0.179</h2>
<h3>Patch Changes</h3>
<ul>
<li>ai@6.0.177</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/blob/@ai-sdk/react@3.0.179/packages/react/CHANGELOG.md">@​ai-sdk/react's changelog</a>.</em></p>
<blockquote>
<h2>3.0.179</h2>
<h3>Patch Changes</h3>
<ul>
<li>ai@6.0.177</li>
</ul>
<h2>3.0.178</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [f591416]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.27</li>
<li>ai@6.0.176</li>
</ul>
</li>
</ul>
<h2>3.0.177</h2>
<h3>Patch Changes</h3>
<ul>
<li>ai@6.0.175</li>
</ul>
<h2>3.0.176</h2>
<h3>Patch Changes</h3>
<ul>
<li>ai@6.0.174</li>
</ul>
<h2>3.0.175</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [7beadf0]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.26</li>
<li>ai@6.0.173</li>
</ul>
</li>
</ul>
<h2>3.0.174</h2>
<h3>Patch Changes</h3>
<ul>
<li>ai@6.0.172</li>
</ul>
<h2>3.0.173</h2>
<h3>Patch Changes</h3>
<ul>
<li>a727da4: chore: ensure consistent import handling and avoid import duplicates or cycles</li>
<li>Updated dependencies [48f842a]</li>
<li>Updated dependencies [a727da4]</li>
<li>Updated dependencies [5fee301]
<ul>
<li>ai@6.0.171</li>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.25</li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e70aab9</code></a> Version Packages (<a href="">#15138</a>)</li>
<li><a href=""><code>e3ccdb5</code></a> Version Packages (<a href="">#15094</a>)</li>
<li><a href=""><code>3015153</code></a> Version Packages (<a href="">#14960</a>)</li>
<li><a href=""><code>0129eb6</code></a> Version Packages (<a href="">#14912</a>)</li>
<li><a href=""><code>8a46a3c</code></a> Version Packages (<a href="">#14875</a>)</li>
<li><a href=""><code>29c80ec</code></a> Version Packages (<a href="">#14868</a>)</li>
<li><a href=""><code>8e650ab</code></a> Version Packages (<a href="">#14824</a>)</li>
<li><a href=""><code>a727da4</code></a> backport of chore: ensure consistent import handling and avoid import duplica...</li>
<li><a href=""><code>7ab1e18</code></a> Version Packages (<a href="">#14815</a>)</li>
<li><a href=""><code>77a4e05</code></a> Version Packages (<a href="">#14802</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/ai/commits/@ai-sdk/react@3.0.179/packages/react">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for <code>@​ai-sdk/react</code> since your current version.</p>
</details>
<br />

Updates `@codemirror/view` from 6.41.0 to 6.42.1
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/codemirror/view/commits">compare view</a></li>
</ul>
</details>
<br />

Updates `@huggingface/hub` from 2.11.0 to 2.11.2
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dad81d1</code></a> 🔖 <code>@​huggingface/hub</code> 2.11.2</li>
<li><a href=""><code>a3e062b</code></a> 🔖 <code>@​huggingface/xetchunk-wasm</code> 0.0.6</li>
<li><a href=""><code>384eb4e</code></a> 🔖 <code>@​huggingface/xetchunk-wasm</code> 0.0.5</li>
<li><a href=""><code>4bc7043</code></a> Add repository field to wasm/jit package.json</li>
<li><a href=""><code>42ca2ae</code></a> 🔖 <code>@​huggingface/hub</code> 2.11.1</li>
<li><a href=""><code>a77f908</code></a> [Hub] Dedupe file entries by xet hash within a shard (<a href="">#2134</a>)</li>
<li><a href=""><code>ac45210</code></a> fix &quot;browser&quot; test (<a href="">#2118</a>)</li>
<li><a href=""><code>0ba04a0</code></a> 🔖 <code>@​huggingface/tasks</code> 0.20.24</li>
<li><a href=""><code>b71006b</code></a> Add Hermes Agent to local apps (<a href="">#2143</a>)</li>
<li><a href=""><code>5ddf2ca</code></a> feat: add workstation gfx1100 cards to hardware list (<a href="">#2142</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/huggingface/huggingface.js/compare/hub-v2.11.0...hub-v2.11.2">compare view</a></li>
</ul>
</details>
<br />

Updates `@larksuiteoapi/node-sdk` from 1.60.0 to 1.63.1
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/larksuite/node-sdk/commits">compare view</a></li>
</ul>
</details>
<br />

Updates `ai` from 6.0.143 to 6.0.177
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/releases">ai's releases</a>.</em></p>
<blockquote>
<h2>ai@6.0.177</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [5c73af8]
<ul>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.112</li>
</ul>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vercel/ai/blob/ai@6.0.177/packages/ai/CHANGELOG.md">ai's changelog</a>.</em></p>
<blockquote>
<h2>6.0.177</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [5c73af8]
<ul>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.112</li>
</ul>
</li>
</ul>
<h2>6.0.176</h2>
<h3>Patch Changes</h3>
<ul>
<li>f591416: feat(ai): add toolMetadata for tool specific metdata</li>
<li>Updated dependencies [f591416]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.27</li>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.111</li>
</ul>
</li>
</ul>
<h2>6.0.175</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [9a88b1d]
<ul>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.110</li>
</ul>
</li>
</ul>
<h2>6.0.174</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [49f6d44]
<ul>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.109</li>
</ul>
</li>
</ul>
<h2>6.0.173</h2>
<h3>Patch Changes</h3>
<ul>
<li>7beadf0: feat(mcp): propagate the server name through dynamic tool parts</li>
<li>Updated dependencies [7beadf0]
<ul>
<li><code>@​ai-sdk/provider-utils</code><a href="https://github.com/4"><code>@​4</code></a>.0.26</li>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.108</li>
</ul>
</li>
</ul>
<h2>6.0.172</h2>
<h3>Patch Changes</h3>
<ul>
<li>Updated dependencies [982af78]
<ul>
<li><code>@​ai-sdk/gateway</code><a href="https://github.com/3"><code>@​3</code></a>.0.107</li>
</ul>
</li>
</ul>
<h2>6.0.171</h2>
<h3>Patch Changes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e70aab9</code></a> Version Packages (<a href="">#15138</a>)</li>
<li><a href=""><code>e3ccdb5</code></a> Version Packages (<a href="">#15094</a>)</li>
<li><a href=""><code>f591416</code></a> Backport: feat(ai): add toolMetadata for tool specific metdata (<a href="">#15053</a>)</li>
<li><a href=""><code>0084974</code></a> Backport: feat(mcp): deprecate name and use clientName for MCPClient (<a href="">#15003</a>)</li>
<li><a href=""><code>3015153</code></a> Version Packages (<a href="">#14960</a>)</li>
<li><a href=""><code>0129eb6</code></a> Version Packages (<a href="">#14912</a>)</li>
<li><a href=""><code>8a46a3c</code></a> Version Packages (<a href="">#14875</a>)</li>
<li><a href=""><code>7beadf0</code></a> Backport: feat(mcp): propagate the server name through dynamic tool parts (<a href="">#1</a>...</li>
<li><a href=""><code>29c80ec</code></a> Version Packages (<a href="">#14868</a>)</li>
<li><a href=""><code>8e650ab</code></a> Version Packages (<a href="">#14824</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/ai/commits/ai@6.0.177/packages/ai">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for ai since your current version.</p>
</details>
<br />

Updates `better-sqlite3` from 12.8.0 to 12.9.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/WiseLibs/better-sqlite3/releases">better-sqlite3's releases</a>.</em></p>
<blockquote>
<h2>v12.9.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Update SQLite to version 3.53.0 in <a href="">WiseLibs/better-sqlite3#1464</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/WiseLibs/better-sqlite3/compare/v12.8.0...v12.9.0">https://github.com/WiseLibs/better-sqlite3/compare/v12.8.0...v12.9.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4058d24</code></a> 12.9.0</li>
<li><a href=""><code>f653513</code></a> Update SQLite to version 3.53.0 (<a href="">#1464</a>)</li>
<li>See full diff in <a href="https://github.com/WiseLibs/better-sqlite3/compare/v12.8.0...v12.9.0">compare view</a></li>
</ul>
</details>
<br />

Updates `katex` from 0.16.44 to 0.16.45
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/KaTeX/KaTeX/releases">katex's releases</a>.</em></p>
<blockquote>
<h2>v0.16.45</h2>
<h2><a href="https://github.com/KaTeX/KaTeX/compare/v0.16.44...v0.16.45">0.16.45</a> (2026-04-05)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>wrap vcenter mpadded in mrow for valid MathML (<a href="">#4193</a>) (<a href="">ee66b78</a>), closes <a href="">#4078</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/KaTeX/KaTeX/blob/main/CHANGELOG.md">katex's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/KaTeX/KaTeX/compare/v0.16.44...v0.16.45">0.16.45</a> (2026-04-05)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>wrap vcenter mpadded in mrow for valid MathML (<a href="">#4193</a>) (<a href="">ee66b78</a>), closes <a href="">#4078</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>90de979</code></a> chore(release): 0.16.45 [ci skip]</li>
<li><a href=""><code>ee66b78</code></a> fix: wrap vcenter mpadded in mrow for valid MathML (<a href="">#4193</a>)</li>
<li><a href=""><code>ed12205</code></a> refactor: move inline double brushs stroke to helper (<a href="">#4194</a>)</li>
<li><a href=""><code>434d4b8</code></a> chore(ci): upgrade to node 24 (<a href="">#4189</a>)</li>
<li><a href=""><code>844a324</code></a> chore(deps): bump codecov/codecov-action from 5 to 6 (<a href="">#4188</a>)</li>
<li><a href=""><code>5675226</code></a> chore(deps): bump actions/github-script from 7 to 8 (<a href="">#4179</a>)</li>
<li><a href=""><code>34ad75e</code></a> chore(deps): bump actions/setup-node from 4 to 6 (<a href="">#4180</a>)</li>
<li><a href=""><code>2525c20</code></a> chore(deps): bump actions/upload-artifact from 4 to 7 (<a href="">#4176</a>)</li>
<li>See full diff in <a href="https://github.com/KaTeX/KaTeX/compare/v0.16.44...v0.16.45">compare view</a></li>
</ul>
</details>
<br />

Updates `lucide-react` from 1.7.0 to 1.14.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/lucide-icons/lucide/releases">lucide-react's releases</a>.</em></p>
<blockquote>
<h2>Version 1.14.0</h2>
<h2>What's Changed</h2>
<ul>
<li>feat(icons): added <code>repeat-off</code> icon by <a href="https://github.com/jguddas"><code>@​jguddas</code></a> in <a href="">lucide-icons/lucide#3102</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lucide-icons/lucide/compare/1.13.0...1.14.0">https://github.com/lucide-icons/lucide/compare/1.13.0...1.14.0</a></p>
<h2>Version 1.13.0</h2>
<h2>What's Changed</h2>
<ul>
<li>fix(docs): sync URL params with UI state on categories page by <a href="https://github.com/taimar"><code>@​taimar</code></a> in <a href="">lucide-icons/lucide#4111</a></li>
<li>feat(icons): add <code>waves-vertical</code> icon by <a href="https://github.com/jamiemlaw"><code>@​jamiemlaw</code></a> in <a href="">lucide-icons/lucide#3867</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lucide-icons/lucide/compare/1.12.0...1.13.0">https://github.com/lucide-icons/lucide/compare/1.12.0...1.13.0</a></p>
<h2>Version 1.12.0</h2>
<h2>What's Changed</h2>
<ul>
<li>feat(icon): add folder-bookmark icon by <a href="https://github.com/swastik7805"><code>@​swastik7805</code></a> in <a href="">lucide-icons/lucide#4262</a></li>
<li>docs(readme): Update readme files by <a href="https://github.com/ericfennis"><code>@​ericfennis</code></a> in <a href="">lucide-icons/lucide#4320</a></li>
<li>feat(icons): added <code>astroid</code> icon by <a href="https://github.com/whoisBugsbunny"><code>@​whoisBugsbunny</code></a> in <a href="">lucide-icons/lucide#4217</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lucide-icons/lucide/compare/1.10.0...1.12.0">https://github.com/lucide-icons/lucide/compare/1.10.0...1.12.0</a></p>
<h2>Version 1.11.0</h2>
<h2>What's Changed</h2>
<ul>
<li>docs: add missing period to TypeScript Support description by <a href="https://github.com/jglu"><code>@​jglu</code></a> in <a href="">lucide-icons/lucide#4309</a></li>
<li>fix(<code>@​lucide/svelte</code>): proper doc comments for svelte components by <a href="https://github.com/blt-r"><code>@​blt-r</code></a> in <a href="">lucide-icons/lucide#4267</a></li>
<li>chore(deps): bump svgo from 3.3.2 to 3.3.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">lucide-icons/lucide#4119</a></li>
<li>chore(deps-dev): bump astro from 6.0.8 to 6.1.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">lucide-icons/lucide#4310</a></li>
<li>feat(icons): add power and quick tags to zap and zap-off by <a href="https://github.com/swastik7805"><code>@​swastik7805</code></a> in <a href="">lucide-icons/lucide#4268</a></li>
<li>test(build-font): added comprehensive unit tests on build-font tool by <a href="https://github.com/karsa-mistmere"><code>@​karsa-mistmere</code></a> in <a href="">lucide-icons/lucide#4315</a></li>
<li>feat(docs): blur background of framework-select by <a href="https://github.com/Spleefies"><code>@​Spleefies</code></a> in <a href="">lucide-icons/lucide#4238</a></li>
<li>feat(icon): add heart-x icon  by <a href="https://github.com/swastik7805"><code>@​swastik7805</code></a> in <a href="">lucide-icons/lucide#4264</a></li>
<li>fix(icons): optimised <code>rotate-3d</code> icon by <a href="https://github.com/jamiemlaw"><code>@​jamiemlaw</code></a> in <a href="">lucide-icons/lucide#4299</a></li>
<li>feat(icons): added <code>layers-minus</code> icon by <a href="https://github.com/Spleefies"><code>@​Spleefies</code></a> in <a href="">lucide-icons/lucide#4005</a></li>
<li>feat(icons): added <code>bell-check</code> icon by <a href="https://github.com/pettelau"><code>@​pettelau</code></a> in <a href="">lucide-icons/lucide#4152</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/jglu"><code>@​jglu</code></a> made their first contribution in <a href="">lucide-icons/lucide#4309</a></li>
<li><a href="https://github.com/pettelau"><code>@​pettelau</code></a> made their first contribution in <a href="">lucide-icons/lucide#4152</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lucide-icons/lucide/compare/1.9.0...1.11.0">https://github.com/lucide-icons/lucide/compare/1.9.0...1.11.0</a></p>
<h2>Version 1.10.0</h2>
<h2>What's Changed</h2>
<ul>
<li>docs: add missing period to TypeScript Support description by <a href="https://github.com/jglu"><code>@​jglu</code></a> in <a href="">lucide-icons/lucide#4309</a></li>
<li>fix(<code>@​lucide/svelte</code>): proper doc comments for svelte components by <a href="https://github.com/blt-r"><code>@​blt-r</code></a> in <a href="">lucide-icons/lucide#4267</a></li>
<li>chore(deps): bump svgo from 3.3.2 to 3.3.3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">lucide-icons/lucide#4119</a></li>
<li>chore(deps-dev): bump astro from 6.0.8 to 6.1.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">lucide-icons/lucide#4310</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>50d8af5</code></a> docs(readme): Update readme files (<a href="">#4320</a>)</li>
<li><a href=""><code>653e44b</code></a> feat(packages): use .mjs for ESM bundles (<a href="">#4285</a>)</li>
<li><a href=""><code>7623e23</code></a> feat(docs): add Zephyr Cloud to Hero Backers tier &amp; rework updateSponsors scr...</li>
<li>See full diff in <a href="https://github.com/lucide-icons/lucide/commits/1.14.0/packages/lucide-react">compare view</a></li>
</ul>
</details>
<br />

Updates `nanoid` from 5.1.7 to 5.1.11
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ai/nanoid/releases">nanoid's releases</a>.</em></p>
<blockquote>
<h2>5.1.11</h2>
<ul>
<li>Fixed breaking Nano ID by requesting big ID.</li>
</ul>
<h2>5.1.10</h2>
<ul>
<li>Fixed breaking nanoid by requesting big ID (by <a href="https://github.com/alanzabihi"><code>@​alanzabihi</code></a>).</li>
</ul>
<h2>5.1.9</h2>
<ul>
<li>Fixed npm package size regression.</li>
</ul>
<h2>5.1.8</h2>
<ul>
<li>Made <code>cusatomAlphabet</code> 75% faster (by <a href="https://github.com/saripovdenis"><code>@​saripovdenis</code></a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ai/nanoid/blob/main/CHANGELOG.md">nanoid's changelog</a>.</em></p>
<blockquote>
<h2>5.1.11</h2>
<ul>
<li>Fixed breaking Nano ID by requesting big ID.</li>
</ul>
<h2>5.1.10</h2>
<ul>
<li>Fixed breaking Nano ID by requesting big ID (by <a href="https://github.com/alanzabihi"><code>@​alanzabihi</code></a>).</li>
</ul>
<h2>5.1.9</h2>
<ul>
<li>Fixed npm package size regression.</li>
</ul>
<h2>5.1.8</h2>
<ul>
<li>Made <code>cusatomAlphabet</code> 75% faster (by <a href="https://github.com/saripovdenis"><code>@​saripovdenis</code></a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5423cf5</code></a> Release 5.1.11 version</li>
<li><a href=""><code>2183894</code></a> Backport 3.3.12 changelog</li>
<li><a href=""><code>7087969</code></a> Limit ID even more</li>
<li><a href=""><code>013517b</code></a> Temporary add pnpm-workspace.yaml to npm ignore</li>
<li><a href=""><code>5db09ee</code></a> Release 5.1.10 version</li>
<li><a href=""><code>be7901a</code></a> Fix random pool break</li>
<li><a href=""><code>974f73b</code></a> Structure tests with describe() instead of prefix</li>
<li><a href=""><code>fe3e7ec</code></a> Update dependencies</li>
<li><a href=""><code>043a7c1</code></a> Move to pnpm 11</li>
<li><a href=""><code>e52d946</code></a> Release 5.1.9 version</li>
<li>Additional commits viewable in <a href="https://github.com/ai/nanoid/compare/5.1.7...5.1.11">compare view</a></li>
</ul>
</details>
<br />

Updates `next` from 16.2.2 to 16.2.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vercel/next.js/releases">next's releases</a>.</em></p>
<blockquote>
<h2>v16.2.6</h2>
<p>This release contains security fixes for the following advisories:</p>
<p>High:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj">GHSA-8h8q-6873-q5fj: Denial of Service with Server Components</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-267c-6grr-h53f">GHSA-267c-6grr-h53f: Middleware / Proxy bypass in App Router applications via segment-prefetch routes</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-26hh-7cqf-hhc6">GHSA-26hh-7cqf-hhc6: Middleware / Proxy bypass in App Router applications via segment-prefetch routes - Incomplete Fix Follow-Up</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-mg66-mrh9-m8jx">GHSA-mg66-mrh9-m8jx: Denial of Service via connection exhaustion in applications using Cache Components</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv">GHSA-492v-c6pp-mqqv: Middleware / Proxy bypass through dynamic route parameter injection</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r">GHSA-c4j6-fc7j-m34r: Server-side request forgery in applications using WebSocket upgrades</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-36qx-fr4f-26g5">GHSA-36qx-fr4f-26g5: Middleware / Proxy bypass in Pages Router applications using i18n</a></li>
</ul>
<p>Moderate:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-ffhc-5mcf-pf4q">GHSA-ffhc-5mcf-pf4q: Cross-site scripting in App Router applications using CSP nonces</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-gx5p-jg67-6x7h">GHSA-gx5p-jg67-6x7h: Cross-site scripting in beforeInteractive scripts with untrusted input</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-h64f-5h5j-jqjh">GHSA-h64f-5h5j-jqjh: Denial of Service in the Image Optimization API</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-wfc6-r584-vfw7">GHSA-wfc6-r584-vfw7: Cache poisoning in React Server Component responses</a></li>
</ul>
<p>Low:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-vfv6-92ff-j949">GHSA-vfv6-92ff-j949: Cache poisoning via collisions in React Server Component cache-busting</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-3g8h-86w9-wvmq">GHSA-3g8h-86w9-wvmq: Middleware / Proxy redirects can be cache-poisoned</a></li>
</ul>
<h2>v16.2.5</h2>
<p>This release contains security fixes for the following advisories:</p>
<p>High:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj">GHSA-8h8q-6873-q5fj: Denial of Service with Server Components</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-267c-6grr-h53f">GHSA-267c-6grr-h53f: Middleware / Proxy bypass in App Router applications via segment-prefetch routes</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-mg66-mrh9-m8jx">GHSA-mg66-mrh9-m8jx: Denial of Service via connection exhaustion in applications using Cache Components</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv">GHSA-492v-c6pp-mqqv: Middleware / Proxy bypass through dynamic route parameter injection</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r">GHSA-c4j6-fc7j-m34r: Server-side request forgery in applications using WebSocket upgrades</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-36qx-fr4f-26g5">GHSA-36qx-fr4f-26g5: Middleware / Proxy bypass in Pages Router applications using i18n</a></li>
</ul>
<p>Moderate:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-ffhc-5mcf-pf4q">GHSA-ffhc-5mcf-pf4q: Cross-site scripting in App Router applications using CSP nonces</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-gx5p-jg67-6x7h">GHSA-gx5p-jg67-6x7h: Cross-site scripting in beforeInteractive scripts with untrusted input</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-h64f-5h5j-jqjh">GHSA-h64f-5h5j-jqjh: Denial of Service in the Image Optimization API</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-wfc6-r584-vfw7">GHSA-wfc6-r584-vfw7: Cache poisoning in React Server Component responses</a></li>
</ul>
<p>Low:</p>
<ul>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-vfv6-92ff-j949">GHSA-vfv6-92ff-j949: Cache poisoning via collisions in React Server Component cache-busting</a></li>
<li><a href="https://github.com/vercel/next.js/security/advisories/GHSA-3g8h-86w9-wvmq">GHSA-3g8h-86w9-wvmq: Middleware / Proxy redirects can be cache-poisoned</a></li>
</ul>
<h2>v16.2.4</h2>
<blockquote>
<p>[!NOTE]
This release is backporting bug fixes. It does <strong>not</strong> include all pending features/changes on canary.</p>
</blockquote>
<h3>Core Changes</h3>
<ul>
<li>chore: Bump reqwest to 0.13.2 (Fixes Google Fonts with Turbopack for Windows on ARM64) (<a href="">#92713</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ee6e79b</code></a> v16.2.6</li>
<li><a href=""><code>afa053d</code></a> Turbopack: Match proxy matchers with webpack implementation (<a href="">#93594</a>)</li>
<li><a href=""><code>97a154e</code></a> Turbopack: Fix middleware matcher suffix (<a href="">#93590</a>)</li>
<li><a href=""><code>83899bc</code></a> [backport] Disable build caches for production/staging/force-preview deploys ...</li>
<li><a href=""><code>7b222b9</code></a> [backport][test] Pin package manager to patch versions (<a href="">#93595</a>)</li>
<li><a href=""><code>a8dc24f</code></a> [backport] Turbopack: more strict vergen setup (<a href="">#93587</a>)</li>
<li><a href=""><code>766148f</code></a> v16.2.5</li>
<li><a href=""><code>0dd9483</code></a> fix: add explicit checks for RSC header (<a href="">#83</a>) (<a href="">#98</a>)</li>
<li><a href=""><code>d166096</code></a> fix proxy matching for segment prefetch URLs (<a href="">#89</a>) (<a href="">#96</a>)</li>
<li><a href=""><code>9d50c0b</code></a> Strip next-resume header from incoming requests (<a href="">#92</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vercel/next.js/compare/v16.2.2...v16.2.6">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for next since your current version.</p>
</details>
<br />

Updates `next-intl` from 4.9.0 to 4.11.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/amannn/next-intl/releases">next-intl's releases</a>.</em></p>
<blockquote>
<h2>v4.11.1</h2>
<h2>4.11.1 (2026-05-08)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Avoid watchers for detached telemetry process (<a href="">#2319</a>) (<a href="">ff77a3d</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
<h2>v4.11.0</h2>
<h2>4.11.0 (2026-04-28)</h2>
<h3>Features</h3>
<ul>
<li>Add <code>displayName</code> to <code>useFormatter</code> (<a href="">#2285</a>) (<a href="">3666aa8</a>) – by <a href="https://github.com/roderickhsiao"><code>@​roderickhsiao</code></a></li>
</ul>
<h2>v4.10.1</h2>
<h2>4.10.1 (2026-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Set redirect domain if <code>x-forwarded-host</code> header exists (<a href="">#2281</a>) (<a href="">70d35db</a>) – by <a href="https://github.com/FourwingsY"><code>@​FourwingsY</code></a></li>
</ul>
<p>⚠️ If you're using a setup behind a reverse proxy and your proxy sets <code>x-forwarded-port</code>, make sure the value is correct (typically 443).</p>
<h2>v4.10.0</h2>
<h2>4.10.0 (2026-04-28)</h2>
<h3>Features</h3>
<ul>
<li>Add per-domain <code>localePrefix</code> override support (<a href="">#2273</a>) (<a href="">3e9febf</a>) – by <a href="https://github.com/frankmatheron"><code>@​frankmatheron</code></a></li>
</ul>
<h2>v4.9.2</h2>
<h2>4.9.2 (2026-04-27)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Prototype safety guards for <code>precompile: true</code> (<a href="">#2307</a>) (<a href="">c0bf0ee</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
<h2>v4.9.1</h2>
<h2>4.9.1 (2026-04-10)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Improve middleware pathname validation (<a href="">#2304</a>) (<a href="">1c80b66</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/amannn/next-intl/blob/main/CHANGELOG.md">next-intl's changelog</a>.</em></p>
<blockquote>
<h2>4.11.1 (2026-05-08)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Avoid watchers for detached telemetry process (<a href="">#2319</a>) (<a href="">ff77a3d</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
<h2>4.11.0 (2026-04-28)</h2>
<h3>Features</h3>
<ul>
<li>Add <code>displayName</code> to <code>useFormatter</code> (<a href="">#2285</a>) (<a href="">3666aa8</a>) – by <a href="https://github.com/roderickhsiao"><code>@​roderickhsiao</code></a></li>
</ul>
<h2>4.10.1 (2026-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Set redirect domain if <code>x-forwarded-host</code> header exists (<a href="">#2281</a>) (<a href="">70d35db</a>) – by <a href="https://github.com/FourwingsY"><code>@​FourwingsY</code></a></li>
</ul>
<h2>4.10.0 (2026-04-28)</h2>
<h3>Features</h3>
<ul>
<li>Add per-domain <code>localePrefix</code> override support (<a href="">#2273</a>) (<a href="">3e9febf</a>) – by <a href="https://github.com/frankmatheron"><code>@​frankmatheron</code></a></li>
</ul>
<h2>4.9.2 (2026-04-27)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Prototype safety guards for <code>precompile: true</code> (<a href="">#2307</a>) (<a href="">c0bf0ee</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
<h2>4.9.1 (2026-04-10)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Improve middleware pathname validation (<a href="">#2304</a>) (<a href="">1c80b66</a>) – by <a href="https://github.com/amannn"><code>@​amannn</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a6a8f8f</code></a> v4.11.1</li>
<li><a href=""><code>ff77a3d</code></a> fix: Avoid watchers for detached telemetry process (<a href="">#2319</a>)</li>
<li><a href=""><code>02989b6</code></a> test: Refactor extractor tests to e2e (<a href="">#2312</a>)</li>
<li><a href=""><code>e68a591</code></a> v4.11.0</li>
<li><a href=""><code>3666aa8</code></a> feat: Add <code>displayName</code> to <code>useFormatter</code> (<a href="">#2285</a>)</li>
<li><a href=""><code>11d9ce8</code></a> v4.10.1</li>
<li><a href=""><code>70d35db</code></a> fix: Set redirect domain if <code>x-forwarded-host</code> header exists (<a href="">#2281</a>)</li>
<li><a href=""><code>d4648b8</code></a> v4.10.0</li>
<li><a href=""><code>3e9febf</code></a> feat: Add per-domain <code>localePrefix</code> override support (<a href="">#2273</a>)</li>
<li><a href=""><code>e1b1825</code></a> v4.9.2</li>
<li>Additional commits viewable in <a href="https://github.com/amannn/next-intl/compare/v4.9.0...v4.11.1">compare view</a></li>
</ul>
</details>
<br />

Updates `react` from 19.2.4 to 19.2.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/releases">react's releases</a>.</em></p>
<blockquote>
<h2>19.2.6 (May 6th, 2026)</h2>
<h2>React Server Components</h2>
<ul>
<li>Type hardening and performance improvements
(<a href="">#36425</a> by <a href="https://github.com/eps1lon"><code>@​eps1lon</code></a> and <a href="https://github.com/unstubbable"><code>@​unstubbable</code></a>)</li>
</ul>
<h2>19.2.5 (April 8th, 2026)</h2>
<h2>React Server Components</h2>
<ul>
<li>Add more cycle protections (<a href="">#36236</a> by <a href="https://github.com/eps1lon"><code>@​eps1lon</code></a> and <a href="https://github.com/unstubbable"><code>@​unstubbable</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eaf3e95</code></a> Version 19.2.6</li>
<li><a href=""><code>23f4f9f</code></a> 19.2.5</li>
<li>See full diff in <a href="https://github.com/facebook/react/commits/v19.2.6/packages/react">compare view</a></li>
</ul>
</details>
<br />

Updates `react-dom` from 19.2.4 to 19.2.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/releases">react-dom's releases</a>.</em></p>
<blockquote>
<h2>19.2.6 (May 6th, 2026)</h2>
<h2>React Server Components</h2>
<ul>
<li>Type hardening and performance improvements
(<a href="">#36425</a> by <a href="https://github.com/eps1lon"><code>@​eps1lon</code></a> and <a href="https://github.com/unstubbable"><code>@​unstubbable</code></a>)</li>
</ul>
<h2>19.2.5 (April 8th, 2026)</h2>
<h2>React Server Components</h2>
<ul>
<li>Add more cycle protections (<a href="">#36236</a> by <a href="https://github.com/eps1lon"><code>@​eps1lon</code></a> and <a href="https://github.com/unstubbable"><code>@​unstubbable</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eaf3e95</code></a> Version 19.2.6</li>
<li><a href=""><code>23f4f9f</code></a> 19.2.5</li>
<li>See full diff in <a href="https://github.com/facebook/react/commits/v19.2.6/packages/react-dom">compare view</a></li>
</ul>
</details>
<br />

Updates `react-resizable-panels` from 4.8.0 to 4.11.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/bvaughn/react-resizable-panels/releases">react-resizable-panels's releases</a>.</em></p>
<blockquote>
<h2>4.9.0</h2>
<ul>
<li><a href="">702</a>: Add <code>disableDoubleClick</code> prop to <code>Separator</code> to enable turning <em>off</em> the double-click size reset behavior.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/bvaughn/react-resizable-panels/blob/main/CHANGELOG.md">react-resizable-panels's changelog</a>.</em></p>
<blockquote>
<h2>4.11.0</h2>
<ul>
<li><a href="">712</a>: <code>Separator</code> supports <code>:focus-visible</code> pseudo-class</li>
<li><a href="">703</a>: Fix: edge case scenarios when collapsing the last panel</li>
<li><a href="">711</a>: Improve legacy browser support wrt global stylesheets</li>
</ul>
<h2>4.10.0</h2>
<ul>
<li><a href="">705</a>: Add <code>data-separator=&quot;focus&quot;</code> state for <code>Separator</code> elements for more consistent custom CSS styles.</li>
</ul>
<h2>4.9.0</h2>
<ul>
<li><a href="">702</a>: Add <code>disableDoubleClick</code> prop to <code>Separator</code> to enable turning <em>off</em> the double-click size reset behavior.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>85714d9</code></a> 4.11.0</li>
<li><a href=""><code>640b88d</code></a> Fix typo on Min/max sizes doc page (<a href="">#710</a>)</li>
<li><a href=""><code>e434898</code></a> Upgrade react-lib-tools to improve site-search</li>
<li><a href=""><code>ab61ee9</code></a> Upgrade react-lib-tools to improve site-search</li>
<li><a href=""><code>5985041</code></a> Update overflow style example</li>
<li><a href=""><code>fa27133</code></a> 4.9.0 -&gt; 4.10.0</li>
<li><a href=""><code>b58ed97</code></a> Add data-separator &quot;focus&quot; state (<a href="">#706</a>)</li>
<li><a href=""><code>f4e5e08</code></a> Upgrade react-lib-tools to improve site-search</li>
<li><a href=""><code>5cf89ea</code></a> Made callouts on Common Questions more consistent</li>
<li><a href=""><code>435f953</code></a> Upgrade react-lib-tools to improve site-search</li>
<li>Additional commits viewable in <a href="https://github.com/bvaughn/react-resizable-panels/compare/4.8.0...4.11.0">compare view</a></li>
</ul>
</details>
<br />

Updates `tailwind-merge` from 3.5.0 to 3.6.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/dcastil/tailwind-merge/releases">tailwind-merge's releases</a>.</em></p>
<blockquote>
<h2>v3.6.0</h2>
<h3>New Features</h3>
<ul>
<li>Add support for Tailwind CSS v4.3 by <a href="https://github.com/dcastil"><code>@​dcastil</code></a> in <a href="">dcastil/tailwind-merge#677</a>
<ul>
<li>Add <code>postfixLookupClassGroups</code> option to config to support Tailwind utilities where a slash is part of the full class name, like named container queries</li>
</ul>
</li>
<li>Add support for readonly array values by <a href="https://github.com/unional"><code>@​unional</code></a> in <a href="">dcastil/tailwind-merge#652</a></li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix broken links in README by <a href="https://github.com/maurer2"><code>@​maurer2</code></a> in <a href="">dcastil/tailwind-merge#662</a></li>
</ul>
<h3>Other</h3>
<ul>
<li>Harden internal CI pipeline security by omitting git checkout by <a href="https://github.com/dcastil"><code>@​dcastil</code></a>, suggested by <a href="https://github.com/kyletaylored"><code>@​kyletaylored</code></a> in <a href=""></a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/dcastil/tailwind-merge/compare/v3.5.0...v3.6.0">https://github.com/dcastil/tailwind-merge/compare/v3.5.0...v3.6.0</a></p>
<p>Thanks to <a href="https://github.com/brandonmcconnell"><code>@​brandonmcconnell</code></a>, <a href="https://github.com/manavm1990"><code>@​manavm1990</code></a>, <a href="https://github.com/langy"><code>@​langy</code></a>, <a href="https://github.com/roboflow"><code>@​roboflow</code></a>, <a href="https://github.com/syntaxfm"><code>@​syntaxfm</code></a>, <a href="https://github.com/getsentry"><code>@​getsentry</code></a>, <a href="https://github.com/codecov"><code>@​codecov</code></a>, a private sponsor, <a href="https://github.com/block"><code>@​block</code></a>, <a href="https://github.com/openclaw"><code>@​op...

_Description has been truncated_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93be8dc924c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.