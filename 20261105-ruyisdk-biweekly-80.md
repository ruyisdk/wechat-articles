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

本期提出的主线CL:

- 857242: cmd/compile: intrinsify Anduintptr and Oruintptr on riscv64 | https://go-review.googlesource.com/c/go/+/857242 指令化 RISC-V And/Or 指针指令
- 816460: internal/runtime/gc/scan: add RVV impl of filterNil | https://go-review.googlesource.com/c/go/+/816460 使用 RVV 加速 GreenGC 的 filterNil 函数 【合入】
- 844366: runtime: crash the GC at clobberdead pointer on riscv64 | https://go-review.googlesource.com/c/go/+/844366 在 runtime 使能 clobberdead 指令
- 844385: cmd/compile: implement clobberdead mode on riscv64 | https://go-review.googlesource.com/c/go/+/844385 在 RISC-V 平台实现 clobberdead 指令
- 857521: cmd/compile: intrinsify Xchg8 on riscv64 | https://go-review.googlesource.com/c/go/+/857521 在 RISC-V 平台指令化 Xchg8

本期审阅的主线CL:
- 807981: cmd/compile: use OpMove instead of memmove in small-size on riscv64 | https://go-review.googlesource.com/c/go/+/807981 使用OpMove 替代 memmove 函数
- 856701: runtime: fix register use in racecallbackthunk on riscv64 | https://go-review.googlesource.com/c/go/+/856701 修复 racecallback 错误的寄存器分配
- 835325: cmd/compile: intrinsify Anduintptr and Oruintptr on amd64 and riscv64 | https://go-review.googlesource.com/c/go/+/835325 指令化 And/Or 指针指令
- 801684: cmd/compile: use RVV for RISCV64 LoweredZeroLoop | https://go-review.googlesource.com/c/go/+/801684 使用 RVV 加速 LoweredZeroLoop 指令

### QEMU


## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
