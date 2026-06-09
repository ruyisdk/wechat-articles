# RuyiSDK 双周进展汇报 第 070 期·2026 年 06 月 09 日

## 卷首语

各位 RuyiSDK 的开发者伙伴，大家好！

过去两周，RuyiSDK 团队持续推进各核心组件的优化与新特性落地。

**工具链方面**，基础 C 库的 RVV 优化持续合入上游主线（GLIBC 与 newlib），GCC 完成了 Zibi 扩展实现及多个草案扩展的支持，LLVM 围绕 P 扩展密集提交了十余项改进与修复。

**运行时环境**方面，V8 持续完善 RISC-V 后端支持，本期合入多项 WASM 相关修复与优化；OpenJDK 在主线推进多项代码重构与风险修复，同时 JEP 401（值类与对象）的移植工作取得阶段性突破，已完成模板解释器的代码解耦。

**开发者工具**体验同步提升：RuyiSDK 包管理器已进入 Debian sid 官方源；VSCode 插件新增开发板文档入口与完整中英文国际化支持，已正式发布0.1.4 版本，欢迎大家下载使用；Eclipse 插件完成多项界面与逻辑优化。

感谢社区贡献者 [@RevySR][@RevySR] 对 Debian 打包工作的支持。RuyiSDK 将持续保持开放迭代，欢迎更多开发者参与共建。

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
* RuyiSDK Eclipse Plugins 0.1.4

  * 在线安装方式: Eclipse IDE → Help → Install New Software... → Add...  →  Location: https://ruyisdk.github.io/ruyisdk-eclipse-plugins/
  * 手动下载安装：
    * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.3/)
    * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
  * [使用文档](https://ruyisdk.org/docs/IDE/)

  > [!NOTE]
  > 近期 Eclipse Marketplace 中的 RuyiSDK 插件查询与安装出现异常，详情可参考[【RuyiSDK Eclipse 插件安装方式临时调整通知】](https://ruyisdk.cn/t/topic/2696)，建议您通过 Eclipse 的 Install New Software… 方式安装插件。
  >

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 6 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 基础开发环境

### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.50.0 版本预期将在 6 月 23 日正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.49.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* 简化资源文件的捆绑方式，以配合 Debian 对源码包的格式要求。Debian sid 用户可以通过 `apt install ruyi` 安装发行版打包的 ruyi 了。感谢 [@RevySR][@RevySR] 的贡献！
* 支持展示软件包的下载大小。
* 支持为软件包关联更丰富的元数据，包括但不限于解压缩后体积、发行版兼容性等。
* 迁移至测试团队新开发的集成测试套件 ruyi-pytest，替换旧的、不再维护的 ruyi-litester 套件。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### RuyiSDK VSCode 插件

- 新增：在 RuyiSDK Home 页面新增 board 文档入口，一键直达开发板相关文档，查阅资料更便捷
- 新增：完整的国际化（i18n）框架，插件界面现已支持中英文双语切换
- 新增：中文翻译，覆盖所有核心功能模块，方便国内开发者无障碍使用
- 新增：为虚拟环境的 sysroot 添加额外包选择框，创建虚拟环境时可按需选择附加软件包，环境配置更加灵活
- 新增：新闻内容支持中英文翻译，方便全球开发者阅读
- 新增：新闻页面动画效果，交互更加流畅生动
- 重构：重新设计新闻页面 UI，视觉体验大幅提升
- 修复：一键编译功能中识别 CMake 项目的错误，编译流程更稳定可靠

### RuyiSDK Eclipse 插件

- ruyi: 修复有关 RuyiSDK 元数据更新结果的判断逻辑与提示信息。
- ruyi: 修复和简化对已安装 ruyi 包管理器的检查逻辑。
- 界面: 添加有关 ruyi 包管理器版本更新的提示信息。
- 界面: 调整各视图在 Eclipse IDE C/C++ 布局下的初始位置，调整 RuyiSDK.cn 网站视图的启动方式。
- 界面: 整理菜单并对各条目妥善分组。

### 版本测试及遗留问题

- VSCode 插件 [v0.1.4 测试报告](https://github.com/ruyisdk-test/ruyisdk-vscode-extension-test/tree/v0.1.4)。遗留缺陷如下：

| 缺陷                                                                                                                    | 问题等级 | 备注            |
| ----------------------------------------------------------------------------------------------------------------------- | -------- | --------------- |
| [i18中文翻译问题 #156](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/156)                                     | 建议     | 已有修复 commit |
| [ruyinews界面卡片特效缩放异常 #157](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/157)                        | 建议     |                 |
| [新闻中英文按钮大小不一致 #160](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/160)                            | 建议     |                 |
| [i18n中文支持情况 #161](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/161)                                    | 建议     | 已有修复 commit |
| [ruyi-venv创建过程时default默认情况下sysroot配置消失 #162](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/162) | 严重     | 已有修复 commit |

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 rawmemchr, strcasecmp 和 mempcpy 的通用版本 RVV 优化。
  - 先前提交到 GLIBC 上游的 memccpy, memchr, memcmp, strchr, strrchr 的通用版本 RVV 优化已合入主线（https://patchwork.sourceware.org/project/glibc/list/?series=57340&state=*）。
- newlib:
  - 先前提交到 newlib 上游的 mempcpy, memrchr, memchr, memccpy 的通用版本 RVV 优化已合入主线（https://sourceware.org/pipermail/newlib/2026/022437.html）。
  - 先前提交到 newlib 上游的 rawmemchr, memcmp 接口的通用版本 RVV 优化，reviewer 提出了修改意见，已完成相关修正。
  - 移植了 acosh 到当前的 newlib 向量数学库框架。

### GCC

- 分析了 bne/beq immediate 支持，完成了Zibi扩展的GCC实现
- 基于 riscv-isa-manual PR #2369，在Ruyisdk GCC / Binutils工具链上支持Zvbc32e / Zvkgs草案
- 完成特权指令扩展Smmtt的第一子扩展Smsdid支持，已更新至Ruyisdk Binutils，正在实现第二子扩展Smmpt部分

### LLVM

- [RISCV][MC] Support experimental Zvdota Family instructions
  https://github.com/llvm/llvm-project/pull/195069 已合并
- [RISCV][P-ext] Split v4i16/v8i8 MUL on RV32.
  https://github.com/llvm/llvm-project/pull/199504
  在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的乘法（按寄存器对拆成两半计算）。
  已合并
- [RISCV][P-ext] Fold bitcast of v4i8/v2i16 const splat to scalar on RV64
  https://github.com/llvm/llvm-project/pull/199513
  在 RV64 上把 v4i8/v2i16 常量 splat 的 bitcast 折叠为标量常量。
- [RISCV][P-ext] Split v4i16/v8i8 INSERT/EXTRACT_VECTOR_ELT on RV32.
  https://github.com/llvm/llvm-project/pull/199917
  在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的元素插入/提取（INSERT/EXTRACT_VECTOR_ELT）。
- [RISCV][P-ext] packed shift-add codegen
  https://github.com/llvm/llvm-project/pull/201294
  实现 P 扩展 packed shift-add codegen。
- [RISCV][P-ext] Select scalar asub/asubu and mulhr/mulhru/mulhrsu on RV32
  https://github.com/llvm/llvm-project/pull/201540
  在 RV32 上为标量 asub/asubu 与 mulhr/mulhru/mulhrsu 指令添加指令选择。
- Fix RV32 instruction sequence for exchanged add/sub i32x2 intrinsics
  https://github.com/riscv/riscv-p-spec/pull/293
  修正 i32x2 交换式加减（p*_x 系列 intrinsic） intrinsic 文档中的 RV32 指令序列。
- RV32 fallback: scalar instructions for 64-bit packed multiply intrinsics
  https://github.com/riscv/riscv-p-spec/pull/295
  把 64-bit packed multiply intrinsic 在 RV32 上回退改为正确的标量 .h 指令
- RV32 fallback: widening wmul/wmacc for 64-bit multiply-parts intrinsics
  https://github.com/riscv/riscv-p-spec/pull/296
  把返回 int64 的 multiply-parts intrinsic 在 RV32 上回退改为单条加宽指令 wmul/wmacc
- Fix typos in 64-bit Q-format multiply-accumulate intrinsics
  https://github.com/riscv/riscv-p-spec/pull/297
  修正 64 位 Q-format 乘累加 intrinsic 的 typo

### V8

本期提交并合入的patch：

1. **[riscv]Follow established InstructionCode layout for LoadTrustedPointer**
   [RISC-V] 参照现有指令码格式规范实现 LoadTrustedPointer（https://chromium-review.googlesource.com/c/7870730）
2. **[riscv][wasm] Support FP comparison condition in ArchSelect**
   [RISC-V][WASM] 在 ArchSelect 中支持浮点比较条件（https://chromium-review.googlesource.com/c/7870950）
3. **[riscv]Reland [turboshaft] Introduce MemoryRepresentation for LoadTrustedPointer Port commit 8a885ed63641d4b0bfb4d8d9aaddc21104614b35**
   [RISC-V] 重提「[Turboshaft] 为 LoadTrustedPointer 引入内存表示」，移植对应代码提交（https://chromium-review.googlesource.com/c/7878121）
4. **[riscv] Support i16 in liftoff**
   [RISC-V] 在 Liftoff 中增加 i16 类型支持（https://chromium-review.googlesource.com/c/7882462）
5. **[riscv]Add SmiUntagUnsigned helpers and adjust maglev debug condition**
   [RISC-V] 新增 SmiUntagUnsigned 辅助函数，并调整 Maglev 调试判断逻辑（https://chromium-review.googlesource.com/c/7888915）
6. **[riscv] Use unsigned comparison in JSToWasmWrapperHelper**
   [RISC-V] 在 JSToWasmWrapperHelper 中改用无符号数比较（https://chromium-review.googlesource.com/c/7884915）
7. **[riscv] Disable float16 due to RVV don't support Zvfh now.**
   [RISC-V] 因当前 RVV 暂未支持 Zvfh 扩展，禁用 float16 相关功能（https://chromium-review.googlesource.com/c/7889597）
8. **[riscv][wasmfx] Avoid code cache lookup on suspend**
   [RISC-V][WasmFX] 线程挂起时跳过代码缓存查找操作（https://chromium-review.googlesource.com/c/7901154）

### OpenJDK

本期审阅并合入的JDK主线patch:

- https://github.com/openjdk/jdk/pull/30562 (8381611: RISC-V: Factor out function cmpptr from MacroAssembler)  为RISC-V汇编器重构代码，移除非必要的cmpptr汇编函数，改善代码可读性
- https://github.com/openjdk/jdk/pull/30598 (8381724: RISC-V: Pass temp registers and use them in CardTableBarrierSetAssembler::store_check())  为RISC-V汇编函数store_check传递额外的临时寄存器
- https://github.com/openjdk/jdk/pull/30491 (8380163: Fix implicit conversion in macroAssembler_aarch64.hpp)  为ARM64修复一处隐式数据类型转换潜在风险
- https://github.com/openjdk/jdk/pull/30616 (8381677: Remove dependence of UseSHA on UseSHAIntrinsics)  为各CPU后端清理UseSHA / UseSHAIntrinsics选项设置
- https://github.com/openjdk/jdk/pull/30646 (8381926: Fix implicit conversion in macroAssembler_riscv.hpp)  为RISC-V修复一处隐式数据类型转换潜在风险

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
通过阅读JEP 401规范文档和调试对比X86/ARM64相关代码，已初步了解该特性的设计思路，并开始着手实现CPU平台一侧代码的解耦。
目前已完成模板解释器模块的代码解耦，并能够构建支持解释执行模式RISC-V JDK二进制，下一步考虑C1& C2 JIT模块的代码解耦。
详细修改见如下链接：

- https://github.com/openjdk/valhalla/commit/dd306a5978bb081e842a607b175d9cda7bff1b7f
- https://github.com/openjdk/valhalla/commit/519e69b4882121823d5b66ce1da496d74c1989d5
- https://github.com/openjdk/valhalla/commit/d1d65189cae1a40b16a8f4136a42147271180459
- https://github.com/openjdk/valhalla/commit/ef493a94d3706fa5a8dcafe587b5f6a5616a74bc
- https://github.com/openjdk/valhalla/commit/1a32a6e292f8efa4ae79ac352684ee5b3027c305

### Go

本期提交主线的CL：

- 788080: cmd/compile/internal/ssa: limit zbb to rva22u64 for riscv64 | https://go-review.googlesource.com/c/go/+/788080 修复原有ZBB 优化无视profile
- 787960: cmd/compile/internal/ssa: optimize multiply-by-constant on riscv64 | https://go-review.googlesource.com/c/go/+/787960 通过ZBB 优化常数乘法
- 787280: test/codegen: add riscv64 check for divmod | https://go-review.googlesource.com/c/go/+/787280 添加divmod的代码生成检查

本期审阅并提出修改意见CL：

- 781080: cmd/compile/internal: add intrinsic rule for sync atomic and/or 32/64 on RISCV64 | https://go-review.googlesource.com/c/go/+/781080 添加atomic32/64操作支持
- 738760: crypto/internal/poly1305: provide optimised assembly for riscv64 | https://go-review.googlesource.com/c/crypto/+/738760 优化poly1305标量汇编实现
- 787420: runtime: check RISC-V ISA profile at runtime init | https://go-review.googlesource.com/c/go/+/787420 runtime时期检查profile
- 787401: internal/bytealg: improve Count/CountString for riscv64 | https://go-review.googlesource.com/c/go/+/787401 优化标量count实现

[@RevySR]: https://github.com/RevySR
