# RuyiSDK 双周进展汇报 第 069 期·2026 年 05 月 26 日

## 卷首语


## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件


## 编译工具链

### 基础C库

### GCC

### LLVM


## 语言运行时

### V8

### OpenJDK
本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30705 (8382087: aarch64: remove unused function declarations in macroAssembler_aarch64.hpp)  为ARM64移除未使用的函数声明

本期回合的JDK21u仓库patch:
- https://github.com/openjdk/jdk21u-dev/pull/2691 (8379464: Enable missing stack walking test via jtreg requires for RISC-V)  为RISC-V使能一项栈回溯测试用例
- https://github.com/openjdk/jdk21u-dev/pull/2692 (8378810: Enable missing FFM test via jtreg requires for RISC-V)  为RISC-V使能一项外部函数和内存接口FFM测试用例

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30309 (8380416: Enable CmpUNodeValueTests.java IR tests for RISC-V)   为RISC-V使能一项无符号比较白盒测试用例
- https://github.com/openjdk/jdk/pull/30258 (8379792: UBSAN runtime error: signed integer overflow during compress expand value transform)  为RISC-V和ARM64修复一类有符号整数溢出风险
- https://github.com/openjdk/jdk/pull/28366 (8363996: Obsolete UseCompressedClassPointers)  为各CPU平台4移除UseCompressedClassPointers特性支持
- https://github.com/openjdk/jdk/pull/30364 (8380580: Enable TestCombineAddPWithConstantOffsets.java IR tests for RISC-V)  为RISC-V使能一项访问地址加法优化白盒测试用例
- https://github.com/openjdk/jdk/pull/30107 (8378985: serviceability/sa/TestJhsdbJstackMixedWithXComp.java failed if sender frame is return barrier of Continuation)  为各CPU平台修复协程场景栈回溯问题
- https://github.com/openjdk/jdk/pull/30397 (8380789: RISC-V: TestOpaqueConstantBoolNodes.java fails when running without RVV)  为RISC-V修复一项测试用例硬件匹配问题
- https://github.com/openjdk/jdk/pull/30488 (8381250: Enable VectorLogicalOpIdentityTest.java IR tests for RISC-V)  为RISC-V使能一项矢量逻辑运算优化白盒测试用例
- https://github.com/openjdk/jdk/pull/30545 (8381554: RISC-V: Small refactoring for cmp_klass_compressed macro-assembler routine)  为RISC-V重构压缩对象类指针比较汇编函数逻辑

### Go


## 版本测试及遗留问题
