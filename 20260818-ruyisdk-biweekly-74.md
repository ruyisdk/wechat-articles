# RuyiSDK 双周进展汇报 第 074 期·2026 年 08 月 18 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- venv & UX: 解决进入虚拟环境向导时的性能问题。
- UX: 整理程序各处的文本以统一命名风格。
- venv: 修改虚拟环境向导的部分设计，使线程间数据流向清晰。

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC

### LLVM

本期提交 PR 如下

- [RISCV][P-ext] Support Packed Narrowing Clip Pair
 https://github.com/llvm/llvm-project/pull/215779
 补齐 P 扩展 Packed Narrowing Clip Pair，覆盖 Clang、LLVM IR、RISC-V 后端选择及 RV32/RV64 测试。已合并

- [Clang][RISCV] Add packed sign and zero extend intrinsics
 https://github.com/llvm/llvm-project/pull/211487
 增加 packed sign/zero extend（psext/pzext）的 Clang 内建函数、头文件封装及代码生成测试。已合并

- [RISCV][P-ext] Select scalar mulhr/mulhru/mulhrsu for RV32 v2i32
 https://github.com/llvm/llvm-project/pull/215938
 修复 RV32 v2i32 舍入高位乘法选择，将运算拆分为 mulhr、mulhru、mulhrsu 标量指令。已合并

- [RISCV][P-ext] Support Packed Multiply High
 https://github.com/llvm/llvm-project/pull/211223
 增加 P 扩展 Packed Multiply High 的 Clang 内建函数、LLVM IR 和代码生成支持，覆盖 RV32/RV64。已合并

- [RISCV][MC] Add experimental Smcsps and Sscsps support
 https://github.com/llvm/llvm-project/pull/211712
 增加 Smcsps 和 Sscsps 拓展的汇编支持。已合并


### V8

### OpenJDK

### Go

### QEMU模拟器
