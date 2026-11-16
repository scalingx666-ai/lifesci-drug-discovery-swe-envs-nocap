# Issue

**Title:** feat(render-still): path-traced publication stills — three-gpu-pathtracer 'Render Still' mode

## Description

OVITO pro 级离线光追出图(渲染质量线,spike 验证后落地)。I/O 面板 → Export → Figure → "Path-traced render…"。

- `src/lib/render-still/`:SoA→merged geometry 烘焙(球+半键,b_eff 跨胞约定与实时渲染器一致)、CPU ACES+sRGB 读回(float RT,绕 drawingBuffer clamp)、能力探测(WebGL2+EXT_color_buffer_float,SwiftShader 警告)、RenderStillSession(offscreen renderer、CENTER BVH maxLeafSize 8、rAF 采样、进度/取消/随时保存)
- 对话框:分辨率预设/samples/bounces/质量档,渐进预览
- i18n en/zh 31 键对齐;+20 单测(bake/tonemap)
- 实测(RTX 4060):demo 分子 200×200@32spp 冷 11.8s(含 shader 编译)/热 3.0s,PNG 落盘验证非空;spike 数据:20k 原子 1080p 出版级 500spp ≈ 5.5min
- 抓到的库坑:generator 默认 `maxLeafTris:1` 会经弃用 shim 覆盖 `maxLeafSize:8`,已压掉

v1 范围:原子+实心键(PBC image 原子/氢键/芳香环/多面体/晶格线暂不进 still);WebKitGTK 只探测降级未实测;详见 commit。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70eeec8f9d35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.