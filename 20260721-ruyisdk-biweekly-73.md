# RuyiSDK 双周进展汇报 第 073 期·2026 年 07 月 21 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- 项目: 发布 0.1.6 测试版。
- CI: 添加测试版交付流程。
- venv: 在所选工具链不包含 sysroot 时禁用相应的 sysroot 配置选项。
- venv: 调整向导配置页的布局。
- 添加问卷调查弹窗。

### 版本测试及遗留问题

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 strcasecmp、strcasecmp_l、strncasecmp 和 strncasecmp_l 的通用版本 RVV 优化。
  - 移植了 exp2m1 和 exp2m1f 至现有的 glibc libmvec 框架。
  - 之前提交的 stpncpy 和 strncpy 已经合入 glibc 上游主线。
- newlib:
  - 提交了向量数学库 RFC patch 到 newlib 上游。
  - 提交了 str* 相关共 17 个接口实现的 patch 到 newlib 上游。

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

本期提交的OpenJDK Valhalla仓patch:
- https://github.com/openjdk/valhalla/pull/2542 (8386618: [lworld] Remove unused entry_guard_Relocation)  清除未使用的entry_guard重定位类型，ARM64和RISC-V平台已不再使用该重定位
- https://github.com/openjdk/valhalla/pull/2544 (8386626: [lworld] Only enable valhalla IR tests in ScalarReplacementWithGCBarrierTests.java for aarch64 and x86)  完善值类与对象相关测试用例，考虑其它CPU平台

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/31106 (8384223: RISC-V: entry_barrier_offset should consider UseZtso)  为RISC-V平台修复Ztso场景C2 JIT方法entry_barrier偏移计算问题
- https://github.com/openjdk/jdk/pull/31140 (8366041: Shenandoah: Late Barrier Expansion)  为各CPU平台优化Shenandoah GC barrier展开时机，提高C2 JIT编译速度并改进JIT代码效率
- https://github.com/openjdk/jdk/pull/31246 (8384404: RISC-V: Do less implicit narrowing conversions)  为RISC-V平台修复数据类型转换潜在风险
- https://github.com/openjdk/jdk/pull/29703 (8376602: [Vector API] Upgrade SLEEF from 3.6.1 to 3.9.0)  同步并导入最新版SLEEF开源库，提高各CPU平台VectorAPI程序执行性能
- https://github.com/openjdk/jdk/pull/31310 (8385583: RISC-V: Debugger very slow during stepping)  为RISC-V平台修复特定场景java调试器单步执行速度慢的缺陷
- https://github.com/openjdk/jdk/pull/31351 (8385835: Shenandoah: Polish C2 pre/post barrier signatures)  为各CPU平台清理Shenandoah GC barrier相关汇编函数签名

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台C1 JIT编译器对JEP 401的支持，能够在Client模式（包括解释器、C1 JIT两种执行模式）下跑通JEP 401相关测试用例，通过兼容性测试。
目前已着手调试和实现RISC-V平台C2 JIT模块对JEP 401的支持，优先解决兼容性问题，短期目标能够在Server模式下跑通JEP 401新增测试用例。
本期详细修改如下：
- https://github.com/openjdk/valhalla/commit/b44b312e0fee4a841943cd5188bf567476aa8678
- https://github.com/openjdk/valhalla/commit/0cc2013eca9dd26a1600f813c11707f1e04465d5
- https://github.com/openjdk/valhalla/commit/371d26340c91a75ae8304ba06d8ef68763973a48
- https://github.com/openjdk/valhalla/commit/8faa89ca92e4270cc4e689c904cbe182be184775

### Go

提交代码

- 801460: runtime: add msan support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/801460 添加msan支持
- 802100: runtime, internal/fuzz: add libFuzzer support on riscv64 | https://go-review.googlesource.com/c/go/+/802100 添加 fuzz 支持
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 cgo 信号支持【合入】

Review
- 801681: runtime, internal/cpu: detect RISC-V vector extension and VLEN | https://go-review.googlesource.com/c/go/+/801681 支持 RISC-V RVV VLEN 长度动态侦测
- 796820: cmd/internal/obj/riscv: document rva23u64 feature macros | https://go-review.googlesource.com/c/go/+/796820 文档支持 【合入】
- 801683: runtime: save RISC-V vector registers state during async preemption | https://go-review.googlesource.com/c/go/+/801683 抢占过程中保存 RVV 寄存器状态 （已经影响部分images/的向量优化）
- 801360: test/codegen: add riscv64 checks for conditional subtractions | https://go-review.googlesource.com/c/go/+/801360 添加codegen 检查（目前 zkt 才有const time能力，大概率拒收）

### QEMU模拟器

实现RISC-V Packed-SIMD扩展的QEMU模拟器支持，提交至上游，Review中。

https://lists.nongnu.org/archive/html/qemu-riscv/2026-07/msg00697.html
