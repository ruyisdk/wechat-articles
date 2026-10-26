# RuyiSDK 双周进展汇报 第 079 期 · 2026 年 10 月 22 日

## 卷首语

各位 RISC-V 开发者与 RuyiSDK 社区伙伴，大家好！

第六届 RISC-V 中国峰会刚刚在深圳会展中心圆满落幕。RuyiSDK 团队此次以两场分论坛技术报告、六篇技术海报和 D15 独立开源展区"三位一体"参展，从包管理器、编译器调优、芯片验证，到 AI 辅助开发与教育生态，与现场观众做了大量面对面的交流，欢迎大家移步阅读：[第六届 RISC-V 中国峰会｜RuyiSDK 持续推进 RISC-V 软硬件生态共建](https://ruyisdk.cn/t/topic/2893)。

RuyiSDK 各组件的常规迭代依旧在稳步推进，具体的技术进展细节，请直接参见本期双周进展报告正文，了解更详尽的更新内容，并期待您与我们一同参与社区共建。

获取更多资讯、下载最新工具或参与技术讨论，欢迎通过文章最下方的渠道找到我们。

## 基础开发环境

### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.54.0 版本预期将在 10 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.53.0 试用。本周 RuyiSDK 开发与测试团队大部分都前往深圳出席了 RISC-V 中国峰会，您可在 D15 RuyiSDK 展位找到他们。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容仍在开发中或开发完成：

* 检测软件包与当前系统的 ABI 兼容性的工作。
* 更多 RuyiSDK 官方维护软件包的 macOS 打包工作。
* 针对 SpacemiT K1/K3 的工具链适配。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

### RuyiSDK IDE

- 添加 build 模块的测试单元
- 搜索软件包时，如果找不到将提示更完整
- Ruyi 包管理器过低时提示用户升级
- 测试由 CI 构建的多平台 VSCodium IDE
- 测试集成的第三方插件

## 社区与内容建设

### packages-index 资源更新

近两周 ISCAS 软件源遇到了数据同步问题，已构建完成的软件包未能刷新到公网，因此暂无软件包方面的更新。

### 开发板支持矩阵

- 新增 RDC2022-D1s 开发板资料及 RT-Thread Smart 5.0.0 出厂固件中英文测试报告。[PR #410](https://github.com/ruyisdk/support-matrix/pull/410)

### 开发板示例仓库

- 补充 SpacemiT K3 CoM260 Kit 的 ROS 2 第 9、10 章课程讲义和实验手册，涵盖 Gazebo 仿真与 SLAM 基础，并限定前端课程展示范围。[课程更新](https://github.com/DuoQilai/ROS2_RISCV/commit/35a4109808b24f60b26bcd901be1c2448769814e)、[前端更新](https://github.com/DuoQilai/board-docs-frontend/compare/2d2689dddc5e2affe9c5c5c0f702a1c9fde938e1...5fd4bcb986efff805df30da8122c90f4e1cba526)

## 基础组件

### 基础C库

- GLIBC:
  - 移植了 sinh, sinhf, sinpi 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 acosf, logf, asinf, asinhf, asinpif, atanf 至现有的 newlib 向量数学框架。

### GCC

- Rebase了Zvdota/Zvbdota的GCC支持，修复了发现的问题
  - https://patchwork.sourceware.org/project/gcc/patch/20261014093604.829234-2-jiawei@iscas.ac.cn/
- 添加了Ztt扩展的Md支持
  - https://github.com/ruyisdk/riscv-gcc/commit/368ab1b0b88984dbf9573d4eb7c324c20cd5c371
- 更新了P扩展的支持至0.6版本
  - https://github.com/ruyisdk/riscv-gcc/commit/883d7da2ca2f20d7ddc2b927e8d639a4eec65ecc

### LLVM

本期提交 PR 如下

- [RISCV] Mark RVA23.1 and RVB23.1 profiles as non-experimental
  https://github.com/llvm/llvm-project/pull/234064
  将已批准的 RVA23.1 和 RVB23.1 profile 标记为非实验性，并同步更新文档和测试。已合并
- [RISCV][GlobalISel] Use Zfhmin for G_FPTRUNC to f16
  https://github.com/llvm/llvm-project/pull/231370
  在 GlobalISel 中使用 Zfhmin 支持 f32/f64 到 f16 的浮点截断，缺少所需扩展时回退到库调用，并补全半精度 `G_FREM` 的合法化。已合并
- [RISCV][GISel] Implement LLT variant of allowsMisalignedMemoryAccesses
  https://github.com/llvm/llvm-project/pull/232183
  实现 `allowsMisalignedMemoryAccesses` 的 LLT 重载，使 GlobalISel 在启用非对齐标量访存时可使用更宽的访存指令展开 `memcpy`，避免逐字节复制。已合并
- [RISCV][P-ext] Add scalar mulq(r) intrinsics
  https://github.com/llvm/llvm-project/pull/232316
  为 RISC-V P 扩展新增标量 Q-format 乘法及舍入变体 intrinsics，并实现 RV32/RV64 对应的指令选择。已合并
- [RISCV][P-ext] Add scalar multiply high accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/232340
  为 RISC-V P 扩展新增标量乘法高位累加 intrinsics，支持有符号、无符号、混合符号及舍入变体，并实现 RV32/RV64 对应的指令选择。已合并
- [Clang][RISCV] Require 64bit for __builtin_riscv_rev16_64
  https://github.com/llvm/llvm-project/pull/232362
  修正 `__builtin_riscv_rev16_64` 的 RV64 特性约束，使 RV32 正确报告不支持该 builtin，避免后端类型合法化崩溃。已合并
- [RISCV][P-ext] Add scalar sati/usati intrinsics
  https://github.com/llvm/llvm-project/pull/233769
  为 RISC-V P 扩展新增有符号和无符号标量饱和 intrinsics，支持 32 位及 RV64 专用的 64 位形式，并实现对应的指令选择。已合并
- [RISCV][P-ext] Add missing packed pair
  https://github.com/llvm/llvm-project/pull/232202
  补全 RISC-V P 扩展 Packed Pair Intrinsics 中的 `v2i32` 支持。已合并
- [RISCV][P-ext] Support Packed Multiplication with Widening Horizontal Addition intrinsics
  https://github.com/llvm/llvm-project/pull/232612
  为 RISC-V P 扩展新增打包乘法与扩宽横向加法 intrinsics 支持。已合并
- [InstCombine][ValueTracking] Infer range for an addend from the sum range
  https://github.com/llvm/llvm-project/pull/231357
  根据和的比较结果及另一个加数的已知范围推导加数范围，消除冗余范围检查。正在 review
- [RISCV][RuntimeLibcalls] Generate and select vector libcalls with TableGen and fix SLEEF selection on RISC-V
  https://github.com/llvm/llvm-project/pull/231739
  使用 TableGen 生成并选择 SLEEF、ArmPL 和 AMDLIBM 向量库调用，并修复 RISC-V 的 SLEEF 调用选择。正在 review

### V8

本期提交并合入的patch如下：

1. **[riscv] Always sign-extend binary-search switch input on riscv64**
   [RISC-V] riscv64 上对二分查找 switch 输入始终做符号扩展 [CL8582687](https://chromium-review.googlesource.com/c/8582687)
2. **[riscv][sandbox] Tag entries in the TrustedPointerTable**
   [RISC-V][Sandbox] 为可信指针表中的条目添加标记 [CL5373845](https://chromium-review.googlesource.com/c/5373845)
3. **[riscv][liftoff] Track f32 and 32-bit f64 constants Port commit 8166bc3931b3291658874b809130e696cdd17fd0**
   [RISC-V][Liftoff] 追踪 f32 和 32位 f64 常量，移植提交 8166bc39 [CL8581294](https://chromium-review.googlesource.com/c/8581294)
4. **[riscv][interpreter] Check max_arguments in entry trampoline**
   [RISC-V][解释器] 在入口跳板中增加最大参数数校验 [CL8581295](https://chromium-review.googlesource.com/c/8581295)

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

本期提出的主线CL:

- 849425: cmd/compile: remove MOVDnop on riscv64 | https://go-review.googlesource.com/c/go/+/849425 去除多余的 MOVDnop 空指令
- 755840: crypto/internal/fips140/sha512: enable zvknhb for riscv64 | https://go-review.googlesource.com/c/go/+/755840 添加 sha2-512 支持【合入】
- 752981: crypto/internal/fips140/sha256: enable zvknha for riscv64 | https://go-review.googlesource.com/c/go/+/752981 添加 sha2-256 支持【合入】

本期审阅的主线CL:

- 849005: cmd/compile: optimise bit tests with register shift values on riscv64 | https://go-review.googlesource.com/c/go/+/849005 优化寄存器位移指令
- 732700: cmd/internal/obj/riscv: add assembly support of Zfa extension | https://go-review.googlesource.com/c/go/+/732700 添加 zfa 汇编支持
- 806260: runtime: prefer the vDSO for riscv_hwprobe | https://go-review.googlesource.com/c/go/+/806260  优先使用 vDSO 执行 riscv_hwprobe

### QEMU

RuyiSDK QEMU仓库发布了P扩展V0.6版本的实现，完成了目前P扩展所有指令的模拟支持。目前P扩展分支基于上游v11.1.0开发。

- https://github.com/ruyisdk/qemu/tree/p-dev

同时，RuyiSDK QEMU仓库合并了来自达摩院的AME扩展V0.6版本的实现，已完成 ame-v0.6 主要功能开发、架构重构，支持 32/64 位用户模式与系统模式，覆盖矩阵计算、整数与浮点混合运算、数据搬运和类型转换，并支持多核共享后端、状态迁移及调试。目前AME扩展分支同样基于上游v11.1.0开发。

- https://github.com/ruyisdk/qemu/tree/ame-0.6

欢迎试用，并提出宝贵意见。

## 社区动态

**[第六届 RISC‑V 中国峰会｜RuyiSDK 持续推进 RISC‑V 软硬件生态共建](https://ruyisdk.cn/t/topic/2893)**：RuyiSDK 在第六届 RISC‑V 中国峰会分享生态共建相关成果，推动RISC‑V软硬件生态建设。

- 进迭开发者大会发表演讲《AI 辅助 K1 移植 Redox OS》并参与 RISC-V 社区生态沙龙
- RISC-V 中国峰会发表演讲 《驾驭RISC-V向量扩展：Go语言基于RVV优化实战》

---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
