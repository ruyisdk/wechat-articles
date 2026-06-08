# RuyiSDK 双周进展汇报 第 070 期·2026 年 06 月 09 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC

### LLVM

- [RISCV][MC] Support experimental Zvdota Family instructions
https://github.com/llvm/llvm-project/pull/195069 已合并

- [RISCV][P-ext] Split v4i16/v8i8 MUL on RV32.
https://github.com/llvm/llvm-project/pull/199504
在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的乘法（按寄存器对拆成两半计算）。
已合并

- [RISCV][P-ext] Fold bitcast of v4i8/v2i16 const splat to scalar on RV64
https://github.com/llvm/llvm-project/pull/199513
在 RV64 上把 v4i8/v2i16 常量 splat 的 bitcast 折叠为标量常量。

- [RISCV][P-ext] Split v4i16/v8i8 INSERT/EXTRACT_VECTOR_ELT on RV32.
https://github.com/llvm/llvm-project/pull/199917
在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的元素插入/提取（INSERT/EXTRACT_VECTOR_ELT）。

- [RISCV][P-ext] packed shift-add codegen
https://github.com/llvm/llvm-project/pull/201294
实现 P 扩展 packed shift-add codegen。

- [RISCV][P-ext] Select scalar asub/asubu and mulhr/mulhru/mulhrsu on RV32
https://github.com/llvm/llvm-project/pull/201540
在 RV32 上为标量 asub/asubu 与 mulhr/mulhru/mulhrsu 指令添加指令选择。

- Fix RV32 instruction sequence for exchanged add/sub i32x2 intrinsics
https://github.com/riscv/riscv-p-spec/pull/293
修正 i32x2 交换式加减（p*_x 系列 intrinsic） intrinsic 文档中的 RV32 指令序列。

- RV32 fallback: scalar instructions for 64-bit packed multiply intrinsics
https://github.com/riscv/riscv-p-spec/pull/295
把 64-bit packed multiply intrinsic 在 RV32 上回退改为正确的标量 .h 指令

- RV32 fallback: widening wmul/wmacc for 64-bit multiply-parts intrinsics
https://github.com/riscv/riscv-p-spec/pull/296
把返回 int64 的 multiply-parts intrinsic 在 RV32 上回退改为单条加宽指令 wmul/wmacc

- Fix typos in 64-bit Q-format multiply-accumulate intrinsics
https://github.com/riscv/riscv-p-spec/pull/297
修正 64 位 Q-format 乘累加 intrinsic 的 typo



### V8

### OpenJDK

### Go

### 模拟器QEMU
