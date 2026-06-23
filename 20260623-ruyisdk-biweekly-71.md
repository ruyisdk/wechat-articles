# RuyiSDK 双周进展汇报 第 071 期·2026 年 06 月 23 日

## 卷首语

端午刚过，夏至已至。过去两周，RuyiSDK 迎来了多项亮点进展。

运行时方面，V8 开始支持 RISC-V ZFH 半精度浮点扩展，适配 Wasm FP16 特性以加速计算；OpenJDK 的 JEP 401（值类与对象）移植取得突破，已完成解释器与 JIT 模块解耦，成功构建 Server 模式二进制。

工具链方面，GCC 提交多项草案扩展实现，并协助 compiler-explorer 社区完善 RVA23 支持；GLIBC 在玄铁 C908 平台完成 memcpy 特定优化。

开发者工具方面，包管理器 0.50.0 将于本周发布，新增包大小展示、macOS 初步适配及解压模块底层重构。Eclipse 插件 0.1.4 通过测试正式发布，欢迎大家下载体验。


更多进展细节详见下方各板块，欢迎试用并在 GitHub 或社区中反馈建议，期待更多伙伴一起共建 RISC‑V 软件开发生态。

⏬ 包管理器和IDE插件工具都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.49.0🚀

  * 从 [PyPI](https://pypi.org/project/ruyi/0.49.0/) 安装：`pip install ruyi`
  * 手动下载安装：
    * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.49.0)
    * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.49.0/)
  * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

  > [!NOTE]
  > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
  > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
  > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
  >
  > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。对于 `ruyi` 的单文件二进制发行版，您必须将下载的文件重命名为一字不差的 `ruyi` 才能正常使用。
  >
  > 请注意：从 RuyiSDK 0.48.0 开始，Ubuntu 22.04 LTS 与 Python 3.10 环境不再受到支持。相关用户，尤其是发行版打包者、CI 环境维护者与仍在使用旧版 Python 运行环境的用户，在升级前请提前确认兼容性影响并完成验证。
  >
  
* RuyiSDK VSCode Extension 0.1.4 🚀

  * VSCode/VSCodium Extensions 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
  * 手动下载安装 (Install from VSIX):
    * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.4/)
    * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
  * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.4 🚀

  * 在线安装方式: Eclipse IDE → Help → Install New Software... → Add...  →  Location: https://ruyisdk.github.io/ruyisdk-eclipse-plugins/
  * 手动下载安装：
    * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.3/)
    * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
  * [使用文档](https://ruyisdk.org/docs/IDE/)

  > [!NOTE]
  > 近期 Eclipse Marketplace 中的 RuyiSDK 插件查询与安装出现异常，详情可参考[【RuyiSDK Eclipse 插件安装方式临时调整通知】](https://ruyisdk.cn/t/topic/2696)，建议您通过 Eclipse 的 Install New Software… 方式安装插件。
  >

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 7 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 基础开发环境

### 包管理器

RuyiSDK 0.50 将于 2026 年 6 月 23 日至 6 月 26 日之间发布，对应的包管理器版本也为 0.50.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* `ruyi list` 会展示本地未安装的软件包在当前架构的下载大小了。
* 对于记载了相应元数据的软件包，`ruyi list` 会展示这些软件包的安装后大小了。
* 工程化迭代：
    * 为 macOS 做了最初的部分适配工作。
    * 切换到了 Python 来解压缩文件，移除了 `gunzip`、`bzip2`、`lz4`、`xz`、`zstd` 这些外部命令依赖。
    * 简化了资源文件的捆绑方式。
    * 切换到了新的 ruyi-pytest 外部集成测试套件，替代原有的 ruyi-litester。
    * 更新了依赖版本。
    * 更新了平台基线依赖版本信息的文档。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 软件源格式更新：
    * 支持了给软件包附着更多元数据，当前支持记录 `binary` 类型软件包在每个架构的安装后大小。
* 新增设备支持：
    * SpacemiT MUSE Pi Pro: 兼容各类 Bianbu 镜像。
* 新增了以下软件包：
    * `board-image/bianbu-desktop-lite-uefi-spacemit-k1`: Bianbu Desktop Lite 的 UEFI 引导版本，适用于 SpacemiT K1 平台。
    * `board-image/bianbu-desktop-lite-uefi-spacemit-k1-sd`: Bianbu Desktop Lite 的 UEFI 引导版本，适用于使用 SD 卡存储的 SpacemiT K1 平台。
* 更新了以下软件到最新版本：
    * `board-image/bianbu-desktop-spacemit-k1`: 更新到了 v2.3.3。
    * `board-image/bianbu-desktop-lite-spacemit-k1`: 更新到了 v2.3.3。
    * `board-image/bianbu-minimal-spacemit-k1`: 更新到了 v2.3.3。
    * `board-image/bianbu-desktop-spacemit-k1-sd`: 更新到了 v2.3.3。
    * `board-image/bianbu-desktop-lite-spacemit-k1-sd`: 更新到了 v2.3.3。
    * `board-image/bianbu-minimal-spacemit-k1-sd`: 更新到了 v2.3.3。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 例行安全更新与依赖更新。
* 支持了查询 RuyiSDK Eclipse 与 VSCode 插件最新版本的 API。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### RuyiSDK VSCode 插件

- 支持阅读本地已缓存的新闻
- 支持 Ruyi 包管理器 0.49 版本 --project-sysroot-from-rootfs 选项

### RuyiSDK Eclipse 插件

- venv: 初步支持一键添加使用 qemu-user 的启动和调试配置。
- venv: 提供默认的 venv 名称并默认选择唯一打开的项目。
- venv: 修复使用 ruyi 创建虚拟环境时错误传递的命令行参数。

### 版本测试及遗留问题

Eclipse 插件计划发版测试期间 <https://api.ruyisdk.cn/releases/latest-pm> 500 故障，待测功能无法验证，故相关测试延后了一周。

重新开展测试后发版的 Eclipse 插件测试[报告](https://github.com/ruyisdk-test/ruyisdk-eclipse-plugins-test/tree/v0.1.4-1)。

遗留缺陷：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [命令执行提示框可以任意关闭且无法重新打开 #82](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/82)   | 建议 |   |
| [虚拟环境建立的项目绑定问题 #84](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/84) | 建议 |  |
| [安装插件时 Eclipse 提示未签名 #85](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/85) | 建议 |  |
| [有一些可以自动获取的东西，不需要手动填写 #90](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/90) | 建议 |  |
| [UI：新闻界面切换仅未读“勾号”不明显 #98](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/98) | 建议 |  |
| [ruyi-venv中的vnev path需要手动点击右侧列表，显示项目路径 #152](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/152) | 建议 |  |
| [ruyi-venv名称可以默认设置为ruyi-venv-profile属性 #153](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/153) | 建议 |  |

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 strncasecmp 和 strstr 的通用版本 RVV 优化。
  - 在阿里玄铁 C908 平台尝试完成了一版基于 RVV 和 xthead 标量访问扩展的 memcpy 平台特定优化。

### GCC

- 添加 RISC-V Profiles 支持到工具链 --with-arch 选项，用于构建默认支持特定 profile 的工具链，已提 PR 至 riscv-gnu-toolchain 仓库：

  https://github.com/riscv-collab/riscv-gnu-toolchain/pull/1869
  
- 提交了 Zvzip 与 Zvdota/Zvbdota 等 RISC-V 草案扩展的 GNU 工具链支持实现。其中，Zvzip 主要面向向量数据重排、打包/解包等场景；Zvdota/Zvbdota 面向点积与批量点积运算，可支撑 AI 推理/训练、DSP、GEMM/Conv 等核心算子的性能优化。

  - zvzip: https://patchwork.sourceware.org/project/gcc/list/?series=62161&archive=both
  - zvdota: https://github.com/ruyisdk/riscv-gcc/tree/zvdota
  - 相关介绍：https://github.com/pz9115/riscv-toolchain-notes/blob/main/talks/2026-riscv-zvdota-zvbdota-introduction/README.md

- 完成并提交 Ziccid 扩展的工具链基础支持，包括扩展识别、依赖解析和架构属性传播:

  https://github.com/ruyisdk/riscv-gcc/tree/ziccid

- 协助 compiler-explorer 社区完善了 Binutils 的 trunk 分支，适配了 RVA23 Profile 支持。

  - https://github.com/compiler-explorer/compiler-explorer/pull/8827
  - 示例：https://godbolt.org/z/h49rYT3To

- 协助 RISE-Developer-Infrastructure 工作组开始进行工具链 CI 模块的维护更新，更新了 GCC CI 模块，添加了 gcc-16 CI 部分，移除了 gcc-14 的相关检测

  https://github.com/riseproject-dev/gcc-postcommit-ci/pull/1
  
### LLVM

- [RISCV][LLVM][Clang] Add experimental Zvvm config intrinsics
https://github.com/llvm/llvm-project/pull/203774
添加 Zvvm config 相关 intrinsics 支持
正在 review

- [RISCV][P-ext] Merge paired pli/plui in RISCVMoveMerger
https://github.com/llvm/llvm-project/pull/202566
在 RISCVMoveMerger 里合并成对的 pli/plui 指令到 pli.d*/plui.d*
已合并

- [Clang][RISCV] packed comparison intrinsics
https://github.com/llvm/llvm-project/pull/203191
添加 P 拓展向量比较相关 intrinsic 支持。包括 pmseq/pmsne/pmslt[u]/pmsgt[u]/pmsge[u]/pmsle[u]
已合并

- [RISCV][P-ext] packed exchanged add/sub codegen
https://github.com/llvm/llvm-project/pull/203473
添加  packed exchanged add/sub 的 codegen 支持
正在 review

- [RISCV][P-ext] Support Packed Averaging Addition and Subtraction
添加Packed Averaging Add/Sub 的 intrinsic 支持
已合并

- [RISCV][P-ext] Support Packed Absolute Value and Absolute Difference
添加 Packed Absolute Value and Absolute Difference 的 intrinsic 支持
已合并

### V8
**本期亮点：开始支持 RISCV  ZFH 扩展，适配 Wasm FP16 特性，可以应用于加速半精度浮点计算。**

本期提交并合入的 patch：
1. **[riscv][codegen] Fix slot calculation for move cycle resolution** [RISC-V][代码生成] 修复寄存器移动循环解析的槽位计算错误（https://chromium-review.googlesource.com/c/7911096）
2. **[riscv] Fix error that use of undeclared identifier** [RISC-V] 修复使用未声明标识符引发的编译错误（https://chromium-review.googlesource.com/c/7908311）
3. **[riscv] Fix Debug check failed: !L->is_bound()** [RISC-V] 修复调试断言 !L->is_bound() 触发失败问题（https://chromium-review.googlesource.com/c/7917370）
4. **[riscv][acqrel] Add acquire-release support for atomic.fence** [RISC-V][内存序] 为原子屏障指令 atomic.fence 提供获取-释放内存序支持（https://chromium-review.googlesource.com/c/7947903）
5. **[riscv]Implement ZFH in Simulator** [RISC-V] 在模拟器中实现 ZFH 半精度浮点扩展指令集（https://chromium-review.googlesource.com/c/7897892）
6. **[riscv] Implement CompareSmiAndAssert** [RISC-V] 实现 CompareSmiAndAssert 校验辅助逻辑（https://chromium-review.googlesource.com/c/7953184）
7. **[riscv][debug] Move DebugInfo to trusted space** [RISC-V][调试] 将调试信息存放至可信内存区域（https://chromium-review.googlesource.com/c/7953185）
8. **[riscv] Implement vfadd/vfsub/vfmul/vfdiv for fp16** [RISC-V] 实现半精度浮点向量四则运算指令 vfadd/vfsub/vfmul/vfdiv（https://chromium-review.googlesource.com/c/7953190）

### OpenJDK

本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30732 (8382199: Remove unused parameter "dst" from CardTableBarrierSetAssembler::store_check())  为X86和ARM64平台汇编函数移除非必要的dst参数
- https://github.com/openjdk/jdk25u-dev/pull/541 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台回合Shenandoah GC一处load_reference_barrier调用对象错误问题修复

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30704 (8382039: Add support do_arch_array_entry() template)  为各CPU平台重构Stub调用入口声明
- https://github.com/openjdk/jdk/pull/30759 (8382315: RISC-V: TestMultiplyReductionByte.java fails with guarantee(is_uimm5(imm)) failed: uimm is invalid)  为RISC-V平台修复一处大矢量宽度场景滑窗指令立即数范围超标问题
- https://github.com/openjdk/jdk/pull/30780 (8382393: Enable VectorStoreMaskIdentityTest.java IR tests for RISC-V)   为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30823 (8382522: Disable stringop-overflow in safepointMechanism.cpp)  为RISC-V平台修复一处GCC编译器构建JDK报警问题
- https://github.com/openjdk/jdk/pull/30864 (8382690: aarch64: Clean up redundant restore_locals() in TemplateTable::invokeinterface)  为ARM64和RISC-V平台移除一处模板解释器接口函数调用场景非必要的locals变量恢复操作，提升性能

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
目前已完成RISC-V平台模板解释器、C1& C2 JIT模块的代码全解耦，能够构建和运行支持Server模式RISC-V JDK二进制。
同时，已着手调试和实现RISC-V平台模板解释器模块对JEP 401的支持，优先考虑兼容性问题，短期目标能够在解释模式下跑通JEP 401新增测试用例。
本期详细修改如下：
- https://github.com/openjdk/valhalla/commit/44cf8f556b2b6f0178452e1c35d2e501fec23745 
- https://github.com/openjdk/valhalla/commit/323d7868ad0e810a44f9fdfa4bf16fc92450dd45 
- https://github.com/openjdk/valhalla/commit/b44b312e0fee4a841943cd5188bf567476aa8678 
- https://github.com/openjdk/valhalla/commit/6bde9f57f679377e6e850c78fdd37c46067bd4ba 

### Go

本期提交主线的CL：

- 790080: cmd/compile: support zba extensions for riscv64 | https://go-review.googlesource.com/c/go/+/790080 添加ZBA SSA 支持
- 789520: cmd/compile: support zbs extensions for riscv64 | https://go-review.googlesource.com/c/go/+/789520 添加ZBS SSA 支持

本期审阅并提出修改意见CL：

- 580276: cmd/compile: support Zba extensions in riscv64 compiler | https://go-review.googlesource.com/c/go/+/580276 沟通后关闭无法进行的CL，移除RVA23合入障碍
- 579797: cmd/compile: support Zbs extensions in riscv64 compiler | https://go-review.googlesource.com/c/go/+/579797 沟通后关闭无法进行的CL，移除RVA23合入障碍
- 616095: test/codegen: add tests for combined shift and zero extension on riscv64 | https://go-review.googlesource.com/c/go/+/616095 添加zero extend 位移测试
- 717980: runtime, cmd/internal/obj/riscv: support spin lock on riscv64 | https://go-review.googlesource.com/c/go/+/717980 要求移除跟随ABIInternal
- 732700: cmd/internal/obj/riscv: add assembly support of Zfa extension | https://go-review.googlesource.com/c/go/+/732700 添加ZFA 支持

