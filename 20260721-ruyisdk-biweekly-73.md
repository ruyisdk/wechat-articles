# RuyiSDK 双周进展汇报 第 073 期·2026 年 07 月 21 日

## 卷首语

各位 RuyiSDK 的开发者伙伴，大家好！又见面了，本期是第 73 期双周进展汇报。近两周，RuyiSDK 在开发者工具、工具链及运行时生态方面的主要进展如下：

开发者工具侧，包管理器 0.51.0 与 Eclipse 插件 0.1.6 均已发布。包管理器 0.51.0 新增了禁用默认软件源、支持打包工作者关闭遥测等灵活配置；软件源同步新增了对 SpacemiT K3 Pico-ITX 和 OrangePi RV2 两款设备镜像的支持。Eclipse 插件 0.1.6 则针对虚拟环境交互体验进行了多项改进，欢迎试用和反馈；VSCode 插件本期暂未发版，团队正规划下一轮迭代。

工具链与运行时方面，GCC 已向上游提交了 Ziccid、Ziccamoc、Svrsw60t59b 等多项扩展支持，并完成了 P 扩展到 gcc-16.1 的 Rebase；LLVM 持续合入了大量 P 扩展的 codegen 与 intrinsic 增强；QEMU 的 Packed-SIMD 模拟支持也已提交上游 Review。OpenJDK 的 JEP 401 移植再进一步，RISC-V 平台 C1 JIT 支持已就绪；V8 则在半精度浮点向量扩展上稳步推进。

每一次迭代都离不开社区的反馈与共建。下个版本计划于 8 月底发布，我们将持续演进，带来更多能力。

📢 **特别邀请**：为了帮助我们更好地优化产品，我们准备了一份简短的**用户体验问卷**，恳请您花几分钟时间填写。您的每一条反馈，都是我们前进的方向！
👉 **问卷直达链接**：[RuyiSDK 用户调研问卷](https://docs.qq.com/form/page/DVUxIZURaY2hGRnFL#/fill-detail)

同时，欢迎您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流畅谈，或前往[官网下载页面](https://ruyisdk.org/downloads)下载试用，通过 [GitHub](https://github.com/ruyisdk/) 或 [社区](https://ruyisdk.cn/) 提交您的问题、建议与想法。期待与更多伙伴携手，共同繁荣 RISC-V 软件生态。

## 基础开发环境

### 包管理器

RuyiSDK 0.51 已于 2026 年 7 月 21 日发布，对应的包管理器版本也为 0.51.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 修复了 `ruyi` 在自动补全命令行时无法补出文件路径的问题。
* 本地软件源 Git 元数据损坏时，会输出更友好的错误信息了。
* 修复了非交互终端情况下 `ruyi repo add` 命令的报错信息中 `[repo]` 字样缺失的问题。感谢 [SmulllLu][SmulllLu] 报告此问题！
* 现在可以用 `ruyi repo` 禁用默认软件源（`ruyisdk`）了。感谢 [sisungo][sisungo] 报告此问题！
* 发行版打包工作者可以通过配置的方式完全禁用首次运行上报安装信息的功能和遥测功能了。
* 工程化迭代：
  * 为方便测试工作，允许将 `ruyi` 二进制命名为带版本号的形式了：如 `ruyi-0.51.0`。
  * 更新了依赖版本。
  * 减少了对 `typing_extensions` 的使用。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新软件包：
  * `analyzer/dynamorio-riscv`: DynamoRIO RISC-V 性能分析工具，11.91.20630 版本。
  * `board-util/wlink`: 社区独立实现的 WCH-Link 刷写与调试工具，0.1.2 版本。
  * `source/opencv`: OpenCV 上游源码，4.13.0 版本。感谢 [Tanmay Gulhane][trg-rgb] 的贡献！
  * `toolchain/gnu-ruyisdk`: 由 RuyiSDK 团队维护、构建的 GNU 工具链，0.20260625.0 版本。在 GNU binutils 2.46、GCC 16.1.1、glibc 2.43 的基础上支持了所有 2026 年 6 月前已批准（ratified）的 RISC-V 扩展。
  * `toolchain/llvm-ruyisdk`: 由 RuyiSDK 团队维护、构建的 LLVM 工具链，0.20260625.0 版本。在 LLVM 22.1.8 的基础上支持了所有 2026 年 6 月前已批准（ratified）的 RISC-V 扩展，具体是新增了对 Svrsw60t59b 与 Ziccid 的支持。
* 新增设备支持：
  * SpacemiT K3 Pico-ITX: 兼容各类 Bianbu 镜像。感谢 [weilinfox][weilinfox] 的贡献！
  * OrangePi RV2: 兼容各类 Armbian 镜像。感谢 [SmulllLu][SmulllLu] 的贡献！
* 完善了设备支持：
  * `board-image/armbian-orangepi-rv2-minimal`: OrangePi RV2 的 Armbian。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/armbian-orangepi-rv2-xfce`: OrangePi RV2 的 Armbian，XFCE 桌面。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/armbian-starfive-visionfive2-xfce`: StarFive VisionFive2 的 Armbian，XFCE 桌面。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/armbian-spacemit-musepipro-xfce`: SpacemiT Muse Pi Pro 的 Armbian，XFCE 桌面。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/freebsd-riscv64-mini-live`: FreeBSD Live 镜像。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/openbsd-riscv64-live`: OpenBSD Live 镜像。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/revyos-sipeed-laptop4a:`: Sipeed Laptop 4A 的 RevyOS。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/revyos-sipeed-lcon4a:`: Sipeed LicheePi Console 4A 的 RevyOS。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `board-image/revyos-sipeed-lpi4a:`: Sipeed LicheePi 4A 的 RevyOS。感谢 [SmulllLu][SmulllLu] 的贡献！

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 例行安全更新与依赖更新。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### RuyiSDK VSCode 插件

- 更新软件源时，自动执行 ruyi update
- 删除软件时使用模态框

### RuyiSDK Eclipse 插件

- 项目: 发布 0.1.6 测试版。
- CI: 添加测试版交付流程。
- venv: 在所选工具链不包含 sysroot 时禁用相应的 sysroot 配置选项。
- venv: 调整向导配置页的布局。
- 添加问卷调查弹窗。

### 版本测试及遗留问题

RuyiSDK 包管理器 0.51.0 与 Eclipse 插件 0.1.6 均已完成测试验证并准予发版，详见[测试报告](https://gitee.com/yunxiangluo/ruyisdk-test/tree/master/20260715)。

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 strcasecmp、strcasecmp_l、strncasecmp 和 strncasecmp_l 的通用版本 RVV 优化。
  - 移植了 exp2m1 和 exp2m1f 至现有的 glibc libmvec 框架。
  - 之前提交的 stpncpy 和 strncpy 已经合入 glibc 上游主线。
- newlib:
  - 提交了向量数学库 RFC patch 到 newlib 上游。
  - 提交了 str* 相关共 17 个接口实现的 patch 到 newlib 上游。

### GCC

提交了Ziccid, Ziccamoc, Ssccfg, Smcdeleg, Smctr, Smsdid, Ssctr, Ssqosid， Svrsw60t59b的扩展支持到gcc上游：
https://patchwork.sourceware.org/project/gcc/list/?series=63789&state=%2A&archive=both

Rebase了P扩展的gcc工具链支持到gcc-16.1 release分支，后续等待P扩展草案冻结后向上游同步提交：
https://github.com/ruyisdk/riscv-gcc/tree/p-rebase

### LLVM

本期提交 PR 如下：

1. [Clang][RISCV][P-ext] Support packed widening convert intrinsics
   https://github.com/llvm/llvm-project/pull/208394
   添加 packed widening convert intrinsics 支持
   已合并
2. [RISCV] Add packed narrowing convert intrinsics
   https://github.com/llvm/llvm-project/pull/210389
   添加 packed narrowing convert intrinsics 支持
   已合并
3. [RISCV][P-ext] Support packed reverse intrinsics
   https://github.com/llvm/llvm-project/pull/207574
   支持 packed reverse intrinsics
   已合并
4. [RISCV][P-ext] Improve codegen for packed reverse intrinsics
   https://github.com/llvm/llvm-project/pull/207575
   优化 packed reverse intrinsics codegen
   已合并
5. [RISCV][P-ext] Add codegen for packed absolute difference sum
   https://github.com/llvm/llvm-project/pull/207314
   添加 packed absolute difference sum codegen 支持
   已合并
6. [RISCV][P-ext] Fold packed insert-into-zero to zero-extend
   https://github.com/llvm/llvm-project/pull/208006
   将特定的 32-bit packed vector 插入零向量操作折叠为 `zext`
   已合并
7. [RISCV][P-ext] Add packed saturating rounding shift codegen
   https://github.com/llvm/llvm-project/pull/208630
   添加 packed saturating rounding shift codegen 支持
   已合并
8. [RISCV][P-ext] Improve RV64 v2i16 reverse codegen
   https://github.com/llvm/llvm-project/pull/208664
   优化 RV64 上 v2i16 reverse codegen
   已合并
9. [Clang][RISCV] Add P extension reinterpret cast intrinsics
   https://github.com/llvm/llvm-project/pull/210241
   添加 P 扩展 reinterpret cast intrinsics
   已合并
10. [RISCV][P-ext] Support Packed Saturating Absolute Value.
    https://github.com/llvm/llvm-project/pull/207978
    添加 Packed Saturating Absolute Value intrinsic 支持
    已合并
11. [RISCV][P-ext] Support Packed Narrowing Zip
    https://github.com/llvm/llvm-project/pull/210040
    添加 Packed Narrowing Zip intrinsic 支持
    已合并
12. [Clang][P-ext] Support packed zip/unzip intrinsics
    https://github.com/llvm/llvm-project/pull/208245
    添加 packed zip/unzip intrinsics 支持
    已合并
13. [RISCV][P-ext] Improve the codegen for pzip
    https://github.com/llvm/llvm-project/pull/208479
    优化 pzip codegen
    已合并
14. [RISCV][P-ext] Improve the codegen for unzip-like shuffle and buildvector
    https://github.com/llvm/llvm-project/pull/208763
    优化特定 unzip 类 shuffle 和 buildvector 代码生成
    已合并
15. [RISCV][P-ext] Generalize lowerVECTOR_SHUFFLEAsRV32PNarrowingShift
    https://github.com/llvm/llvm-project/pull/210522
    泛化 `lowerVECTOR_SHUFFLEAsRV32PNarrowingShift`
    已合并
16. [InstCombine] Treat `uitofp nneg` as non-negative signed range for fcmp clamp folds
    https://github.com/llvm/llvm-project/pull/208234
    让 InstCombine 将 `uitofp nneg` 的输入按非负有符号整数范围处理，从而折叠 `fcmp` 钳位及端点比较
    正在 review
17. [ValueTracking][InstCombine] Preserve samesign when flipping icmp strictness
    https://github.com/llvm/llvm-project/pull/209097
    在将非严格整数比较规范化为严格比较时保留 `samesign` 标志，同时避免常量调整跨越溢出或符号边界
    正在 review
18. [InstCombine] Use samesign constraints in unsigned known-bits folds
    https://github.com/llvm/llvm-project/pull/209675
    在无符号比较的 known-bits 折叠中传播 `samesign` 的符号位约束，从而支持更多整数范围端点折叠
    正在 review
19. [RISCV][P-ext] Add packed sign and zero extend intrinsics
    https://github.com/llvm/llvm-project/pull/208685
    添加 packed sign and zero extend intrinsics
    正在 review

### V8

本期提交patch如下：

1. **[riscv][wasm][debug] Fix OSR safepoint mismatch in Liftoff**
   [RISC-V][WASM][调试] 修复 Liftoff 中 OSR 安全点不匹配问题（https://chromium-review.googlesource.com/c/8071149）
2. **[maglev][riscv] Fix SmiSubConstant overflow false positive under pointer compression**
   [Maglev][RISC-V] 修复指针压缩场景下 SmiSubConstant 溢出误报断言（https://chromium-review.googlesource.com/c/8074004）
3. **[wasm][riscv] Add SwitchSimulatorStackLimit in WasmHandleStackOverflow**
   [WASM][RISC-V] 在栈溢出处理函数 WasmHandleStackOverflow 中添加模拟器栈边界切换逻辑（https://chromium-review.googlesource.com/c/8049967）
4. **[riscv][wasm-wide-arith] fix incorrect DCHECK in VisitWideAddSub**
   [RISC-V][WASM宽算术] 修复 VisitWideAddSub 内错误的调试断言（https://chromium-review.googlesource.com/c/8084001）
5. **[riscv][regexp]Skip the JS stack guard check for register-light patterns**
   [RISC-V][正则引擎] 对寄存器轻量正则模式跳过 JS 栈保护校验（https://chromium-review.googlesource.com/c/8089969）
6. **[riscv] Implement F16x8/I16x8 vector conversions**
   [RISC-V] 实现 F16x8 与 I16x8 向量类型转换指令（https://chromium-review.googlesource.com/c/8095784）
7. **[riscv] Fix undeclared identifier 'kWRegSize'**
   [RISC-V] 修复标识符 kWRegSize 未声明编译错误（https://chromium-review.googlesource.com/c/8097963）

### OpenJDK

本期提交的OpenJDK Valhalla仓patch:

- https://github.com/openjdk/valhalla/pull/2542 (8386618: [lworld] Remove unused entry_guard_Relocation)  清除未使用的entry_guard重定位类型，ARM64和RISC-V平台已不再使用该重定位
- https://github.com/openjdk/valhalla/pull/2544 (8386626: [lworld] Only enable valhalla IR tests in ScalarReplacementWithGCBarrierTests.java for aarch64 and x86)  完善值类与对象相关测试用例，考虑其它CPU平台

本期审阅并合入的JDK主线patch:

- https://github.com/openjdk/jdk/pull/31106 (8384223: RISC-V: entry_barrier_offset should consider UseZtso)  为RISC-V平台修复Ztso场景C2 JIT方法entry_barrier偏移计算问题
- https://github.com/openjdk/jdk/pull/31140 (8366041: Shenandoah: Late Barrier Expansion)  为各CPU平台优化Shenandoah GC barrier展开时机，提高C2 JIT编译速度并改进JIT代码效率
- https://github.com/openjdk/jdk/pull/31246 (8384404: RISC-V: Do less implicit narrowing conversions)  为RISC-V平台修复数据类型转换潜在风险
- https://github.com/openjdk/jdk/pull/29703 (8376602: [Vector API] Upgrade SLEEF from 3.6.1 to 3.9.0)  同步并导入最新版SLEEF开源库，提高各CPU平台VectorAPI程序执行性能
- https://github.com/openjdk/jdk/pull/31310 (8385583: RISC-V: Debugger very slow during stepping)  为RISC-V平台修复特定场景java调试器单步执行速度慢的缺陷
- https://github.com/openjdk/jdk/pull/31351 (8385835: Shenandoah: Polish C2 pre/post barrier signatures)  为各CPU平台清理Shenandoah GC barrier相关汇编函数签名

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台C1 JIT编译器对JEP 401的支持，能够在Client模式（包括解释器、C1 JIT两种执行模式）下跑通JEP 401相关测试用例，通过兼容性测试。
目前已着手调试和实现RISC-V平台C2 JIT模块对JEP 401的支持，优先解决兼容性问题，短期目标能够在Server模式下跑通JEP 401新增测试用例。
本期详细修改如下：

- https://github.com/openjdk/valhalla/commit/b44b312e0fee4a841943cd5188bf567476aa8678
- https://github.com/openjdk/valhalla/commit/0cc2013eca9dd26a1600f813c11707f1e04465d5
- https://github.com/openjdk/valhalla/commit/371d26340c91a75ae8304ba06d8ef68763973a48
- https://github.com/openjdk/valhalla/commit/8faa89ca92e4270cc4e689c904cbe182be184775

### Go

提交代码

- 801460: runtime: add msan support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/801460 添加msan支持
- 802100: runtime, internal/fuzz: add libFuzzer support on riscv64 | https://go-review.googlesource.com/c/go/+/802100 添加 fuzz 支持
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 cgo 信号支持【合入】

Review

- 801681: runtime, internal/cpu: detect RISC-V vector extension and VLEN | https://go-review.googlesource.com/c/go/+/801681 支持 RISC-V RVV VLEN 长度动态侦测
- 796820: cmd/internal/obj/riscv: document rva23u64 feature macros | https://go-review.googlesource.com/c/go/+/796820 文档支持 【合入】
- 801683: runtime: save RISC-V vector registers state during async preemption | https://go-review.googlesource.com/c/go/+/801683 抢占过程中保存 RVV 寄存器状态 （已经影响部分images/的向量优化）
- 801360: test/codegen: add riscv64 checks for conditional subtractions | https://go-review.googlesource.com/c/go/+/801360 添加codegen 检查（目前 zkt 才有const time能力，大概率拒收）

### QEMU模拟器

实现RISC-V Packed-SIMD扩展的QEMU模拟器支持，提交至上游，Review中。

https://lists.nongnu.org/archive/html/qemu-riscv/2026-07/msg00697.html

[sisungo]: https://github.com/sisungo
[SmulllLu]: https://github.com/SmulllLu
[trg-rgb]: https://github.com/trg-rgb
[weilinfox]: https://github.com/weilinfox
