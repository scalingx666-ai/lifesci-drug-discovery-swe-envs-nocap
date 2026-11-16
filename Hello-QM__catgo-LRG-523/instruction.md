# Issue

**Title:** fix(trajectory): web版轨迹打不开 — binary .traj reads + indexed client parse for all formats (+idle warmup)

## Description

Round 3 前半(网页版轨迹修复,用户生产实测撞上;GPU 键变换另开 PR)。

**app.catgo-ucsd.org(纯静态,无后端流式)上轨迹"打不开"的三层根因,全修**:

1. **`decompress_file` 把所有未压缩文件 `readAsText`** → ASE .traj 二进制乱码,全部文本解析器拒收("Unsupported text format"= 直接失败)。修:二进制结构格式(.traj/.h5/.hdf5)读/解压为 ArrayBuffer;文本调用方(XRD、merge)显式收窄。
2. **`ingest_one` 走急切 `parse_trajectory_data`** → 全帧 site 对象一次性构建。修:改 `parse_trajectory_async`(索引路由 + 4 急载帧 + 延迟 plot metadata,#522 的秒开刀在此路径生效)。
3. **索引阈值 50MB 太高**:.traj 的 ulm 头自带全帧 offset 表(索引零成本)→ 任意大小一律索引;文本 .xyz/.extxyz 阈值降到 2MB(索引=一次边界扫描,严格优于急切)。

**实测(node,真实文件)**:
| 文件 | 修前 | 修后 |
|---|---|---|
| 48MB .traj(100 帧 20k 原子) | 浏览器 >30s 卡死 / 静态部署直接失败 | **63ms** |
| 35MB .extxyz(1020 帧) | 数十秒主线程卡死 | **14ms** |
| 315MB .xyz(5000 帧) | 分钟级/看似打不开 | **98ms** |

附带:二进制载荷只解码头 64KB 做嗅探;raw_traj_b64(HPC 回推副本)加 8MB 上限(48MB 文件曾在打开时同步构建 ~64MB base64 串);**idle 预热**(加载后空闲时预转换全帧位置,首圈播放 6.6→20fps 的差距来源)。

vitest 4522 全绿;svelte-check 0 err。**注意:app.catgo-ucsd.org 要等合并后 deploy-cloudflare 跑完才生效。**

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a79aaef44d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.