# RuyiSDK 双周进展汇报 第 073 期·2026 年 07 月 21 日

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

本期提交 PR 如下：

1. [Clang][RISCV][P-ext] Support packed widening convert intrinsics
https://github.com/llvm/llvm-project/pull/208394
添加 packed widening convert intrinsics 支持
已合并

2. [RISCV] Add packed narrowing convert intrinsics
https://github.com/llvm/llvm-project/pull/210389
添加 packed narrowing convert intrinsics 支持
已合并

3. [RISCV][P-ext] Support packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207574
支持 packed reverse intrinsics
已合并

4. [RISCV][P-ext] Improve codegen for packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207575
优化 packed reverse intrinsics codegen
已合并

5. [RISCV][P-ext] Add codegen for packed absolute difference sum
https://github.com/llvm/llvm-project/pull/207314
添加 packed absolute difference sum codegen 支持
已合并

6. [RISCV][P-ext] Fold packed insert-into-zero to zero-extend
https://github.com/llvm/llvm-project/pull/208006
将特定的 32-bit packed vector 插入零向量操作折叠为 `zext`
已合并

7. [RISCV][P-ext] Add packed saturating rounding shift codegen
https://github.com/llvm/llvm-project/pull/208630
添加 packed saturating rounding shift codegen 支持
已合并

8. [RISCV][P-ext] Improve RV64 v2i16 reverse codegen
https://github.com/llvm/llvm-project/pull/208664
优化 RV64 上 v2i16 reverse codegen
已合并

9. [Clang][RISCV] Add P extension reinterpret cast intrinsics
https://github.com/llvm/llvm-project/pull/210241
添加 P 扩展 reinterpret cast intrinsics
已合并

10. [RISCV][P-ext] Support Packed Saturating Absolute Value.
https://github.com/llvm/llvm-project/pull/207978
添加 Packed Saturating Absolute Value intrinsic 支持
已合并

11. [RISCV][P-ext] Support Packed Narrowing Zip
https://github.com/llvm/llvm-project/pull/210040
添加 Packed Narrowing Zip intrinsic 支持
已合并

12. [Clang][P-ext] Support packed zip/unzip intrinsics
https://github.com/llvm/llvm-project/pull/208245
添加 packed zip/unzip intrinsics 支持
已合并

13. [RISCV][P-ext] Improve the codegen for pzip
https://github.com/llvm/llvm-project/pull/208479
优化 pzip codegen
已合并

14. [RISCV][P-ext] Improve the codegen for unzip-like shuffle and buildvector
https://github.com/llvm/llvm-project/pull/208763
优化特定 unzip 类 shuffle 和 buildvector 代码生成
已合并

15. [RISCV][P-ext] Generalize lowerVECTOR_SHUFFLEAsRV32PNarrowingShift
https://github.com/llvm/llvm-project/pull/210522
泛化 `lowerVECTOR_SHUFFLEAsRV32PNarrowingShift`
已合并

16. [InstCombine] Treat `uitofp nneg` as non-negative signed range for fcmp clamp folds
https://github.com/llvm/llvm-project/pull/208234
让 InstCombine 将 `uitofp nneg` 的输入按非负有符号整数范围处理，从而折叠 `fcmp` 钳位及端点比较
正在 review

17. [ValueTracking][InstCombine] Preserve samesign when flipping icmp strictness
https://github.com/llvm/llvm-project/pull/209097
在将非严格整数比较规范化为严格比较时保留 `samesign` 标志，同时避免常量调整跨越溢出或符号边界
正在 review

18. [InstCombine] Use samesign constraints in unsigned known-bits folds
https://github.com/llvm/llvm-project/pull/209675
在无符号比较的 known-bits 折叠中传播 `samesign` 的符号位约束，从而支持更多整数范围端点折叠
正在 review

19. [RISCV][P-ext] Add packed sign and zero extend intrinsics
https://github.com/llvm/llvm-project/pull/208685
添加 packed sign and zero extend intrinsics
正在 review

### V8

### OpenJDK

### Go

### QEMU模拟器
