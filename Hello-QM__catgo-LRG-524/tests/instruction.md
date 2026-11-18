# Issue

**Title:** perf(bonds): GPU vertex-shader transforms for trajectory playback — kill the 52k-instance CPU mat4 floor

## Description

Round 3 主菜。缓存圈 20fps 的地板 = 每帧 52k 实例 CPU 端 mat4 全量重算 + 3.3MB instanceMatrix 上传;本 PR 把键变换搬进顶点着色器(原子渲染的既有架构),CPU 每帧只剩 ~320KB 位置纹理上传。

### 方案
- **单 ShaderMaterial + `uGpuXform` uniform 分支**(非双材质互换):零重编译零 swap;attr 缺失时 WebGL 喂常量 0 无害
- **静态 per-instance attr**:`a_site` vec2 f32(24bit 索引)、`a_jimage` Int8×3、`a_half` Uint8(按奇偶容量期写死);**位置纹理** RGBA32F 宽 1024,texelFetch 按 site 索引取端点;`uLattice` 顶点内做 jimage 平移;len>uMaxBondLength 或非有限 → 零缩放(stale 过滤的 GPU 版)
- **激活条件 = typed-direct 播放期**(`gpu_transform_active={typed_direct_active}`);multibond / decorator 非空自动回落 CPU 路径(live 验证:6451 image atoms 时干净回落,关掉即回 GPU);零回归面
- 周期键 paired-stub 渲染补进 shader(uStubMode/uStubScale,对齐 #write_slot 周期分支)——默认 `hide_incomplete_bonds=false` 工况下 GPU 路径才有意义
- 附带:`build_image_atom_layout` 空布局早退(此前每帧白建 26k Map,CPU 基线同受益)
- `sync_gpu_topology()`:拓扑变化时一次全量 attr 写(矩阵不碰);出模式无条件 force_full_resync 重建矩阵;untrack 纪律全程(见 #519 的类字段 $state 隐式订阅坑)

### 实测(19968 原子 ×100 帧,48MB dump.traj)
| 口径 | fps |
|---|---|
| 本 PR 前基线(同会话) | 11.2 |
| CPU 路径(仅关 GPU 开关) | 16.4(layout 早退的功劳) |
| **GPU 路径** | **23.8 均值 / 峰值 30.2**(60Hz vsync 量化≈2 vsync/帧) |

键侧 CPU 归因(5s trace):conn→typed 0.5% + gpu sync 0.1% + tex 上传 ≈0 → **合计 0.6%**。剩余上限 = Svelte 图遍历 get 6.2% + effects 5.7% + GC 8.6% + 渲染管线(round 4 范畴)。

### 验证
- vitest **4529 全绿**(+7 新单测 gpu-topology-sync);svelte-check 0 err
- 几何:程序化(JS 镜像 shader 数学跑同一 GPU 绑定数据)多帧 26k 键 0 长键/0 NaN/0 越界;截图对比像素 diff 0.9%(圆柱边缘着色差,无缺键)
- 拾取:暂停尾同步重建 filtered_bond_pairs=25990 ✓,原子点选 ✓;**键的定点点击未直接演示**(CDP 中心射线在稠密体系总先撞原子;键 hitbox 代码路径零接触、数据供给已验证)

### 遗留
变胞轨迹 uLattice 用冻结晶格(与 CPU 路径同等既有局限);GPU attr 懒分配 ~12MB@1M 容量(与 color attr 同模式);stub 像素未单独放大对比。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc21ee90c692`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.