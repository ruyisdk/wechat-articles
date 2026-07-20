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

### GCC

### LLVM

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
