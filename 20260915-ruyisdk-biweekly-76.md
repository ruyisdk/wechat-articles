# RuyiSDK 双周进展汇报 第 076 期 · 2026 年 09 月 15 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 log10, log10f, log10p1, log10p1f, log1p, log1pf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 atan2pi, exp2, cbrt, cospi, exp10, log2p1 至现有的 newlib 向量数学框架。

### GCC

### LLVM

本期提交 PR 如下

- [RISCV][SLP] Use common alignment when checking constant-stride loads
  https://github.com/llvm/llvm-project/pull/222520
  修复 SLP 常量步长加载合法性检查中的对齐判断，使用 `CommonAlignment`，避免将 32 位加载扩宽为未对齐的 64 位 RVV 访问而触发 `SIGBUS`。已合并
- [RISCV][SLP] Precommit strided-load alignment tests (NFC)
  https://github.com/llvm/llvm-project/pull/222863
  补充 RV32/RV64 下 SLP 步长加载对齐测试，覆盖相邻加载组对齐不同及严格对齐场景，为后续合法性修复提供回归测试。已合并
- [RISCV] Support Packed Multiplication with Horizontal Addition
  https://github.com/llvm/llvm-project/pull/218430
  实现 packed multiplication with horizontal addition 的 Clang、LLVM intrinsic、后端选择及 RV32/RV64 测试。上期正在 review，本期已合并
- [InstCombine] Fold `uitofp nneg` comparisons above the signed maximum
  https://github.com/llvm/llvm-project/pull/221118
  在浮点比较折叠中将 `uitofp nneg` 的上界收紧为有符号整数最大值，简化超出其有效范围的比较。正在 review

### V8

### OpenJDK

### Go

### QEMU

## 社区动态


---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
