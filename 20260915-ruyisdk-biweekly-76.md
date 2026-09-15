# RuyiSDK 双周进展汇报 第 076 期 · 2026 年 09 月 15 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵

- 更新 HiFive Premier P550 的 Debian 中英文测试报告。[PR #393](https://github.com/ruyisdk/support-matrix/pull/393)
- 更新 Milk-V Duo S 的 Arch Linux、Debian、RT-Thread、RT-Thread Smart 和 Ubuntu 24.04 中英文测试报告。[PR #394](https://github.com/ruyisdk/support-matrix/pull/394)、[PR #395](https://github.com/ruyisdk/support-matrix/pull/395)、[PR #396](https://github.com/ruyisdk/support-matrix/pull/396)、[PR #397](https://github.com/ruyisdk/support-matrix/pull/397)、[PR #398](https://github.com/ruyisdk/support-matrix/pull/398)
- 新增 SpacemiT K3 CoM260 Kit 的 Buildroot 中英文测试报告。[PR #399](https://github.com/ruyisdk/support-matrix/pull/399)

### 开发板示例仓库

- 统一 SpaceMIT 厂商名称在开发板元数据及中英文索引中的拼写。[PR #43](https://github.com/ruyisdk/board-docs/pull/43)
- 为 K3 Pico-ITX 新增 ROS 2 课程入口和第一章课程元数据，并将课程文档来源切换至 GitHub 镜像。[PR #44](https://github.com/ruyisdk/board-docs/pull/44)、[PR #45](https://github.com/ruyisdk/board-docs/pull/45)
- 开发板文档前端新增 ROS 2 课程页面及中英文访问路由，并优化课程列表和课程正文的移动端显示。[PR #9](https://github.com/DuoQilai/board-docs-frontend/pull/9)、[PR #10](https://github.com/DuoQilai/board-docs-frontend/pull/10)

### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 log10, log10f, log10p1, log10p1f, log1p, log1pf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 atan2pi, exp2, cbrt, cospi, exp10, log2p1 至现有的 newlib 向量数学框架。

### GCC

- 提交了 Sspmp 扩展的工具链支持，已合入 Binutils 上游：
  - https://sourceware.org/git/?p=binutils-gdb.git;a=commit;h=b16f10037c4814ab03416a4ab143337591881e2b
- 补充了 P 扩展的 Binutils 指令别名支持，，修复了 intrinsics api 测试中发现的一些问题
  - https://github.com/ruyisdk/riscv-gcc/commits/p-rebase/
  - https://github.com/ruyisdk/riscv-binutils/commit/cf8cab68b5addd773e86619f974c9dbbf91cc37a
- RISE-CI 的维护 PR 通过了会议审核，已经正式合入 RISE-CI 上游代码中
  - https://github.com/riseproject-dev/gcc-postcommit-ci/pull/4
  - https://github.com/riseproject-dev/gcc-precommit-ci/pull/1
  - https://github.com/riseproject-dev/riscv-gnu-toolchain-ci/pull/1

### LLVM

本期提交 PR 如下

- [RISCV][SLP] Use common alignment when checking constant-stride loads
  https://github.com/llvm/llvm-project/pull/222520
  修复 SLP 常量步长加载合法性检查中的对齐判断，使用 `CommonAlignment`，避免将 32 位加载扩宽为未对齐的 64 位 RVV 访问而触发 `SIGBUS`。已合并
- [RISCV][SLP] Precommit strided-load alignment tests (NFC)
  https://github.com/llvm/llvm-project/pull/222863
  补充 RV32/RV64 下 SLP 步长加载对齐测试，覆盖相邻加载组对齐不同及严格对齐场景，为后续合法性修复提供回归测试。已合并
- [RISCV] Support Packed Multiplication with Horizontal Addition
  https://github.com/llvm/llvm-project/pull/218430
  实现 packed multiplication with horizontal addition 的 Clang、LLVM intrinsic、后端选择及 RV32/RV64 测试。上期正在 review，本期已合并
- [InstCombine] Fold `uitofp nneg` comparisons above the signed maximum
  https://github.com/llvm/llvm-project/pull/221118
  在浮点比较折叠中将 `uitofp nneg` 的上界收紧为有符号整数最大值，简化超出其有效范围的比较。正在 review
- [RISCV][P-ext] Add packed multiply-parts accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/222571
  为 LLVM 和 Clang 实现 RISC-V P 扩展的 packed multiply-parts accumulate 系列 intrinsic，并添加相应的指令选择支持。已合并
- [RISCV][P-ext] Fold an add of a multiply-parts product into the accumulate form
  https://github.com/llvm/llvm-project/pull/222748
  将 multiply-parts 乘积与加法组合折叠为累加形式，使 `mul.hXX` 加 `add` 的序列生成单条 `macc.hXX` 指令。已合并
- [RISCV][P-ext] Support Packed Element Extract
  https://github.com/llvm/llvm-project/pull/221565
  为 RISC-V P 扩展新增 Packed Element Extract intrinsic 支持。已合并
- [RISCV][MC]Fix encoding for psati.dw/dh
  https://github.com/llvm/llvm-project/pull/221889
  修正 `psati.dw` 和 `psati.dh` 的立即数编码，使饱和位宽分别按 `uimm5+1` 和 `uimm4+1` 解释。已合并
- [RISCV] Disable shrink wrapping for SiFive CLIC and QCI handlers
  https://github.com/llvm/llvm-project/pull/218347
  禁用 SiFive CLIC 和 QCI 中断处理函数的 shrink wrapping 优化。已合并
- [RISCV]Support Sspmp, Sspmpen and Smpmpdeleg Extensions
  https://github.com/llvm/llvm-project/pull/207696
  新增 Sspmp、Sspmpen 和 Smpmpdeleg 扩展支持。已合并
- [RISCV] Add MC support for FCVT.H.Q and FCVT.Q.H
  https://github.com/llvm/llvm-project/pull/220176
  添加 `FCVT.H.Q` 和 `FCVT.Q.H` 两条浮点转换指令的 MC 支持。已合并
- [Clang][RISCV] Add packed widening add accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/221622
  为 RISC-V P 扩展新增 packed widening add accumulate intrinsic 支持，并完善 RV32/RV64 CodeGen 覆盖。正在 review
- [RISCV][P-ext] Support Packed Element Insert
  https://github.com/llvm/llvm-project/pull/222268
  为 RISC-V P 扩展新增 Packed Element Insert intrinsic 支持。正在 review

此外，向 RISC-V P 扩展规范仓库 `riscv/riscv-p-spec` 提交了以下修正：

- Rename `__riscv_pm2wadd{,a}su_u64` to `_i64`
  https://github.com/riscv/riscv-p-spec/pull/361
  将 `__riscv_pm2wadd{,a}su_u64` 重命名为 `_i64` 后缀，使 intrinsic 命名与有符号返回类型一致。已合并
- Take an unsigned rs1 in `__riscv_sshl_u32`/`__riscv_sshlr_u32`
  https://github.com/riscv/riscv-p-spec/pull/362
  将 `__riscv_sshl_u32` 和 `__riscv_sshlr_u32` 的 `rs1` 参数改为无符号类型，修正规范中的参数类型错误。已合并

### V8
本期修复了若干bug，提升了RISC-V V8的稳定性，提交并合入的patch如下：
1. **[riscv64] Zero-extend JSDispatchHandle before computing table offsets**
   [RISC-V] 在计算表偏移前对JSDispatchHandle做零扩展 [CL8342529](https://chromium-review.googlesource.com/c/8342529)
2. **[riscv][maglev] Keep Word32 values sign-extended in all producers**
   [RISC-V][Maglev] 在所有生成节点保持Word32数值带符号扩展 [CL8335670](https://chromium-review.googlesource.com/c/8335670)
3. **[riscv] Use or instead of add for decompression**
   [RISC-V] 使用OR指令替代ADD完成解压缩运算 [CL8334087](https://chromium-review.googlesource.com/c/8334087)
4. **[riscv] Sign-extend operands of 32-bit compares in Select**
   [RISC-V] 在Select节点对32位比较操作数做符号扩展 [CL8342851](https://chromium-review.googlesource.com/c/8342851)
5. **[riscv] Sign-extend AMO.W results in simulator**
   [RISC-V] 在模拟器中对AMO.W原子操作结果进行符号扩展 [CL8350097](https://chromium-review.googlesource.com/c/8350097)
6. **[riscv] Fix unordered FP comparison and emit at the consumer**
   [RISC-V] 修复无序浮点数比较逻辑，在消费端生成指令 [CL8360836](https://chromium-review.googlesource.com/c/8360836)
7. **[riscv] Fix input constraint in BuiltinStringFromCharCode::SetValueLocationConstraints()**
   [RISC-V] 修复BuiltinStringFromCharCode::SetValueLocationConstraints()中的输入寄存器约束 [CL8349148](https://chromium-review.googlesource.com/c/8349148)
8. **[riscv][wasm] Fix Liftoff sub-word atomic RMW**
   [RISC-V][WASM] 修复Liftoff中半字粒度原子读改写(RMW)操作 [CL8378121](https://chromium-review.googlesource.com/c/8378121)
9. **[riscv] Preserve vector registers in PushCallerSaved**
   [RISC-V] 在PushCallerSaved函数中保留向量寄存器 [CL8395546](https://chromium-review.googlesource.com/c/8395546)

### OpenJDK

本期审阅并合入的JDK主线PR:
- https://github.com/openjdk/jdk/pull/31853 (8388035: RISC-V: Auto-enable Zfa extension features)  -- 为RISC-V添加Zfa扩展的自动探测和使能
- https://github.com/openjdk/jdk/pull/31862 (8388075: RISC-V: Auto-enable Zvbc extension features)  -- 为RISC-V添加Zvbc扩展的自动探测和使能
- https://github.com/openjdk/jdk/pull/31934 (8388399: RISC-V: Enable vector FP16 conversions with Zvfhmin)  -- 为RISC-V添加Zvfhmin半精度浮点矢量转换支持
- https://github.com/openjdk/jdk/pull/31958 (8388459: RISC-V: Add specialized CMove patterns with zero operand)  -- 为RISC-V优化零操作数场景条件Move优化
- https://github.com/openjdk/jdk/pull/31880 (8321012: RISC-V: C2 ExtractUB)  -- 为RISC-V添加矢量无符号字节元素提取优化

本期审阅并合入的JDK-updates PRs:
- https://github.com/openjdk/jdk25u-dev/pull/653 (8387381: RISC-V: assert failed with fastdebug build on systems with different core types)  -- 为RISC-V修复异构CPU探测断言错误
- https://github.com/openjdk/jdk17u-dev/pull/4407 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  -- 为RISC-V修复ShenandoahGC Barrier调用对象错误

Java重要新特性JEP 544: AOT静态编译（Ahead-of-Time Code Compilation）RISC-V移植工作进展：
已初步开展调研工作 (https://openjdk.org/jeps/401)，先通过在X86/ARM64平台调试，逐步熟悉和了解该特性的设计思路和代码实现细节，为后续将该特性移植到RISC-V平台做好准备。
JEP 544提案在X86/ARM64平台详细实现：
- https://github.com/openjdk/jdk/pull/30778 (8380476: Implement JEP 544: Ahead-of-Time Code Compilation)

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
