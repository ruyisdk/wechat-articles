# RuyiSDK 双周进展汇报 第 077 期 · 2026 年 09 月 24 日

## 卷首语

各位 RISC-V 开发者与 RuyiSDK 社区伙伴，大家好！

中秋与国庆双节临近，首先祝福每一位社区伙伴中秋团圆、国庆愉快！也感谢每一位伙伴一直以来对 RuyiSDK 社区的关注与贡献。
由于假期安排，本期双周进展提前与大家相见，RuyiSDK 各板块继续稳步推进。

基础开发环境方面，RuyiSDK 包管理器 0.53 已发布，新增二进制包 ABI 兼容性检测与报告基础设施，并修复了默认软件源优先级、下载失败回退以及多源同名同版本软件包安装状态同步等问题，跨平台稳定性进一步提升；RuyiSDK IDE 在本期围绕软件包排序、安装进度展示、虚拟工作区检测、工作区安全限制等方向持续打磨，同时补充了跨平台 CI 构建测试。

社区与内容建设方面，packages-index 清理了上游不再提供的 Armbian 软件版本，开发板支持矩阵新增 HiFive Premier P550、SpacemiT K3 CoM260 Kit 等多款板卡的中英文测试报告，开发板示例仓库同步补充了对应板卡文档与 HelloWorld、CoreMark 示例，官网与文档侧新增 Ruyi Imager 使用说明。

基础组件方面，GLIBC 与 newlib 持续推进向量数学函数移植，GCC 完成 SpacemiT 厂商扩展向 16.2 分支的 backport，LLVM 在 RISC-V P 扩展、RVA23.1/RVB23.1 profile、MC 校验等方向合入多项 PR，V8 通过优化 Word32 相等/不等比较使 AOT 内置库静态代码尺寸降低 2.7%，OpenJDK、Go、QEMU 也分别在 G1 GC 优化、矢量运算支持、RVV 性能优化与 Packed SIMD 扩展等方向取得进展。

社区动态方面，RuyiAI 携 RuyiSDK 亮相 2026 云栖大会如意社区展台，与参会开发者进行了深入交流。

欢迎阅读正文，了解更详尽的更新内容，并期待您与我们一同参与社区共建。

获取更多资讯、下载最新工具或参与技术讨论，欢迎通过文章最下方的渠道找到我们。

下个版本计划于 2026 年 10 月底发布，敬请期待！

## 基础开发环境


### 包管理器

RuyiSDK 0.53 将于 2026 年 9 月 24 日发布，对应的包管理器版本也为 0.53.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 新增了检测与报告二进制包 ABI 兼容性的基础设施，这将有助于判断某个二进制分发的软件在您的系统上是否能正常工作。
* 修复了无法为默认软件源 `ruyisdk` 设置优先级的问题。感谢 [sisungo][sisungo] 报告此问题！
* 修复了某个下载成功返回了失败页面时，不会接着尝试其他下载链接的问题。感谢 [weilinfox][weilinfox] 报告此问题！
* 修复了多个软件源存在同名、同版本软件包时，安装状态与来源软件源失去同步的问题。感谢 [qingwan12138][qingwan12138] 报告此问题！
* 工程化迭代：
  * 更新了依赖版本。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

[qingwan12138]: https://github.com/qingwan12138
[sisungo]: https://github.com/sisungo
[weilinfox]: https://github.com/weilinfox

### RuyiSDK IDE

### 新功能

- 侧边栏图标改为透明样式。
- 支持基于语义化版本号的比较对软件包、工具链进行排序。
- 软件包树视图的搜索提示更加醒目。
- 安装软件包时显示详细的进度信息。
- 支持检测虚拟工作区。
- 软件包详情中新增 slug 信息，同时从软件包标签中移除 slug。
- 运行本地化同步工具（sync-l10n）时自动重新生成 bundles。
- 修复工具链选择与 sysroot 选择行为不一致的问题。
- 修复仓库管理操作后软件包树未重新加载的问题。
- 修复软件包树视图的本地化问题。
- 清理资源后软件包树视图会自动刷新。
- 采用 esbuild 打包，消除打包警告。
- 在不受信任的工作区中禁止执行构建操作，提升工作区安全性。
- 删除虚拟环境时校验删除目标，并停用对应环境别名。
- 安装、更新 ruyi 前提示用户需要安装 "python3"、"python3-pip" 等软件包以使用 pip 或 pipx。
- 测试由 CI 构建的跨平台的 IDE。

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新软件包：
  * `board-image/armbian-*`: 删除了上游不再提供的软件版本。感谢 [weilinfox][weilinfox] 的贡献！

您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### 开发板支持矩阵

- 新增 HiFive Premier P550 的 Fedora 44 Server 中英文测试报告。[PR #400](https://github.com/ruyisdk/support-matrix/pull/400)
- 新增 SpacemiT K3 CoM260 Kit 的 Bianbu 4.0.6、OpenHarmony 6.1 中英文测试报告，并补充 openEuler 24.03-LTS-SP4 中英文待测文档。[PR #401](https://github.com/ruyisdk/support-matrix/pull/401)、[PR #402](https://github.com/ruyisdk/support-matrix/pull/402)、[PR #403](https://github.com/ruyisdk/support-matrix/pull/403)
- 更新 CH32V307 的 RT-Thread 5.3.1 中英文测试报告。[PR #404](https://github.com/ruyisdk/support-matrix/pull/404)
- 更新 Milk-V Duo S 的 Zephyr 4.1.99 中英文测试报告。[PR #405](https://github.com/ruyisdk/support-matrix/pull/405)

### 开发板示例仓库

- 新增 HiFive Premier P550 中英文板卡文档及 HelloWorld、CoreMark 示例。[PR #46](https://github.com/ruyisdk/board-docs/pull/46)
- 新增 SpacemiT K3 CoM260 Kit 中英文板卡文档和 HelloWorld 示例，补充中文 CoreMark 示例及 ROS 2 前两章课程入口。[PR #47](https://github.com/ruyisdk/board-docs/pull/47)
- 开发板文档前端新增课程前后章节导航，并在首页展示最新课程章节预览。[PR #11](https://github.com/DuoQilai/board-docs-frontend/pull/11)

### 官网&文档
- 新增 Ruyi Imager 使用文档，为图形化镜像烧录工具补充了使用说明，已在 docs 仓库合入（[docs#149](https://github.com/ruyisdk/docs/pull/149)）；官网侧同步更新正在评审中（[ruyisdk-website#589](https://github.com/ruyisdk/ruyisdk-website/pull/589)），合入后即可在官网查阅。

## 基础组件


### 基础C库

- GLIBC:
  - 移植了 pow 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 rsqrt, expm1 至现有的 newlib 向量数学框架。

### GCC

- 本周 backport 了 Spacemit 厂商自定义扩展到 ruyisdk gcc 16.2 分支
  https://github.com/ruyisdk/riscv-gcc/tree/16.2

- 修复了 packed slide intrinsic lowering 的问题
  https://github.com/riscv/riscv-p-spec/pull/369

- 协助 review 了 tail pseudo 的寄存器选择处理支持
  https://sourceware.org/pipermail/binutils/2026-September/151491.html

### LLVM

本期提交 PR 如下

- [Clang][RISCV] Add packed widening add accumulate intrinsics
  https://github.com/llvm/llvm-project/pull/221622
  为 RISC-V P 扩展新增 packed widening add accumulate intrinsic 支持，并完善 RV32/RV64 CodeGen 覆盖。上期正在 review，本期已合并
- [RISCV][P-ext] Support Packed Element Insert
  https://github.com/llvm/llvm-project/pull/222268
  为 RISC-V P 扩展新增 Packed Element Insert intrinsic 支持。上期正在 review，本期已合并
- [Clang][RISCV] Add scalar saturating add/sub, absolute value and rev intrinsics
  https://github.com/llvm/llvm-project/pull/224377
  为 RISC-V P 扩展新增第一批 Scalar Intrinsics，支持标量饱和加减、绝对值和位反转操作。已合并
- [Clang][RISCV] Add packed subvector extract intrinsics
  https://github.com/llvm/llvm-project/pull/224429
  为 RISC-V P 扩展新增 packed subvector extract intrinsics，支持从 64 位 packed vector 中提取 32 位子向量。已合并
- [RISCV] Add OPERAND_UIMM4_PLUS1 to RISCVInstrInfo::verifyInstruction
  https://github.com/llvm/llvm-project/pull/224423
  在 `RISCVInstrInfo::verifyInstruction` 中补充 `psati.h` 和 `psati.dh` 使用的 `OPERAND_UIMM4_PLUS1` 校验，解决相关崩溃。已合并
- [RISCV][P-ext] Support Packed Load
  https://github.com/llvm/llvm-project/pull/223313
  为 RISC-V P 扩展新增 Packed Load intrinsic 支持。已合并
- [RISCV][P-ext] Support Packed Store
  https://github.com/llvm/llvm-project/pull/223619
  为 RISC-V P 扩展新增 Packed Store intrinsic 支持。已合并
- [RISCV][P-ext] Support Packed Element Join
  https://github.com/llvm/llvm-project/pull/223931
  为 RISC-V P 扩展新增 Packed Element Join intrinsic 支持。已合并
- [RISCV]Add RVA23.1 and RVB23.1 experimental profiles
  https://github.com/llvm/llvm-project/pull/217199
  新增 RVA23.1 和 RVB23.1 实验性 profile 支持。已合并
- [RISCV][MC] Require H for HINVAL instructions
  https://github.com/llvm/llvm-project/pull/223588
  修正 `HINVAL.VVMA` 和 `HINVAL.GVMA` 指令的扩展依赖，要求启用 H 扩展。已合并
- [MC][RISCV] Make Zve32x a dependency of Zvabd
  https://github.com/llvm/llvm-project/pull/223901
  在 MC 实现中补充 Zvabd 对 Zve32x 的扩展依赖。已合并
- [RISCV] Fix immediate operand ranges for XCVsimd instructions
  https://github.com/llvm/llvm-project/pull/224876
  修正 XCVsimd 指令的立即数操作数范围。已合并
- [RISCV][MC] Reject invalid combined immediates for `cv.insert`
  https://github.com/llvm/llvm-project/pull/224985
  为 `cv.insert` 补充组合立即数约束检查，拒绝不满足 `Is3 + Is2 < 32` 的操作数。已合并
- [RISCV][P-ext] Add packed saturation intrinsics
  https://github.com/llvm/llvm-project/pull/224432
  为 RISC-V P 扩展新增 packed saturation intrinsics 支持。正在 review
- [RISCV][P-ext] Support Packed Multiply High Parts
  https://github.com/llvm/llvm-project/pull/225015
  为 RISC-V P 扩展新增 Packed Multiply High Parts intrinsic 支持。正在 review

### V8
本期亮点：对Word32Equal，Word32NotEqual IR的代码生成进行了优化，优化后，提前编译（AOT）的内置库静态代码尺寸降低了2.7%。

本期提交并合入的patch：
1. **[riscv][sandbox] Remove kDefaultCodeEntrypointTag, pt.1**
   [RISC-V][沙箱] 移除 kDefaultCodeEntrypointTag（第一部分）[CL8400460](https://chromium-review.googlesource.com/c/8400460)
2. **[riscv][wasm-wide-arith] optimize nested 128 bit additions**
   [RISC-V][Wasm 宽位算术] 优化嵌套128位加法 [CL8404059](https://chromium-review.googlesource.com/c/8404059)
3. **[riscv] Fix 32-bit add/sub overflow check with dirty upper bits**
   [RISC-V] 修复高位脏数据场景下32位加减溢出检查 [CL8411269](https://chromium-review.googlesource.com/c/8411269)
4. **[riscv] Handle kProjection in ZeroExtendsWord32ToWord64NoPhis**
   [RISC-V] 在 ZeroExtendsWord32ToWord64NoPhis 中处理 kProjection [CL8413986](https://chromium-review.googlesource.com/c/8413986)
5. **[riscv][wasm] Fix safepoints in huge-frame stack check**
   [RISC-V][Wasm] 修复超大栈帧栈检查中的安全点 [CL8424461](https://chromium-review.googlesource.com/c/8424461)
6. **[riscv][wasm] Remove the trap_on_null bit/NullDereference memory access mode**
   [RISC-V][Wasm] 移除 trap_on_null 标记与空解引用内存访问模式 [CL8417701](https://chromium-review.googlesource.com/c/8417701)
7. **[riscv][wasm-wide-arith] optimize nested 128 bit additions**
   [RISC-V][Wasm 宽位算术] 优化嵌套128位加法 [CL8411268](https://chromium-review.googlesource.com/c/8411268)
8. **[riscv][wasm-wide-arith] Fix incorrect carry in Add128**
   [RISC-V][Wasm 宽位算术] 修复 Add128 进位错误 [CL8411517](https://chromium-review.googlesource.com/c/8411517)
9. **[riscv][compiler] Optimize Word32 equality/inequality comparisons**
   [RISC-V][编译器] 优化 Word32 相等/不等比较 [CL8414493](https://chromium-review.googlesource.com/c/8414493)
10. **[riscv] Fix ZeroExtendsWord32ToWord64NoPhis for atomic loads**
    [RISC-V] 修复原子加载场景下 ZeroExtendsWord32ToWord64NoPhis 逻辑 [CL8414976](https://chromium-review.googlesource.com/c/8414976)
11. **[riscv] Optimize tagged comparison branches with subw**
    [RISC-V] 使用 subw 优化带标记值的比较分支 [CL8411262](https://chromium-review.googlesource.com/c/8411262)
12. **[riscv] Fix Word32And zero test with dirty upper bits**
    [RISC-V] 修复高位脏数据下 Word32And 判零逻辑 [CL8403122](https://chromium-review.googlesource.com/c/8403122)
13. **[riscv] Fix register constraint field layout after AccessMode shrink**
    [RISC-V] 修复 AccessMode 缩减后的寄存器约束字段布局 [CL8431981](https://chromium-review.googlesource.com/c/8431981)

本期审阅并合入的patch：
1. **[riscv] Fix register clobbering for atomic compare-exchange**
   [RISC-V] 修复原子比较交换的寄存器覆盖问题 [CL8411976](https://chromium-review.googlesource.com/c/8411976)
2. **[riscv] Avoid clobbering expect value in atomic compare-exchange**
   [RISC-V] 避免原子比较交换中覆盖预期值 [CL8319928](https://chromium-review.googlesource.com/c/8319928)
3. **[riscv][maglev] Use public Float64Min/Max helpers**
   [RISC-V][Maglev] 使用公开的 Float64Min/Max 辅助函数 [CL8397048](https://chromium-review.googlesource.com/c/8397048)

### OpenJDK

本期审阅并合入的JDK主线PR:
- https://github.com/openjdk/jdk27u/pull/84 (8391041: RISC-V: Fix out-of-bounds read in string_indexof_char intrinsic)  -- 为RISC-V修复string_indexof_char intrinsic越界访问风险
- https://github.com/openjdk/jdk/pull/32020 (8388837: RISC-V: Track card addresses directly in G1 array post-write barrier loop)  -- 为RISC-V优化G1GC数组post-write barrier汇编
- https://github.com/openjdk/jdk/pull/32043 (8388474: RISC-V: Relax satp mode check for sv57)  -- 尝试为RISC-V添加SV57寻址空间，风险待确认
- https://github.com/openjdk/jdk/pull/31956 (8388458: RISC-V: Optimize G1 post-write barrier conditional card mark)  -- 为RISC-V优化G1GC数组post-write barrier寻址
- https://github.com/openjdk/jdk/pull/32076 (8389312: RISC-V: vector_update_crc32 wrongly assumes undisturbed tail elements)  -- 为RISC-V修复矢量CRC32计算场景矢量格式设置问题
- https://github.com/openjdk/jdk/pull/32162 (8389581: RISC-V: building fails with clang toolchain)  -- 为RISC-V修复clang构建编译错误问题
- https://github.com/openjdk/jdk/pull/31961 (8388460: RISC-V: Auto-enable Zcb extension features)  -- 为RISC-V打开Zcb扩展，提升性能
- https://github.com/openjdk/jdk/pull/32192 (8389677: RISC-V: Prefer vmv.v.i to zero vector registers)  -- 为RISC-V优化矢量寄存器清零操作，提升性能
- https://github.com/openjdk/jdk/pull/32290 (8390101: RISC-V: Use vmandn.mm for vector mask and-not)  -- 为RISC-V添加掩码矢量与运算优化，提升性能
- https://github.com/openjdk/jdk/pull/32289 (8390044: RISC-V: Support vector integer division)  -- 为RISC-V添加整型矢量除法运算支持
- https://github.com/openjdk/jdk/pull/32387 (8390441: RISC-V: Fix C2 stack-to-stack spill copies with large offsets)  -- 为RISC-V修复大堆栈场景矢量寄存器spill操作问题

Java重要新特性JEP 544: AOT静态编译（Ahead-of-Time Code Compilation）RISC-V移植工作进展：
通过在X86/ARM64平台调试，现已逐步熟悉和了解JEP 544特性的设计思路和代码实现细节。
同时与OpenJDK社区生态伙伴沟通协作，下一步优先将JEP 483 and JEP 515特性移植到RISC-V平台。

- https://openjdk.org/jeps/483 (JEP 483: Ahead-of-Time Class Loading & Linking)
- https://openjdk.org/jeps/515 (JEP 515: Ahead-of-Time Method Profiling)

### Go

本期提出的主线CL:

- 711075: chacha20: improve performance for riscv64 by rvv | https://go-review.googlesource.com/c/crypto/+/711075 chacha20 算法针对 RVV 优化【本周期重新测试性能数据】
- 804504: vector: add RVV SIMD assembly for riscv64 (opt-in) | https://go-review.googlesource.com/c/image/+/804504 image 库针对 RVV 进行 vector 优化

本期审阅的主线CL:

- 807461: cmd/internal/obj/riscv: compress jumps with known immediates | https://go-review.googlesource.com/c/go/+/807461 针对可压缩跳转立即数开启C扩展
- 805300: cmd/internal/obj/riscv: use compressed branch instructions | https://go-review.googlesource.com/c/go/+/805300 针对跳转指令开启C扩展
- 821221: cmd/compile: use BEXT/BEXTI for bit tests on riscv64 | https://go-review.googlesource.com/c/go/+/821221 开启 SSA 优化 BEXT/BEXTI
- 825685: cmd/compile: use BSET/BSETI for single bit set on riscv64 | https://go-review.googlesource.com/c/go/+/825685 开启 SSA 优化 BSET/BSETI
- 835465: cmd/compile: add riscv64 math rounding intrinsics | https://go-review.googlesource.com/c/go/+/835465 开启 SSA 优化浮点取整指令
- 835905: cmd/compile: use runtime Zbb dispatch for riscv64 TrailingZeros | https://go-review.googlesource.com/c/go/+/835905 runtime 针对 Zbb 开启短路径

### QEMU

本期向上游提交Packed SIMD扩展V3版Patch，增加了tcg测试：
https://lists.nongnu.org/archive/html/qemu-riscv/2026-09/msg00523.html

## 社区动态
[RuyiSDK 亮相 2026 云栖大会如意社区展台，展示 RISC-V 开发生态能力](https://ruyisdk.cn/t/topic/2849)：RuyiSDK 携多款 RISC-V 开发相关成果亮相云栖大会如意社区展台，现场展示一体化集成开发环境与软硬件资源共建成果，和参会开发者交流 RISC-V 生态进展。

---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
