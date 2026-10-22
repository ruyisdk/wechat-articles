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

- 新增 RDC2022-D1s 开发板资料及 RT-Thread Smart 5.0.0 出厂固件中英文测试报告。[PR #410](https://github.com/ruyisdk/support-matrix/pull/410)

### 开发板示例仓库

- 补充 SpacemiT K3 CoM260 Kit 的 ROS 2 第 9、10 章课程讲义和实验手册，涵盖 Gazebo 仿真与 SLAM 基础，并限定前端课程展示范围。[课程更新](https://github.com/DuoQilai/ROS2_RISCV/commit/35a4109808b24f60b26bcd901be1c2448769814e)、[前端更新](https://github.com/DuoQilai/board-docs-frontend/compare/2d2689dddc5e2affe9c5c5c0f702a1c9fde938e1...5fd4bcb986efff805df30da8122c90f4e1cba526)

### 官网&文档


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
