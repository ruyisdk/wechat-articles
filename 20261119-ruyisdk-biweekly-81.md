# RuyiSDK 双周进展汇报 第 081 期 · 2026 年 11 月 19 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

- 去除新闻页面无用的按钮
- 更新 l10n tools 文档

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵

- 更新 Sipeed Lichee Pi 4A 的 RevyOS 20260504 中英文测试报告。[PR #413](https://github.com/ruyisdk/support-matrix/pull/413)
- 修复 CI 中构建依赖的安装问题。[PR #414](https://github.com/ruyisdk/support-matrix/pull/414)

### 开发板示例仓库

- 新增 Milk-V Jupiter2 的 ONNX Runtime 中文部署与推理示例。[PR #57](https://github.com/ruyisdk/board-docs/pull/57)
- 新增 SpacemiT V100-C2201 中英文板卡文档及 HelloWorld、CoreMark 示例。[PR #58](https://github.com/ruyisdk/board-docs/pull/58)
- 开发板文档前端开放 SpacemiT K3 CoM260 Kit 的 ROS 2 第 16 至 19 章课程入口，并改为按课程目录确定展示范围。[PR #17](https://github.com/DuoQilai/board-docs-frontend/pull/17)、[PR #19](https://github.com/DuoQilai/board-docs-frontend/pull/19)

### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 tanh, tanhf, tanpi, tanpif 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 hypotf, lgammaf, log10f, log1pf, powf, sincosf, sincospif, sinf, sinhf, sinpif, sqrtf, tanf, tanhf, tanpif 至现有的 newlib 向量数学框架。

### GCC

### LLVM

### V8

### OpenJDK

本期审阅并合入的JDK主线PR链接:
- https://github.com/openjdk/jdk/pull/32604 (8391466: RISC-V: Remove unreachable non-acquiring CAS/GetAndSet/GetAndAdd match rules)
- https://github.com/openjdk/jdk/pull/32720 (8391881: RISC-V: jni_fast_Get<Primitive>Field registers the wrong pc for the speculative load)
- https://github.com/openjdk/jdk/pull/32727 (8390450: RISC-V: Add Xuantie vendor feature detection)
- https://github.com/openjdk/jdk/pull/32745 (8391942: RISC-V: Remove redundant null checks in needs_acquiring_load_reserved())
- https://github.com/openjdk/jdk/pull/31955 (8387725: RISC-V: Redundant memory barrier around various CAS instrucions)
- https://github.com/openjdk/jdk/pull/32718 (8391873: RISC-V: Prevent non-acquire CAS patterns from matching nodes that need acquire)
- https://github.com/openjdk/jdk/pull/32776 (8392015: Remove broken and untested VerifyStackAtCalls debug flag)
- https://github.com/openjdk/jdk/pull/32785 (8392041: RISC-V: TestFloat16ScalarOperations.java fails after JDK-8391717 with fastdebug)
- https://github.com/openjdk/jdk/pull/32635 (8391177: RISC-V: Optimize conditional arithmetic with Zicond)
- https://github.com/openjdk/jdk/pull/32806 (8392127: RISC-V: Replace assert with guarantee in patch_offset_in_jal and patch_offset_in_conditional_branch)

这些 PR 主要围绕 OpenJDK RISC-V 的硬件支持、性能优化和稳定性改进展开，可概括为四点：

- 扩展硬件支持：新增 Zibi 立即数比较分支指令支持，并补充玄铁处理器的厂商特性检测，更好地利用硬件能力（#32624、#32727）。
- 优化代码生成：减少访存时不必要的地址计算，利用 Zicond 优化条件算术运算，并在原子指令已提供所需内存序时消除外围冗余屏障（#32644、#32635、#31955）。
- 修复正确性问题：纠正 JNI 快速字段访问中推测性加载的 PC 记录，避免需要 acquire 语义的原子操作匹配到较弱的指令规则，修复半精度 FMA 的支持条件，并让分支偏移合法性检查在 release
  构建中也生效（#32720、#32718、#32785、#32806）。
- 清理冗余实现：删除不可达的非 acquire 原子操作匹配规则、多余的空指针检查，以及已损坏且缺乏测试的 VerifyStackAtCalls 调试选项和相关代码，降低维护成本（#32604、#32745、#32776）。

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
