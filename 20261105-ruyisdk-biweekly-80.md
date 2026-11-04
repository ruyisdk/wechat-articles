# RuyiSDK 双周进展汇报 第 080 期 · 2026 年 11 月 05 日

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
  - 移植了 sinpif, sqrt, sqrtf, tanf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 atanhf, atan2f, atanpif, atan2pif, exp2f, cosf, coshf, cospif, exp10f, expf, log2f, log2p1f, rsqrtf, expm1f 至现有的 newlib 向量数学框架。


### GCC

### LLVM

本期提交 PR 如下

- [RISCV][P-ext] Combine more pmadd to pmadda
  https://github.com/llvm/llvm-project/pull/235306
  扩展打包水平乘加的累加模式匹配，将更多 `pm*add*` 与后续加法合并为 `pm*adda*` 等指令，并完善 RV32/RV64 指令选择。已合并
- [RISCV][P-ext] Improve codegen for funnel shifts
  https://github.com/llvm/llvm-project/pull/235245
  改进 RV32 上 64 位 funnel shift 的代码生成，通过 32 位操作与合并指令消除分支，减少最坏情况下的动态指令数。已合并
- [RISCV][P-ext] Support Packed Multiplication with Widening Horizontal Addition and Accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/234450
  为 RISC-V P 扩展新增带扩宽水平加法的打包乘累加 intrinsics，并实现相应代码生成支持。已合并
- [RISCV][GlobalISel] Improve narrow ctlz_zero_poison lowering for XTHeadBb
  https://github.com/llvm/llvm-project/pull/237815
  在 XTHeadBb 下先扩宽窄类型 `G_CTLZ_ZERO_POISON` 再 lowering，以左移替代零扩展和减法，改进前导零计数的代码生成。已合并
- [RISCV][GlobalISel] Widen narrow G_CTTZ before lowering for XTHeadBb
  https://github.com/llvm/llvm-project/pull/238214
  在 XTHeadBb 下先将窄类型 `G_CTTZ` 和 `G_CTTZ_ZERO_POISON` 扩宽至 XLEN，再通过 `G_CTLZ` 进行 lowering，选择 `th.ff1` 指令，避免回退到基于 popcount 的展开。已合并
- [Clang][RISCV] Add packed byte horizontal multiply-accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/234484
  新增 RISC-V P 扩展的打包字节水平乘累加 intrinsics，支持有符号、无符号及混合符号三种形式。已合并

RuyiSDK LLVM 分支进展：

- [RISCV] Add initial Ztt matrix extension support based on spec v0.6 and intrinsic doc v0.6
  https://github.com/ruyisdk/llvm-project/pull/169
  基于 Ztt 规范与 intrinsics 文档 v0.6，初步支持 RV32/RV64 矩阵扩展，涵盖汇编/反汇编、Clang 类型与 intrinsics、LLVM IR 和代码生成，以及 M/ACC 寄存器分配、拷贝与溢出处理。已合并
- Add AME CI
  https://github.com/ruyisdk/llvm-project/pull/170
  为 AME 分支新增 GitHub Actions CI，自动构建 RISC-V 目标的 LLVM/Clang，并运行 RISC-V CodeGen、汇编及语义测试。已合并（补记）

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
