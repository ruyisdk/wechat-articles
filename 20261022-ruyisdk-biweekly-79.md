# RuyiSDK 双周进展汇报 第 079 期 · 2026 年 10 月 22 日

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

本期审阅并合入的JDK主线PR:
- https://github.com/openjdk/jdk/pull/32309 (8358959: RISC-V: Add Zalasr support for RVWMO)  -- 为RISC-V 模板解释器，C1/C2 JIT添加Zalasr扩展支持
- https://github.com/openjdk/jdk/pull/32480 (8390826: RISC-V: Use dedicated vector mask logical instructions)  -- 为RISC-V 优化特定掩码逻辑运算
- https://github.com/openjdk/jdk/pull/32512 (8391044: [zgc] unused parameter "node" in z_color and z_uncolor)  -- 为各CPU平台移除ZGC相关的未使用的函数参数
- https://github.com/openjdk/jdk/pull/32528 (8391171: Enable TestVectorBroadcastTransforms.java IR tests for RISC-V)  -- 为RISC-V打开IR向量代码匹配测试
- https://github.com/openjdk/jdk/pull/32494 (8391041: RISC-V: Fix out-of-bounds read in string_indexof_char intrinsic)  -- 为RISC-V修复string_indexof_char内联函数访存越界风险
- https://github.com/openjdk/jdk/pull/32550 (8391236: RISC-V: Save a jump in string_indexof_char intrinsic)  -- 为RISC-V优化string_indexof_char内联函数
- https://github.com/openjdk/jdk/pull/31279 (8385696: Remove unnecessary ICache flush calls before code copy operations)  -- 为各CPU平台移除不需要的指令缓存同步操作
- https://github.com/openjdk/jdk/pull/32567 (8391330: RISC-V: JSR166TestCase.java fails after JDK-8369828)  -- 为RISC-V修复Zalasr扩展相关失败用例
- https://github.com/openjdk/jdk/pull/32568 (8391333: RISC-V: C2: Use zext.h and zext.w for AndL with 16-bit and 32-bit mask)  -- 为RISC-V优化零扩展代码生成
- https://github.com/openjdk/jdk/pull/32553 (8353495: tools/launcher/ExecutionEnvironment.java fails on RISC-V when run by qemu)  -- 为RISC-V修复QEMU User模式用例失败问题
- https://github.com/openjdk/jdk/pull/31959 (8387969: RISC-V: Optimize zero-result integer cmoves with Zicond)  -- 为RISC-V优化特定场景条件MOVE代码生成
- https://github.com/openjdk/jdk/pull/31923 (8388288: RISC-V: Use Zicond instruction for encode/decode heap oop)  -- 为RISC-V优化特定场景条件MOVE生成（利用Zicond扩展）

Java重要新特性JEP 544: AOT静态编译（Ahead-of-Time Code Compilation）RISC-V移植工作进展：

已初步完成JEP 544在RISC-V平台的移植，开展功能测试和性能验证：
- https://github.com/DingliZhang/jdk/commit/5ee95351ad6902e02605192a610b0ad327792b34

相关JEP提案：
- https://openjdk.org/jeps/544 (JEP 544: Ahead-of-Time Code Compilation)

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
