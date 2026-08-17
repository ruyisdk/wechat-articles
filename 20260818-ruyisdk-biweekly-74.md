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

### V8

### OpenJDK

本期审阅并合入的JDK主线patch:

- https://github.com/openjdk/jdk/pull/31340 (8385702: Improve polymorphic handling in JDK-8385648)  为各CPU平台优化polymorphic相关处理的指令跳转逻辑
- https://github.com/openjdk/jdk/pull/31358 (8384442: Shenandoah: Remove vestigial CAS barrier code)  为各CPU平台清理ShenandoahGC未使用的CAS barrier函数
- https://github.com/openjdk/jdk/pull/31373 (8385915: RISC-V: Remove unused cmpxchg* methods)  为RISC-V平台清理未使用的cmpxchg汇编函数
- https://github.com/openjdk/jdk/pull/31423 (8386161: RISC-V: Auto-enable Zvkn/Zvkg extension features)  为RISC-V平台自动开启Zvkn/Zvkg探测和加解密指令运用（SpaceMit K3平台加解密操作性能实测2-3倍性能加速）
- https://github.com/openjdk/jdk/pull/31434 (8386252: Shenandoah: Polish LRB argument preparation)  为各CPU平台优化LRB参数准备
- https://github.com/openjdk/jdk/pull/31424 (8385323: Support capstone on riscv64)  支持配置构建面向RISC-V平台的capstone反汇编器so文件

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台Java虚拟机的模板解释器、C1、C2 JIT即时编译器三大模块对JEP 401特性的兼容性支持，能够在Server模式下跑通JEP 401相关兼容性测试用例。
同时，JVM相关修改可在RISC-V平台全量通过JDK自带全部回归测试用例。JEP 401兼容性相关工作已经通过PR形式提交到Valhalla代码仓，详细修改见PR链接。
下一步工作：
继续调研JEP 401 Value Class相关的性能优化实现细节，具体包括值类型Flattening支持（UseArrayFlattening & UseFieldFlattening）和方法调用值类型参数传递内联支持（InlineTypePassFieldsAsArgs & InlineTypeReturnedAsFields）。

- https://github.com/openjdk/valhalla/pull/2531 (8386240: [lworld] Port JEP 401 to RISC-V)

### Go

### QEMU模拟器
