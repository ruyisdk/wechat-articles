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

### V8

### OpenJDK

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30562 (8381611: RISC-V: Factor out function cmpptr from MacroAssembler)  为RISC-V汇编器重构代码，移除非必要的cmpptr汇编函数，改善代码可读性
- https://github.com/openjdk/jdk/pull/30598 (8381724: RISC-V: Pass temp registers and use them in CardTableBarrierSetAssembler::store_check())  为RISC-V汇编函数store_check传递额外的临时寄存器
- https://github.com/openjdk/jdk/pull/30491 (8380163: Fix implicit conversion in macroAssembler_aarch64.hpp)  为ARM64修复一处隐式数据类型转换潜在风险
- https://github.com/openjdk/jdk/pull/30616 (8381677: Remove dependence of UseSHA on UseSHAIntrinsics)  为各CPU后端清理UseSHA / UseSHAIntrinsics选项设置
- https://github.com/openjdk/jdk/pull/30646 (8381926: Fix implicit conversion in macroAssembler_riscv.hpp)  为RISC-V修复一处隐式数据类型转换潜在风险

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
通过阅读JEP 401规范文档和调试对比X86/ARM64相关代码，已初步了解该特性的设计思路，并开始着手实现CPU平台一侧代码的解耦。
目前已完成模板解释器模块的代码解耦，并能够构建支持解释执行模式RISC-V JDK二进制，下一步考虑C1& C2 JIT模块的代码解耦。
详细修改见如下链接：
- https://github.com/openjdk/valhalla/commit/dd306a5978bb081e842a607b175d9cda7bff1b7f
- https://github.com/openjdk/valhalla/commit/519e69b4882121823d5b66ce1da496d74c1989d5
- https://github.com/openjdk/valhalla/commit/d1d65189cae1a40b16a8f4136a42147271180459
- https://github.com/openjdk/valhalla/commit/ef493a94d3706fa5a8dcafe587b5f6a5616a74bc
- https://github.com/openjdk/valhalla/commit/1a32a6e292f8efa4ae79ac352684ee5b3027c305

### Go

### 模拟器QEMU
