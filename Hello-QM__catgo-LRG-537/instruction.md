# Issue

**Title:** fix(render): trajectory packet-path material styles (#533) + per-frame GL buffer churn

## Description

## 中文摘要

修复 #533(轨迹态 Material 选择器失效)与 #534(dump.traj 播放逐帧延迟)——两者同属 packet/replica GPU 管线,基于 `feat/impostor-bond-mvp` @ f79c1e33,两个原子提交:

- `74ffbbcc` **perf(render): capacity-stable bond replica attributes**(#534)
- `b247708a` **fix(render): honor Appearance → Material on the packet/replica path**(#533)

**定性:功能修复完成,软件层回归全部通过;仅保留一项硬件性能复验作为 merge 前 checklist(见文末)。**

---

## #534 归因(数据裁决,非推断)

**结论:回归不是 `886e23c9..8a3bed35` 窗口内某次提交引入的——它是 packet 路径自 `49e8546a`(接线进真实场景)起固有的逐帧 GPU buffer 翻建 + 泄漏。** 同机同负载 A/B(19,968 原子 × 100 帧合成 MD extxyz,页内 GL 调用计数器——精确计数,不受软件光栅速度影响):

| 树 | createBuffer/帧 | bufferData/帧 | bufferSubData/帧 | deleteBuffer/帧 | 位置纹理/帧 | 主线程忙时/帧 |
|---|---|---|---|---|---|---|
| main `fcb6b687`(23.8 fps 参照) | 0.9 | 0.9 次 / 1.33 MB | 0.5 次 / 0.33 MB | 0.5 | ~0 | 195 ms |
| Gate A `49e8546a`("流畅") | **4** | 4 次 / 2.95 MB | 8.8 次 / 10.45 MB | **0** | 1 × 328 KB | 6214 ms |
| 窗口尾 `8a3bed35`(被报卡顿) | **4** | 4 次 / 2.97 MB | 7.9 次 / 3.46 MB | **0** | 1 × 328 KB | 2704 ms |
| **本 PR `74ffbbcc`** | **0.1**(装载+一次增容) | 0.1 次 / 0.09 MB | 11.8 次(活跃前缀 ranged)/ 6.4 MB | 0 | 1 × 328 KB | 2407 ms |

注:窗口尾反而比 Gate A 快 ~2×(T5 关掉了 hitbox 重建)。"Gate A 流畅"是硬件短时吸收了翻建成本;**泄漏(每帧 4 个 GL buffer 从不 delete)随播放时长累积,越放越卡**——正是"逐帧延迟"的机制。

**根因:** MD 播放键数几乎每帧变化 → `BondReplicaRenderer.#rebuild_half_attrs` 每帧重分配 4 个 per-half 属性数组 → `ensure_instanced_attr` 每帧安装 4 个全新 `InstancedBufferAttribute` → 每帧 4×`createBuffer` + 4×全容量 `bufferData`(~3 MB)+ 整 VAO 重建 + 0×`deleteBuffer` + 全量重传。

**修复:** half 属性改为 grow-only 容量模型(×1.5 余量):活跃区间 `#half_count` 驱动 `instanceCount` 与 update ranges(只加不清,遵守 #532 的 draw 时消费契约);键数变化 = 稳定身份上的原地重写;容量增长(对数次摊销)才走 fresh-attribute 路径。

**五个嫌疑逐一裁决:** ① `49102db3` 守卫逐帧误触—否(capacity 比较播放中恒等,divisor 不变即 no-op);② 逐帧 packet 重建—部分成立,但慢的是渲染器的属性翻建而非 packet 对象;③ #532 ranges 互作—否(legacy mesh 未挂载不绘制);④ Bonds T6 逐帧重跑键检测—否(与 main 行为一致,帧连通性缓存在位);⑤ T5 ID-pass 泄入—否(播放窗口 `readPixels`=0,T5 反而砍半了逐帧成本)。

## #533 根因与修复

轨迹态 packet 路径的 `AtomReplicaRenderer` impostor shader 只有一套硬编码 Blinn-Phong,从不消费 `render_style`;实现样式的 legacy 材质在 packet 模式下不挂载 → Material 选择器整体失效。修复:legacy 的 `uRenderStyle` 四分支(glossy/metallic GGX+ACES、matte、toon 三段 cel、matcap)**逐字移植**进 replica shader;映射抽到共享模块 `atoms/render-style.ts`;`AtomManagerInstances` 把 `render_style`/`matcap_preset`/`highlight_strength` 透传 `WebGLReplicaLayer`,uniform 实时(共享 uniform 对象,主/ghost 同步;零重编译零换装)。键 impostor 与 legacy 键材质对齐(本就无样式分支,两路径一致)。

---

## 验证

### 单测 / 类型

- `tests/vitest/structure/gpu` **155 pass / 6 skipped**(+10 个新回归测试:容量契约 ×3、样式 shader/uniform ×3、组件级穿透 ×1、及配套)
- `tests/vitest/trajectory` **497 pass / 1 skipped**
- `pnpm check` **0 errors**(304 个既有 warning)
- 全量 vitest:**4920 pass / 2 fail** — 两个红项均有基线裁决,不阻塞(见下)

### Known test failures 基线裁决(非本 PR 回归)

| 用例 | 现象 | 裁决 |
|---|---|---|
| `cube/periodic-cube-lattice` › `find_pbc_images_fast preserves the lattice` | worker 5 s timeout | **baseline/environment failure**:在不含本 PR 的 `f79c1e33` 基线上同环境复现(5004 ms 同样超时);2026-07-17 已有同类记录 |
| `xrd/calc-xrd` › `compare XRD for mp-1204603.json` | 全量负载下偶发 | **test flake**:isolated run 30/30 通过 |

### 真实 UI 运行时验收(隔离静态前端,11/11 PASS)

1. 轨迹经真实 drop handler 加载,packet 路径自 1× 接管
2. 真实 interval Play 帧推进
3. **播放稳态窗口 `createBuffer = 0` / `deleteBuffer = 0`** —— 直接验证 #534 的修复机制本身(buffer 翻建与泄漏消除),而非仅"看起来不卡"
4. Play/Pause ×3 干净切换
5. 跳帧 5 → 末帧 → 5
6. **播放中**连切 5 种材质(toon/glossy/matcap/matte/flat)无崩溃
7. 暂停态 toon / matte / matcap / glossy 渲染两两可辨(#533 视觉证据)
8. XDATCAR 轨迹上经真实 CellSelect 走 **1×→2x2x2→1×** 因子循环:状态标签正确、8 复制体 + 晶胞框 + 边界键渲染正确、循环后播放正常
9. image atoms(ghost-images 策略)开关正常
10. 活跃 WebGL context 健康:`isContextLost()=false`、`getError()=0`(两个 lost context 均属已卸载的孤儿画布——launcher 预览等,浏览器正常回收)
11. 全程零非预期 page/console error

### 测量方法说明

本机为 WSL2 headless Chromium(SwiftShader 软件光栅),绝对 fps 无意义;所有结论基于**精确的 GL 调用/字节计数**与同机 A/B。真实 `dump.traj` 在报告机器上,测量用等价合成负载(同 19,968 原子 × 100 帧、47 MB、键数逐帧涨落、~55k half ≥ 真实 ~52k,结论偏保守)。

---

## Merge 前 checklist

- [ ] **Hardware-only performance verification pending**:原版 `dump.traj` @ :3300 真实 GPU,真实 interval Play 回到 **≥20 fps 档**(#534 验收)。correctness / 资源生命周期 / WebGL 健康已在本 PR 内验证完毕,此项仅验证真实硬件绝对吞吐。

## 相关

- ;(两者均阻塞 #531 的 merge gate)
- 验收排查中发现并另行立案:#536(索引式 xyz/extxyz 加载丢失 Lattice,>2 MB 文件;不同故障域,不入本 PR)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f79c1e332e5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.