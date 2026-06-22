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

### V8

### OpenJDK

本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30732 (8382199: Remove unused parameter "dst" from CardTableBarrierSetAssembler::store_check())  为X86和ARM64平台汇编函数移除非必要的dst参数
- https://github.com/openjdk/jdk25u-dev/pull/541 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台回合Shenandoah GC一处load_reference_barrier调用对象错误问题修复

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30704 (8382039: Add support do_arch_array_entry() template)  为各CPU平台重构Stub调用入口声明
- https://github.com/openjdk/jdk/pull/30759 (8382315: RISC-V: TestMultiplyReductionByte.java fails with guarantee(is_uimm5(imm)) failed: uimm is invalid)  为RISC-V平台修复一处大矢量宽度场景滑窗指令立即数范围超标问题
- https://github.com/openjdk/jdk/pull/30780 (8382393: Enable VectorStoreMaskIdentityTest.java IR tests for RISC-V)   为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30823 (8382522: Disable stringop-overflow in safepointMechanism.cpp)  为RISC-V平台修复一处GCC编译器构建JDK报警问题
- https://github.com/openjdk/jdk/pull/30864 (8382690: aarch64: Clean up redundant restore_locals() in TemplateTable::invokeinterface)  为ARM64和RISC-V平台移除一处模板解释器接口函数调用场景非必要的locals变量恢复操作，提升性能

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
目前已完成RISC-V平台模板解释器、C1& C2 JIT模块的代码全解耦，能够构建和运行支持Server模式RISC-V JDK二进制。
同时，已着手调试和实现RISC-V平台模板解释器模块对JEP 401的支持，优先考虑兼容性问题，短期目标能够在解释模式下跑通JEP 401新增测试用例。
本期详细修如下：
- https://github.com/openjdk/valhalla/commit/44cf8f556b2b6f0178452e1c35d2e501fec23745 
- https://github.com/openjdk/valhalla/commit/323d7868ad0e810a44f9fdfa4bf16fc92450dd45 
- https://github.com/openjdk/valhalla/commit/b44b312e0fee4a841943cd5188bf567476aa8678 
- https://github.com/openjdk/valhalla/commit/6bde9f57f679377e6e850c78fdd37c46067bd4ba 

### Go

### QEMU模拟器
