# Issue

**Title:** perf(ferrox): SIMD128 (wasm) + chunked rayon (native) bond-detection kernel — native 20.9→4.0ms

## Description

ferrox #4。27³=19683 原子基准(22 核,min-of-5):

| 场景 | 前 | 后 | 加速 |
|---|---|---|---|
| native rayon TTT / FFF | 20.9 / 20.6 | **4.0 / 4.0** | 5.2× |
| native 串行 TTT / FFF | 34.3 / 30.1 | 12.9 / 8.8 | 2.7× / 3.4× |
| wasm typed 全链 TTT / FFF | 40.7 / 34.7 | **14.9 / 10.4** | 2.7× / 3.3× |

- CellList 改 CSR + bin 排序 SoA;内层循环 zip 迭代消边界检查;`scan_bin_hits` 提取
- wasm `+simd128` 默认开(.cargo/config.toml 全入口覆盖)+ `--no-simd`/`CATGO_WASM_NO_SIMD=1` 逃生 flag;`wasm-tools print` 证据:+simd 构建 1486 条 f64x2/v128 指令,no-simd 0 条;诚实标注:本负载下 SIMD 计时差在噪声内(收紧 cutoff 后每 bin ~2.5 原子吃不饱两 lane),wasm 2.7× 主要来自 CSR/SoA 重构 + cutoff 收紧(`min(max_bond_dist, 2·r_max·scale)`,数学可证结果不变)
- rayon 原子区段分块 + 按块序归并,**键表顺序与串行逐字节一致**(确定性);feature-gated,wasm 不开
- wasm 线程(SharedArrayBuffer)可行性报告:不建议现在做(COOP/COEP × Tauri WebKitGTK 未验 + nightly build-std;核已 ~10ms/帧,收益在 100k+ 原子档)
- cargo test 1062 全绿(默认与 --no-default-features);clippy 零新增;键数逐例一致
- 风险:老 WebKitGTK(<2.40)不支持 wasm SIMD → 打包老发行版用 --no-simd;用户自设 RUSTFLAGS 会静默覆盖

⚠️ 合并后需 `node scripts/build-wasm.mjs` 重建本地 pkg(IF_MISSING 短路不会自动重建)。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70eeec8f9d35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.