# RuyiSDK 双周进展汇报 第 080 期 · 2026 年 11 月 05 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵

- 新增 Milk-V Jupiter2 的 Bianbu 4.0.1 Desktop 中英文测试报告。[PR #411](https://github.com/ruyisdk/support-matrix/pull/411)
- 新增 SpacemiT K3 Pico-ITX 的 Bianbu 4.0.8 LXQt 中英文测试报告。[PR #412](https://github.com/ruyisdk/support-matrix/pull/412)
- 更新 VisionFive 2 Lite 的 Ubuntu 24.04.5 中英文测试报告。[PR #390](https://github.com/ruyisdk/support-matrix/pull/390)

### 开发板示例仓库

- 新增 HiFive Premier P550 的 Dhrystone 基准测试及 SiFive Kernel Library（SKL）中文示例。[PR #51](https://github.com/ruyisdk/board-docs/pull/51)、[PR #52](https://github.com/ruyisdk/board-docs/pull/52)
- 新增 Milk-V Jupiter2 的 llama-server 中文部署示例。[PR #55](https://github.com/ruyisdk/board-docs/pull/55)
- 开发板文档前端开放 SpacemiT K3 CoM260 Kit 的 ROS 2 第 11 至 15 章课程入口，涵盖扫描匹配、SLAM 与定位。[PR #14](https://github.com/DuoQilai/board-docs-frontend/pull/14)、[PR #16](https://github.com/DuoQilai/board-docs-frontend/pull/16)
- 补充 SpacemiT K3 Pico-ITX 的 ROS 2 第 2 至 4 章课程入口，并同步到开发板文档前端。[课程目录 PR #4](https://github.com/DuoQilai/ROS2_RISCV/pull/4)、[前端更新](https://github.com/DuoQilai/board-docs-frontend/commit/bfca45ef9b80fba0e9731ba51d9a6cc2f7792d9f)

### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 sinpif, sqrt, sqrtf, tanf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 atanhf, atan2f, atanpif, atan2pif, exp2f, cosf, coshf, cospif, exp10f, expf, log2f, log2p1f, rsqrtf, expm1f 至现有的 newlib 向量数学框架。


### GCC
### GCC

本期重点围绕 **RISC-V GCC 代码生成优化及真实硬件性能评测能力建设** 推进工作，在编译器上游优化和下一阶段性能分析准备方面取得进展。

**1. 完成三项 RISC-V GCC 后端代码生成优化，已合入 GCC 上游主线**

针对 RISC-V 位操作及整数运算中的冗余指令、指令组合和成本模型问题，完成三项后端优化，并于 10 月 27 日正式进入 GCC 开发主线：

- **Zba 整数运算优化：** 完善移位加法指令与整数除法、取余操作的组合识别，支持更多有符号和无符号运算场景，减少可优化代码中的冗余指令。
- **Zbs 位操作优化：** 利用 `bclr` 指令自身的移位索引语义，消除不必要的掩码计算，改进 RV32/RV64 位图操作的代码生成。
- **Zbkb 指令选择优化：** 修正 `packh` 指令的成本模型和匹配优先级，解决 Zbb/Zbkb 同时启用时无法正确选择更优指令的问题。

上述优化均已配套补充针对性回归测试，有助于提高 RISC-V 编译器对扩展指令的利用效率及生成代码的质量。

相关上游提交：

- [Zba 优化（r17-5638）](https://github.com/gcc-mirror/gcc/commit/cfbc8c48ae78c69401e8bc70d80eacbea8b47ec5)
- [Zbs 优化（r17-5639）](https://github.com/gcc-mirror/gcc/commit/282087fbab2d230a103c844316ac9c48db4e3b94)
- [Zbkb 优化（r17-5640）](https://github.com/gcc-mirror/gcc/commit/635d3209171d20bce4de35041097064a3afeff66)

**2. 完善RISE-CI工具链测试维护**

打通了`Hertner`容器服务与GITHUB Actions，新增`multilib构建场景检查`，进一步完善Toolchain CI验证边界。

目前聚焦RISC-V后端，每天会对新的RISC-V提交进行充分测试
- [multilib反馈问题示例](https://github.com/riseproject-dev/gcc-postcommit-ci/issues/275)

后续计划接入LLM对CI发现的错误进行评估和分析，协助开发者简化分析处理流程。

**3. 启动基于 SPEC CPU 2026 的 RISC-V 真实硬件性能评测准备工作**

引入新一代 SPEC CPU 2026 基准测试集，推进 GCC 在真实 RISC-V 硬件上的性能分析与优化研究。已开展测试环境及硬件资源需求评估，重点关注 RVV 1.0 支持、内存容量及性能分析能力。

针对候选 K3 等硬件平台，识别出完整 SPECspeed 2026 测试的内存资源限制，并开展其他硬件方案评估，为后续建立可复现的编译器性能对比环境做准备。

**下一步：** 推进测试平台确认与环境部署，逐步建立 GCC 不同优化选项及版本间的性能对比基线，通过热点分析寻找新的后端优化机会。

### LLVM

### V8
本期提交并合入的patch如下：
1. **[riscv] Fix RISC-V trusted pointer tag range check**
   [RISC-V] 修复可信指针标签范围检查 [CL8639244](https://chromium-review.googlesource.com/c/8639244)
2. **[riscv] Zero out-of-range trusted pointers on tag underflow**
   [RISC-V] 标签下溢时将越界可信指针置零 [CL8620871](https://chromium-review.googlesource.com/c/8620871)
3. **[riscv][maglev] Store zero-valued constants through the zero register**
   [RISC-V][Maglev] 借助零寄存器保存零值常量 [CL8641030](https://chromium-review.googlesource.com/c/8641030)
4. **[riscv] Derive CPU features from the GN build configuration**
   [RISC-V] 从 GN 编译配置推导 CPU 特性 [CL8641350](https://chromium-review.googlesource.com/c/8641350)
5. **[riscv][maglev] Preserve the NaN sign in Float64->Float32 conversions**
   [RISC-V][Maglev] 在 Float64 转 Float32 时保留 NaN 的符号位 [CL8701858](https://chromium-review.googlesource.com/c/8701858)
6. **[riscv][liftoff] Allocate sub-word atomic RMW temp outside the loop**
   [RISC-V][Liftoff] 在循环外分配子字原子 RMW 临时寄存器 [CL8714199](https://chromium-review.googlesource.com/c/8714199)

本期审阅并合入的patch如下：
1. **[riscv] Fix emit_i32_eqz error**
   [RISC-V] 修复 emit_i32_eqz 错误 [CL8691005](https://chromium-review.googlesource.com/c/8691005)
2. **[riscv] Implement missing RV64 Add643 ops**
   [RISC-V] 实现缺失的 RV64 Add643 运算 [CL8689521](https://chromium-review.googlesource.com/c/8689521)
3. **[riscv] Fix RV64 int32mul typo**
   [RISC-V] 修复 RV64 int32mul 拼写错误 [CL8690428](https://chromium-review.googlesource.com/c/8690428)
4. **[riscv] Emit only ebreak for stop() on hardware**
   [RISC-V] 在硬件上 stop() 仅生成 ebreak 指令 [CL8698658](https://chromium-review.googlesource.com/c/8698658)
5. **[riscv] Preserve vector tails for scalar moves**
   [RISC-V] 标量移动操作时保留向量尾部 [CL8714039](https://chromium-review.googlesource.com/c/8714039)
6. **[riscv] Allow vlen=1024**
   [RISC-V] 支持 VLEN=1024 [CL8585179](https://chromium-review.googlesource.com/c/8585179)

### OpenJDK

本期审阅并合入的JDK主线PR:
- https://github.com/openjdk/jdk/pull/32643 (8385698: [Valhalla] C1 omits type profiling for null-free types)  -- 为各CPU平台修复值类型profiling操作
- https://github.com/openjdk/jdk/pull/32476 (8390813: C2: Wrong entries in adlc commutative op lists)  -- 为各CPU平台修复C2矢量化操作缺陷
- https://github.com/openjdk/jdk/pull/32693 (8391442: Test compiler/c1/CanonicalizeArrayLength.java is timing out with VerifyOops)  -- 为RISC-V和ARM64优化C1重定位操作
- https://github.com/openjdk/jdk/pull/32592 (8391431: RISC-V: AOTCodeTest.java fails after JDK-8388288 with fastdebug)  -- 为RISC-V修复一处测试用例失败问题
- https://github.com/openjdk/jdk/pull/32496 (8350085: RISC-V: Enable upper GPR registers in C1)  -- 为RISC-V优化C1寄存器分配
- https://github.com/openjdk/jdk/pull/32061 (8389223: RISC-V: Implement CRC32C intrinsic using Zbc extension)  -- 利用Zbc扩展指令为RISC-V实现CRC32C instrinsic加速
- https://github.com/openjdk/jdk/pull/32046 (8389108: RISC-V: Use shift pairs for logical right shift and mask patterns)  -- 为RISC-V优化逻辑移位和掩码组合操作
- https://github.com/openjdk/jdk/pull/32604 (8391466: RISC-V: Remove unreachable non-acquiring CAS/GetAndSet/GetAndAdd match rules)  -- 为RISC-V清理未使用的C2 CAS匹配规则
- https://github.com/openjdk/jdk/pull/32629 (8391597: RISC-V: Use movptr2 for C2 pointer constants)  -- 为RISC-V优化C2常量指针移动操作

本期审阅并合入的JDK LTS主线PR:
- https://github.com/openjdk/jdk25u-dev/pull/763 (8391041: RISC-V: Fix out-of-bounds read in string_indexof_char intrinsic) -- 为RISC-V修复string_indexof_char intrinsic访存越界问题
- https://github.com/openjdk/jdk21u-dev/pull/3041 (8391041: RISC-V: Fix out-of-bounds read in string_indexof_char intrinsic)
- https://github.com/openjdk/jdk17u-dev/pull/4644 (8391041: RISC-V: Fix out-of-bounds read in string_indexof_char intrinsic)

Java重要新特性JEP 544: AOT静态编译（Ahead-of-Time Code Compilation）RISC-V移植工作进展：

JEP 544在RISC-V平台的移植通过功能测试，对应的性能收益符合预期，已合入JDK主线：
- https://github.com/openjdk/jdk/pull/32311 (8390102: RISC-V: Support AOT Code Cache)

相关JEP提案：
- https://openjdk.org/jeps/544 (JEP 544: Ahead-of-Time Code Compilation)

### Go

### QEMU


## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
