# RuyiSDK 双周进展汇报 第 074 期·2026 年 08 月 18 日

## 卷首语

各位 RuyiSDK 的开发者伙伴，大家好！近期，RuyiSDK 在开发者工具、工具链及运行时生态方面的主要进展如下：

开发者工具方面，包管理器近期主要在推进对 macOS 平台的支持和适配，工具链的 macOS 打包工作是近期的推进重点；VSCode 插件迎来了一系列体验优化，新增了工作区信任检测、资源清理命令，并补齐了本地化文本；Eclipse 插件则着重解决了虚拟环境向导的性能问题。

工具链领域，LLVM 持续合入了 P 扩展的多个关键特性，覆盖窄化饱和裁剪、高位乘法及符号/零扩展内建函数等；GCC 方面则积极推进了 SIMD 扩展的工具链落地，并持续维护 RISE Toolchain CI 基础设施。基础 C 库方面，GLIBC 将 expint1、expm1 等数学函数移植至 libmvec 框架，并基于 C920 对 strstr 接口进行了初步调优，newlib 则基于 C908 对 memset 进行了调优。

运行时生态方面，OpenJDK 完成了 JEP 401（值类与对象）在 RISC-V 平台上对三大执行引擎（解释器、C1、C2）的兼容性支持，相关 PR 已提交至 Valhalla 代码仓；Go 运行时继续丰富 RISC-V 后端能力，新增了对 `zvk` 加密指令集与 `vgetrandom` vDSO 的支持；V8 则实现了 FP16 向量降精度/升精度转换、qfma/qfms 快速乘加/乘减等 SIMD 运算，并增加了 ZFH、ZVFH 硬件扩展特性检测能力。

欢迎阅读正文，了解更详尽的更新内容，并期待您与我们一同参与社区共建。获取更多资讯、下载最新工具或参与技术讨论，欢迎通过以下渠道找到我们：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区：[ruyisdk.cn](https://ruyisdk.cn/)
- 工具下载：[官网下载页面](https://ruyisdk.org/downloads)
- GitHub 仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)

下个版本计划于 2026 年 8 月底发布，敬请期待！

## 基础开发环境

### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.52.0 版本预期将在 8 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.51.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* RuyiSDK 工具链的 macOS 打包工作。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新软件包：
  * `board-image/armbian-spacemit-musepipro-minimal`: SpacemiT Muse Pi Pro 的 Armbian。感谢 [SmulllLu][SmulllLu] 的贡献！

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### RuyiSDK VSCode 插件

- board docs: 将 RuyiSDK Examples/开发板文档入口切换至最新站点 boards.ruyisdk.org。
- main: 增加工作区信任检测，在不受信任工作区中阻止构建和虚拟环境激活。
- venv: 根据 profile 所需 quirks 筛选可用工具链，并展示相关需求。
- setup: 新增 ruyi self clean 资源清理命令，支持选择资源并进行危险操作确认。
- venv/packages: 工具链和软件包列表按名称及版本排序。
- packages/UX: 安装软件包时在包树中显示“安装中”状态和动态图标。
- setup/macOS: 支持 macOS 平台自动安装 Ruyi 0.51。
- setup/macOS: 修复 Homebrew 安装的 pipx 未被识别的问题，并增加安装命令回退。
- setup/UX: 安装或更新失败时改为在编辑器中查看错误详情，而不是复制到剪贴板。
- build/i18n: 补齐构建模块缺失的本地化文本，并将构建进度提示接入翻译。
- venv: 创建虚拟环境时仅将实际包含 sysroot 的工具链作为候选。
- packages/i18n: 增加软件包分类名称的本地化显示。

### RuyiSDK Eclipse 插件

- venv & UX: 解决进入虚拟环境向导时的性能问题。
- UX: 整理程序各处的文本以统一命名风格。
- venv: 修改虚拟环境向导的部分设计，使线程间数据流向清晰。

## 基础组件

### 基础C库

- GLIBC:
  - 移植了 expint1、expm1、erfinv 和 erfcinv 至现有的 glibc libmvec 框架。
  - 基于 C920 针对 strstr 接口进行了初步调优。
- newlib:
  - 移植了 acosh 至现有的 newlib 向量数学框架。
  - 基于 C908 针对 memset 接口进行了初步调优。

### GCC

1. 推进 RISC-V SIMD 扩展工具链落地

本周继续推进 SIMD 扩展在 GNU 工具链中的支持，更新了汇编、反汇编相关实现；同时与 SiFive 合作，进一步完善 intrinsics 功能支持和验证。目前工作正在从基础指令支持向编译器接口和完整工具链支持推进。同时继续担任 RISC-V P Extension Task Group Vice-Chair，参与后续规范、工具链及生态协同工作。

- https://github.com/riscv/riscv-p-spec/pull/322
- https://lists.riscv.org/g/tech-p-ext/message/1031

2. 参与 RISC-V Binutils 上游维护

协助审核 Alibaba 提交的 dtrel 符号解析相关 patch，并推动其合入上游。除了自身功能开发之外，继续承担 RISC-V Binutils 社区的 patch review 和上游维护工作。

- https://sourceware.org/git/?p=binutils-gdb.git;a=commit;h=4e8ba93fdb24f9bcf31f706e62e67c57ae91168f

3. 维护 RISE Toolchain CI 基础设施

持续维护 RISE Toolchain CI，支撑 RISC-V GCC/Binutils 上游开发和回归验证。后续会继续结合实际运行情况完善 CI 稳定性和问题跟踪。

- https://github.com/riseproject-dev/gcc-postcommit-ci/pull/3

### LLVM

本期提交 PR 如下

- [RISCV][P-ext] Support Packed Narrowing Clip Pair
  https://github.com/llvm/llvm-project/pull/215779
  补齐 P 扩展 Packed Narrowing Clip Pair，覆盖 Clang、LLVM IR、RISC-V 后端选择及 RV32/RV64 测试。已合并
- [Clang][RISCV] Add packed sign and zero extend intrinsics
  https://github.com/llvm/llvm-project/pull/211487
  增加 packed sign/zero extend（psext/pzext）的 Clang 内建函数、头文件封装及代码生成测试。已合并
- [RISCV][P-ext] Select scalar mulhr/mulhru/mulhrsu for RV32 v2i32
  https://github.com/llvm/llvm-project/pull/215938
  修复 RV32 v2i32 舍入高位乘法选择，将运算拆分为 mulhr、mulhru、mulhrsu 标量指令。已合并
- [RISCV][P-ext] Support Packed Multiply High
  https://github.com/llvm/llvm-project/pull/211223
  增加 P 扩展 Packed Multiply High 的 Clang 内建函数、LLVM IR 和代码生成支持，覆盖 RV32/RV64。已合并
- [RISCV][MC] Add experimental Smcsps and Sscsps support
  https://github.com/llvm/llvm-project/pull/211712
  增加 Smcsps 和 Sscsps 拓展的汇编支持。已合并

### V8

本期提交并合入的patch：

1. **[riscv] Implement FP16 demote and promote SIMD operations for RISC‑V**
   [RISC‑V] 实现FP16向量降精度、升精度SIMD转换运算（https://chromium‑review.googlesource.com/c/8129298）
2. **[riscv]Implement FP16 qfma/qfms SIMD operator**
   [RISC‑V] 实现FP16向量快速乘加/快速乘减(qfma/qfms)SIMD指令（https://chromium‑review.googlesource.com/c/8128824）
3. **[riscv][maglev] Cache the DataView's byteLength for the bounds check**
   [RISC‑V][Maglev] 缓存DataView的字节长度，用于边界检查优化（https://chromium‑review.googlesource.com/c/7129740）
4. **[riscv] Fix F16x8DemoteF64x2Zero register aliasing and tail policy**
   [RISC‑V] 修复F16x8DemoteF64x2Zero存在的寄存器别名冲突以及尾部元素处理策略问题（https://chromium‑review.googlesource.com/c/8136057）
5. **[riscv][wasm‑wide‑arith] Consistently use IsUsed checks on output values**
   [RISC‑V][WASM宽算术] 统一对输出操作数做IsUsed使用状态检测（https://chromium‑review.googlesource.com/c/8222564）
6. **[riscv][regexp]Skip backtrack stack setup for patterns that never backtrack**
   [RISC‑V][正则引擎] 对完全不需要回溯的正则模式，跳过回溯栈初始化（https://chromium‑review.googlesource.com/c/8225557）
7. **[riscv] Add zfh/zvfh detect**
   [RISC‑V] 增加ZFH、ZVFH硬件扩展特性检测能力（https://chromium‑review.googlesource.com/c/8134337）
8. **[riscv][compiler] Unify wasm code‑generator stack checks**
   [RISC‑V][编译器] 统一WASM代码生成器内部的栈溢出检测逻辑（https://chromium‑review.googlesource.com/c/8222565）

本期审阅并合入的patch：

**[riscv] Fix AtomicStoreTaggedPointer and AtomicStore fence order**
[RISC‑V] 修复 `AtomicStoreTaggedPointer` 与 `AtomicStore` 的内存屏障（fence）执行顺序问题
（https://chromium-review.googlesource.com/c/8190694）

### OpenJDK

本期审阅并合入的JDK主线patch:

- https://github.com/openjdk/jdk/pull/31340 (8385702: Improve polymorphic handling in JDK-8385648)  为各CPU平台优化polymorphic相关处理的指令跳转逻辑
- https://github.com/openjdk/jdk/pull/31358 (8384442: Shenandoah: Remove vestigial CAS barrier code)  为各CPU平台清理ShenandoahGC未使用的CAS barrier函数
- https://github.com/openjdk/jdk/pull/31373 (8385915: RISC-V: Remove unused cmpxchg* methods)  为RISC-V平台清理未使用的cmpxchg汇编函数
- https://github.com/openjdk/jdk/pull/31423 (8386161: RISC-V: Auto-enable Zvkn/Zvkg extension features)  为RISC-V平台自动开启Zvkn/Zvkg探测和加解密指令运用（SpaceMit K3平台加解密操作性能实测2-3倍性能加速）
- https://github.com/openjdk/jdk/pull/31434 (8386252: Shenandoah: Polish LRB argument preparation)  为各CPU平台优化LRB参数准备
- https://github.com/openjdk/jdk/pull/31424 (8385323: Support capstone on riscv64)  支持配置构建面向RISC-V平台的capstone反汇编器so文件

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台Java虚拟机的模板解释器、C1、C2 JIT即时编译器三大模块对JEP 401特性的兼容性支持，能够在Server模式下跑通JEP 401相关兼容性测试用例。
同时，JVM相关修改可在RISC-V平台全量通过JDK自带全部回归测试用例。JEP 401兼容性相关工作已经通过PR形式提交到Valhalla代码仓，详细修改见PR链接。
下一步工作：
继续调研JEP 401 Value Class相关的性能优化实现细节，具体包括值类型Flattening支持（UseArrayFlattening & UseFieldFlattening）和方法调用值类型参数传递内联支持（InlineTypePassFieldsAsArgs & InlineTypeReturnedAsFields）。

- https://github.com/openjdk/valhalla/pull/2531 (8386240: [lworld] Port JEP 401 to RISC-V)

### Go

提交代码

- 664155: cmd/asm, cmd/internal/obj: add crypto algorithm suites for riscv64 | https://go-review.googlesource.com/c/go/+/664155 添加zvk 指令集【合入】
- 796060: runtime: enable vgetrandom vDSO support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/796060 加速crypto库【合入】
- 787960: cmd/compile/internal/ssa: optimize multiply-by-constant on riscv64 | https://go-review.googlesource.com/c/go/+/787960 降低常数乘法强度 【合入】
- 816460: internal/runtime/gc/scan: add RVV impl of filterNil. | https://go-review.googlesource.com/c/go/+/816460 新Greantea GC 添加rvv指令

Review

- 807460: cmd/internal/obj/riscv: compress function returns | https://go-review.googlesource.com/c/go/+/807460 添加C扩展的返回指令，对比原有编译器能减少~2700个指令
- 738760: crypto/internal/poly1305: provide optimised assembly for riscv64 | https://go-review.googlesource.com/c/crypto/+/738760 poly1305添加riscv支持 【合入】
- 808080: runtime: clear frame pointer before calling into C on RISCV64 | https://go-review.googlesource.com/c/go/+/808080 清除帧指针【合入】
- 812961: cmd/asm, cmd/internal/obj: support 6-bit VROR.VI immediates | https://go-review.googlesource.com/c/go/+/812961 支持VROR.VI 的 6-bit编码模式
- 806200: internal/cpu: detect RISC-V VLENB when the vector extension is available | https://go-review.googlesource.com/c/sys/+/806200 添加runtime VLENB
- 815840: runtime: fix sigtramp abi in riscv64 mipsx mips64x and s390x | https://go-review.googlesource.com/c/go/+/815840 修复Go ABI 跳过了sigtramp 的save/restore 【合入】

[SmulllLu]: https://github.com/SmulllLu
