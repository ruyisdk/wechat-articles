# RuyiSDK 双周进展汇报 第 071 期·2026 年 06 月 23 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC

- 添加 RISC-V Profiles 支持到工具链 --with-arch 选项，用于构建默认支持特定 profile 的工具链，已提 PR 至 riscv-gnu-toolchain 仓库：

  https://github.com/riscv-collab/riscv-gnu-toolchain/pull/1869
  
- 提交了 Zvzip 与 Zvdota/Zvbdota 等 RISC-V 草案扩展的 GNU 工具链支持实现。其中，Zvzip 主要面向向量数据重排、打包/解包等场景；Zvdota/Zvbdota 面向点积与批量点积运算，可支撑 AI 推理/训练、DSP、GEMM/Conv 等核心算子的性能优化。

  - zvzip: https://patchwork.sourceware.org/project/gcc/list/?series=62161&archive=both
  - zvdota: https://github.com/ruyisdk/riscv-gcc/tree/zvdota
  - 相关介绍：https://github.com/pz9115/riscv-toolchain-notes/blob/main/talks/2026-riscv-zvdota-zvbdota-introduction/README.md

- 完成并提交 Ziccid 扩展的工具链基础支持，包括扩展识别、依赖解析和架构属性传播:

  https://github.com/ruyisdk/riscv-gcc/tree/ziccid

- 协助 compiler-explorer 社区完善了 Binutils 的 trunk 分支，适配了 RVA23 Profile 支持。

  - https://github.com/compiler-explorer/compiler-explorer/pull/8827
  - 示例：https://godbolt.org/z/h49rYT3To

- 协助 RISE-Developer-Infrastructure 工作组开始进行工具链 CI 模块的维护更新，更新了 GCC CI 模块，添加了 gcc-16 CI 部分，移除了 gcc-14 的相关检测

  https://github.com/riseproject-dev/gcc-postcommit-ci/pull/1
  
### LLVM

### V8

### OpenJDK

### Go

### QEMU模拟器
