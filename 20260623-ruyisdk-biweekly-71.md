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

### LLVM

- [RISCV][LLVM][Clang] Add experimental Zvvm config intrinsics
https://github.com/llvm/llvm-project/pull/203774
添加 Zvvm config 相关 intrinsics 支持
正在 review

- [RISCV][P-ext] Merge paired pli/plui in RISCVMoveMerger
https://github.com/llvm/llvm-project/pull/202566
在 RISCVMoveMerger 里合并成对的 pli/plui 指令到 pli.d*/plui.d*
已合并

- [Clang][RISCV] packed comparison intrinsics
https://github.com/llvm/llvm-project/pull/203191
添加 P 拓展向量比较相关 intrinsic 支持。包括 pmseq/pmsne/pmslt[u]/pmsgt[u]/pmsge[u]/pmsle[u]
已合并

- [RISCV][P-ext] packed exchanged add/sub codegen
https://github.com/llvm/llvm-project/pull/203473
添加  packed exchanged add/sub 的 codegen 支持
正在 review

- [RISCV][P-ext] Support Packed Averaging Addition and Subtraction
添加Packed Averaging Add/Sub 的 intrinsic 支持
已合并

- [RISCV][P-ext] Support Packed Absolute Value and Absolute Difference
添加 Packed Absolute Value and Absolute Difference 的 intrinsic 支持
已合并

### V8

### OpenJDK

### Go

### QEMU模拟器