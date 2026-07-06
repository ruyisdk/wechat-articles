# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

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

本期提交的JDK-25u主线patch:
- https://github.com/openjdk/jdk25u-dev/pull/541 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台回合Shenandoah GC一处load_reference_barrier调用对象错误问题修复

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30865 (8382691: RISC-V: Clean up redundant restore_locals() in TemplateTable::invokeinterface)  为ARM64和RISC-V平台移除一处模板解释器接口函数调用场景非必要的locals变量恢复操作以提升性能
- https://github.com/openjdk/jdk/pull/30837 (8382606: Enable VectorMinMaxTransforms.java IR tests for RISC-V)  为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30823 (8382522: Disable stringop-overflow in safepointMechanism.cpp)  为RISC-V平台修复一处GCC编译器构建JDK报警问题
- https://github.com/openjdk/jdk/pull/30634 (8377715: Thawing frame can undo deoptimization)  为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30893 (8382878: RISC-V: Missing InlineSkippedInstructionsCounter in ZGC barriers stubs)  为RISC-V平台修复一处ZGC场景内敛指令数评估准确性问题
- https://github.com/openjdk/jdk/pull/30901 (8382934: LateInlineQueueDrainTest.java fails without diagnostic option)  修复一处jtreg回归测试用例选项设置缺陷
- https://github.com/openjdk/jdk/pull/30890 (8380753: C2: RegMask::find_first_set() incorrectly returns partially contained sets for scalable vector registers)  为ARM64和RISC-V平台修复一处C2 JIT编译器可扩展矢量寄存器分配问题
- https://github.com/openjdk/jdk/pull/30945 (8383196: Shenandoah: Interpreter barriers clobber interpreter registers)  为ARM64和RISC-V平台修复一处模板解释器场景寄存器使用缺陷
- https://github.com/openjdk/jdk/pull/30990 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台修复一处Shenandoah GC一处load_reference_barrier调用对象错误问题

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台模板解释器模块对JEP 401的支持，能够在纯解释模式下跑通JEP 401相关测试用例，成功通过兼容性测试。
目前已着手调试和实现RISC-V平台C1& C2 JIT模块对JEP 401的支持，优先解决兼容性问题，短期目标能够在解释模式下跑通JEP 401新增测试用例。
本期详细修改如下：
- https://github.com/openjdk/valhalla/commit/2e7c204830c23d9b88daee1a7926aed9ad99ea8b 
- https://github.com/openjdk/valhalla/commit/39763548c92ec744e31edc4b52aa42275414d8ad 
- https://github.com/openjdk/valhalla/commit/9bda478af718f97e396f7f40a4a2a2c33d71afbc 
- https://github.com/openjdk/valhalla/commit/de1c6297cec79d18b5800187d3c504ae06c027ce 

### Go

### QEMU模拟器
