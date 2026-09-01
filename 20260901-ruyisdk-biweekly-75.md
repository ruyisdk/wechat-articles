# RuyiSDK 双周进展汇报 第 075 期 · 2026 年 09 月 01 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

### GCC

### LLVM

### V8

### OpenJDK

本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/32123 (8388192: [lworld] Some code is not guarded by Arguments::is_valhalla_enabled())  为各CPU平台添加必要的value type特性开关判断

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/31576 (8386292: Shenandoah: Simplify and strengthen C1 barriers)  为各CPU平台清理ShenandoahGC C1 barrier汇编器实现
- https://github.com/openjdk/jdk/pull/31627 (8387078: RISC-V: x27 can be allocated in CompressedOops mode)  CompressedOops场景下将RISC-V x27设置为可分配寄存器
- https://github.com/openjdk/jdk/pull/28894 (8374184: RISC-V: implement GCM intrinsic with Zvkg and Zvkned extension)  为RISC-V平台实现GCM加密解密intrinsic实现
- https://github.com/openjdk/jdk/pull/31717 (8387381: RISC-V: assert failed with fastdebug build on systems with different core types)  为RISC-V平台修复异构芯片场景断言错误
- https://github.com/openjdk/jdk/pull/30816 (8379706: Cleanup and clarify BarrierSetAssembler::try_resolve_weak_handle_in_c2)  为各CPU平台清理barrier汇编器实现
- https://github.com/openjdk/jdk/pull/31793 (8387789: RISC-V: Optimize G1 post-write barrier conditional card mark)  为RISC-V平台优化G1GC barrier实现
- https://github.com/openjdk/jdk/pull/31779 (8387747: Enable long vector multiply IR tests for RISC-V)  为RISC-V平台打开矢量乘法IR测试
- https://github.com/openjdk/jdk/pull/31806 (8387857: RISC-V: Add UseZvbb to RVA23U64Profile)  为RISC-V平台补齐RVA23扩展集合
- https://github.com/openjdk/jdk/pull/27409 (8368180: RISC-V: Remove redundant ext_Zicboz.enable_feature())  为RISC-V平台删除冗余的Zicboz扩展使能

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）RISC-V移植工作进展：
RISC-V平台JEP 401兼容性相关工作已随Value Class PR合并到JDK主线仓，通过兼容性测试，且支持值类型Flattening优化（UseArrayFlattening & UseFieldFlattening）。
下一步工作：继续调研方法调用场景下Value Class值类型参数传递内联优化在X86和ARM64上的实现细节（InlineTypePassFieldsAsArgs & InlineTypeReturnedAsFields）。
Value Class PR详细修改如下：
- https://github.com/openjdk/jdk/pull/31120 (8389219: Implement JEP 401: Value Objects (Preview))

### Go

### QEMU

## 社区动态


---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
