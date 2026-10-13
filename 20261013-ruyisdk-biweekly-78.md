# RuyiSDK 双周进展汇报 第 078 期 · 2026 年 10 月 13 日

## 卷首语

>

## 基础开发环境


### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.54.0 版本预期将在 10 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.53.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* 检测软件包与当前系统的 ABI 兼容性的工作。
* 更多 RuyiSDK 官方维护软件包的 macOS 打包工作。
* 针对 SpacemiT K1/K3 的工具链适配。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新软件包：
  * `board-image/ubuntu-server-riscv64-sifive-unmatched`: 修复下载地址。

感谢 [weilinfox][weilinfox] 的贡献！

您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

[weilinfox]: https://github.com/weilinfox

### 开发板支持矩阵

- 新增 ESP32-C3 的 RT-Thread 5.3.1 中英文测试报告。[PR #406](https://github.com/ruyisdk/support-matrix/pull/406)
- 更新 Milk-V Duo S 的 xv6 中英文测试报告。[PR #407](https://github.com/ruyisdk/support-matrix/pull/407)
- 新增 CH32V003 的 RT-Thread 5.3.1 中英文测试报告。[PR #408](https://github.com/ruyisdk/support-matrix/pull/408)
- 新增 ESP32-C6 的 RT-Thread 5.3.1 中英文测试报告。[PR #409](https://github.com/ruyisdk/support-matrix/pull/409)

### 开发板示例仓库

- 补充 SpacemiT K3 CoM260 Kit 的 ROS 2 第 3 至 8 章课程讲义和实验手册。[PR #48](https://github.com/ruyisdk/board-docs/pull/48)、[课程目录](https://github.com/DuoQilai/ROS2_RISCV/blob/fe977a732838de83065129ce63309ca2bb000325/course_support/k3_com260_kit/catalog.yml)
- 开发板文档前端支持从课程仓库同步 ROS 2 目录、正文和媒体资源，并按课程目录自动生成章节页面。[PR #12](https://github.com/DuoQilai/board-docs-frontend/pull/12)

### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 powf, sincos, sincosf, sincospi, sincospif, sinf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 hypot, log10, log1p, sincospi, sinpi, tanpi 至现有的 newlib 向量数学框架。

### GCC
- 完善了 ZTT 的 GNU 工具链后端，启动了 GEMM / GEMV 算子验证方案设计与优化，编译时间降低约 5.05%—6.97%，已经开始改善 GCC 后端的编译成本
  - https://github.com/ruyisdk/riscv-gcc/tree/ztt-dev
  - https://github.com/ruyisdk/AME-operator
- 修复了 RISE-CI 运维中发现的一些问题
  - https://github.com/riseproject-dev/riscv-gnu-toolchain-ci/pull/2
  - https://github.com/riseproject-dev/gcc-postcommit-ci/pull/89
- 持续推进 Packed-SIMD 扩展更新，已同步至0.6文档版本
  - https://github.com/riscv/riscv-p-spec/releases/tag/v0.6
- 提交了 Zvzip 0.3 版本的 gcc 后端支持，更新了 API 名称，添加了 VLS 支持
  - https://patchwork.sourceware.org/project/gcc/patch/20261010020704.300115-1-jiawei@iscas.ac.cn/

### LLVM

本期提交 PR 如下

- [RISCV][P-ext] Add packed saturation intrinsics
  https://github.com/llvm/llvm-project/pull/224432
  为 RISC-V P 扩展新增 packed saturation intrinsics 支持。上期正在 review，本期已合并
- [RISCV][P-ext] Support Packed Multiply High Parts
  https://github.com/llvm/llvm-project/pull/225015
  为 RISC-V P 扩展新增 Packed Multiply High Parts intrinsic 支持。上期正在 review，本期已合并
- [RISCV][P-ext] Support the missing packed pair
  https://github.com/llvm/llvm-project/pull/226992
  补全 RISC-V P 扩展 Packed Pair Intrinsics 中的 `v2i16` 支持。已合并
- [RISCV][P-ext] Support Packed Widening Unzip
  https://github.com/llvm/llvm-project/pull/227211
  为 RISC-V P 扩展新增 Packed Widening Unzip Intrinsics 支持。已合并
- [RISCV] Support frame pointers in SiFive CLIC preemptible handlers
  https://github.com/llvm/llvm-project/pull/221318
  支持 SiFive CLIC 可抢占中断处理函数使用帧指针。已合并
- [RISCV] Reject reserved (qc.)cm.mvsa01/(qc.)cm.mva01s encodings in the disassembler
  https://github.com/llvm/llvm-project/pull/229091
  在反汇编器中拒绝 `(qc.)cm.mvsa01` 和 `(qc.)cm.mva01s` 的保留编码，补充寄存器组合及 RVE 寄存器约束检查。已合并
- [RISCV] Fix FP properties for Zvbdota instructions
  https://github.com/llvm/llvm-project/pull/228737
  为 Zvbdota 浮点指令补充可能触发浮点异常的属性，并为使用动态舍入模式的 `vfbdota.vv` 添加隐式 FRM 依赖。已合并
- [RISCV][P-ext] Support Packed Slide 1 up/down
  https://github.com/llvm/llvm-project/pull/228049
  为 RISC-V P 扩展新增 Packed Slide 1 up/down Intrinsics 及相应代码生成支持。已合并
- [Clang][RISCV] Add packed widening shift intrinsics
  https://github.com/llvm/llvm-project/pull/224790
  为 Clang RISC-V 新增 packed widening shift intrinsics 支持。已合并
- [mlir][arith] Handle unsigned moduli in int-range optimizations
  https://github.com/llvm/llvm-project/pull/224933
  完善 MLIR arith 整数范围优化对无符号模数的处理，避免将最高位为 1 的无符号模数误判为负值。已合并
- [Clang][RISCV] Add packed narrowing shift intrinsics
  https://github.com/llvm/llvm-project/pull/228726
  为 RISC-V P 扩展新增 packed narrowing shift intrinsics，支持逻辑右移、算术右移及舍入变体。已合并
- [Clang][RISCV][P-ext] Add packed Q-format widening accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/228009
  新增 P 扩展 Q-format 扩宽乘累加 intrinsics，并实现 RV32/RV64 对应的指令选择与 lowering。已合并
- [SelectionDAG][RISCV] Account for samesign in preferred export extensions
  https://github.com/llvm/llvm-project/pull/226013
  在跨基本块值的扩展偏好分析中考虑 `samesign`，避免无符号同号比较取消既有的符号扩展偏好，减少部分 RISC-V `i8`/`i16` 冗余零扩展。正在 review

### V8
本期我们开始在实际硬件平台上开展基于Node.js的RVV的Wasm SIMD功能/性能测试，并在一开始就发现旧版内核不提供hwprobe，导致V8 runtime无法正确获取运行时指令集特征的问题。这类问题是在仅基于V8的开发和测试中无法发现的，接下来适配会进一步推进。

本期提交并合入的patch：
1. **[riscv] Fix CompareTaggedAndBranch with relocatable immediates**
   [RISC-V] 修复带可重定位立即数的 CompareTaggedAndBranch [CL8436921](https://chromium-review.googlesource.com/c/8436921)
2. **[riscv][maglev] Zero-extend string index before address computation**
   [RISC-V][Maglev] 在地址计算前对字符串索引做零扩展 [CL8438659](https://chromium-review.googlesource.com/c/8438659)
3. **[riscv][wasm] Fix OOL spill space size in RecordSpillsInSafepoint**
   [RISC-V][WASM] 修复 RecordSpillsInSafepoint 中Out-Of-Line代码区段溢出空间大小 [CL8436642](https://chromium-review.googlesource.com/c/8436642)
4. **[riscv] Fix zero-extension of BitcastFloat32ToWord32 in ChangeUint32ToUint64**
   [RISC-V] 修复 ChangeUint32ToUint64 中 BitcastFloat32ToWord32 的零扩展 [CL8461522](https://chromium-review.googlesource.com/c/8461522)
5. **[riscv][wasm]Patch jump table slots atomically**
   [RISC-V][WASM] 原子方式修补跳转表槽位 [CL8483311](https://chromium-review.googlesource.com/c/8483311)
6. **[riscv][sandbox] Tag entries in the TrustedPointerTable**
   [RISC-V][Sandbox] 为可信指针表中的条目添加标记 [CL5373845](https://chromium-review.googlesource.com/c/5373845)
7. **[riscv][maglev] Avoid clobbering allocatable register t4 in ByteSwap**
   [RISC-V][Maglev] 在 ByteSwap 中避免覆盖可分配寄存器 t4 [CL8492392](https://chromium-review.googlesource.com/c/8492392)
8. **[riscv][wasm] Zero upper lanes in v128.load{32,64}_zero**
   [RISC-V][WASM] 在 v128.load{32,64}_zero 中将高位通道置零 [CL8485765](https://chromium-review.googlesource.com/c/8485765)
9. **[riscv][wasm] Fix growable stacks return trampoline frame teardown**
   [RISC-V][WASM] 修复可增长栈返回跳板帧的销毁逻辑 [CL8535227](https://chromium-review.googlesource.com/c/8535227)
10. **[riscv][wasm] Add preemptive stack checks to generic JS-to-Wasm wrapper**
    [RISC-V][WASM] 在通用 JS-to-Wasm 包装器中增加抢占式栈检查 [CL8536826](https://chromium-review.googlesource.com/c/8536826)
11. **[riscv][compiler] Simplify AssembleConstructFrame**
    [RISC-V][编译器] 简化 AssembleConstructFrame 实现 [CL8535328](https://chromium-review.googlesource.com/c/8535328)
12. **[riscv][compiler] Add stack check to compiled JS-to-Wasm wrappers**
    [RISC-V][编译器] 在编译后的 JS-to-Wasm 包装器中添加栈检查 [CL8535329](https://chromium-review.googlesource.com/c/8535329)
13. **[riscv] Implement and correctly round FP16 RVV fused multiply-add**
    [RISC-V] 实现 FP16 RVV 融合乘加并正确处理舍入 [CL8544731](https://chromium-review.googlesource.com/c/8544731)

本期审阅并合入的patch：
1. **[riscv] Fall back to /proc/cpuinfo when riscv_hwprobe is unavailable**
   [RISC-V] riscv_hwprobe 不可用时回退读取 /proc/cpuinfo [CL8473041](https://chromium-review.googlesource.com/c/8473041)

### OpenJDK

本期审阅并合入的JDK主线PR:
- https://github.com/openjdk/jdk/pull/32391 (8389939: RISC-V: OrderAccess can be simplified by UseZtso)  --  为RISC-V优化强内存序场景JVM C++内存访问
- https://github.com/openjdk/jdk/pull/32392 (8390452: RISC-V: gc/shenandoah/TestSieveObjects.java fails with "assert(UseZba) failed: must be")  -- 为RISC-V修复ShenandoahGC场景断言错误
- https://github.com/openjdk/jdk/pull/32096 (8389378: RISC-V: Eliminate redundant sext.w by fusing ConvI2L with int producers)  -- 为RISC-V优化32位整数运算符号扩展优化
- https://github.com/openjdk/jdk/pull/32417 (8390522: RISC-V: Avoid clobbering ra in the nmethod entry barrier)  -- 为RISC-V改进JIT方法入口barrier寄存器使用，避免修改RA特殊寄存器
- https://github.com/openjdk/jdk/pull/32416 (8390521: RISC-V: Clean up vector register dispatch in MachSpillCopyNode::implementation)  --  为RISC-V重构矢量寄存器SPILL相关代码实现

本期审阅并合入的JDK LTS主线PR:
- https://github.com/openjdk/jdk25u-dev/pull/734 (8390441: RISC-V: Fix C2 stack-to-stack spill copies with large offsets)  --  为RISC-V修复寄存器SPILL大偏移量支持问题
- https://github.com/openjdk/jdk21u-dev/pull/3018 (8390441: RISC-V: Fix C2 stack-to-stack spill copies with large offsets)
- https://github.com/openjdk/jdk17u-dev/pull/4623 (8390441: RISC-V: Fix C2 stack-to-stack spill copies with large offsets)

- https://github.com/openjdk/jdk25u-dev/pull/748 (8390521: RISC-V: Clean up vector register dispatch in MachSpillCopyNode::implementation)  --  为RISC-V重构矢量寄存器SPILL相关代码实现
- https://github.com/openjdk/jdk21u-dev/pull/3040 (8390521: RISC-V: Clean up vector register dispatch in MachSpillCopyNode::implementation)
- https://github.com/openjdk/jdk17u-dev/pull/4643 (8390521: RISC-V: Clean up vector register dispatch in MachSpillCopyNode::implementation)

Java重要新特性JEP 544: AOT静态编译（Ahead-of-Time Code Compilation）RISC-V移植工作进展：

与社区生态伙伴沟通协作，已将JEP 483 and JEP 515特性移植到RISC-V平台并合入JDK主线：
- https://github.com/openjdk/jdk/pull/32311 (8390102: RISC-V: Support AOT Code Cache)  -- JEP 483 and JEP 515特性在RISC-V上的移植
- https://github.com/openjdk/jdk/pull/32592 (8391431: RISC-V: AOTCodeTest.java fails after JDK-8388288 with fastdebug)  -- 为RISC-V相关AOT失败用例修复
- https://github.com/openjdk/jdk/pull/32438 (8390614: RISC-V: Support VerifyOops for AOT caching stub and code)  -- 为RISC-V添加AOT VerifyOops支持
- https://github.com/openjdk/jdk/pull/33081 (8393051: RISC-V: Check SATP mode when loading the AOT code cache)  -- 为RISC-V添加AOT地址模式比对
- https://github.com/openjdk/jdk/pull/32491 (8390914: [leyden] add missing relocations for addresses recorded in AOT code cache)  -- 为RISC-V添加缺失的AOT重定位信息

相关JEP提案：
- https://openjdk.org/jeps/483 (JEP 483: Ahead-of-Time Class Loading & Linking)
- https://openjdk.org/jeps/515 (JEP 515: Ahead-of-Time Method Profiling)

### Go

### QEMU

## 社区动态
**[RuyiSDK邀您一同参与第六届RISC‑V中国峰会，RuyiSDK将带来演讲与海报展示](https://ruyisdk.cn/t/topic/2889)**：RuyiSDK将亮相第六届RISC‑V中国峰会，现场将带来主题演讲以及海报展示，并在开源社区**D15**展位展示多种RuyiSDK应用方案，欢迎各位开发者到场交流。

---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
