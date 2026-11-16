# Issue

**Title:** feat: normalize drug aliases at query entry

## Description

- 支持药物标准名和常见别名输入
- 同一药物的标准名/别名尽量归到同一个 canonical drug
- 在固定 mode + resource_filter 下结果高度一致
- 标准化失败不导致系统崩溃


### In Scope

- 药物标准名输入，如 `imatinib`
- 常见别名 / 品牌名输入，如 `Gleevec`
- 大小写、空格、简单符号噪声处理
- 高置信 typo 修正，如 `imatanib -> imatinib`
- 输入标准化结果写入执行链路和 query 日志
- 自动化测试与人工回归测试

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fc110652bf9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.