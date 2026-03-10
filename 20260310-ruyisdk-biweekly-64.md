# RuyiSDK 双周进展汇报 第 064 期·2026 年 03 月 10 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！
 
本期包管理器集成了香山编译器（执行`ruyi update` 后再使用 `ruyi install xscc` 安装即可）；VSCode 插件上架 [Open VSX](https://open-vsx.org/extension/RuyiSDK/ruyisdk-vscode-extension) ，您可以在主流 Linux 发行版（包括 openKylin、Deepin、Ubuntu（非官方版）、Fedora、Debian、openEuler 等）和 VSCodium 等兼容 VS Code 扩展 API 的编辑器、IDE 和开发平台中安装使用 RuyiSDK VSCode 插件。


⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.46.0
    * 从 [PyPI](https://pypi.org/project/ruyi/0.46.0/) 安装：`pip install ruyi`
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.46.0)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.46.0/)
    * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

    > [!NOTE]
    > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
    > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
    > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
    >
    > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

* RuyiSDK VSCode Extension 0.1.2🚀
    * VSCode/VSCodium Extensions 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装 (Install from VSIX):
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
    * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.2
    * Eclipse Marketplace 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
    * [使用文档](https://ruyisdk.org/docs/IDE/)

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479 

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 3 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.47.0 版本预期将在 3 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.46.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增软件包：
    * `toolchain/xscc`: XSCC 编译器，由香山编译器（计算所与开芯院联合）团队提供。此软件包仅支持 `x86_64` 架构。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权限的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

- 多版本管理对不受支持的Ruyi包管理器版本添加outdated标记
- 上架 [Open VSX](https://open-vsx.org/extension/RuyiSDK/ruyisdk-vscode-extension)
- 发布 0.1.2 版本！

### Eclipse 插件

- 重写项目中英文文档。
- 支持在内置的终端内执行 ruyi device provision 程序。
- 引入 Maven Wrapper 管理 Maven 并更新相关配置。
- 引入 PMD 对代码做静态分析，移除未使用的函数和变量。

## GCC

- 更新了Binutils版本到2.46 release
- Rebase了Svrsw60t59b和Zibi扩展的Binutils实现.

## LLVM

- [IA][RISCV] Make the isDeInterleaveMask check the contents of shuffle
 https://github.com/llvm/llvm-project/pull/185384
- [InstCombine] make foldBinOpIntoSelectOrPhi fold on all operands
 https://github.com/llvm/llvm-project/pull/183692

## V8
本期亮点：
下文提到的第5项代码提交，将JSToWasmInterpreterWrapper迁移至Torque语言， 统一了V8内置组件的开发范式。这意味着如意V8团队作为RISC-V架构维护者不再仅局限于“适配移植”层面，而是开始深度跟进并参与到V8核心主体功能（WASM解释器核心逻辑）的架构改进与原生实现中，为后续RISC-V架构下V8核心功能的原生优化奠定了基础。

本期提交的patch：
1. **[riscv][sandbox] Fix CrashFilter to detect ASAN shadow memory addresses**  
   [RISC-V][沙箱] 修复 CrashFilter 使其能检测 ASAN 影子内存地址（https://chromium-review.googlesource.com/c/7641970）
2. **[riscv][ic] Introduce homomorphic state for ICs sharing a handler**  
   [RISC-V][内联缓存] 为共享处理程序的内联缓存（IC）引入同态状态（homomorphic state）（https://chromium-review.googlesource.com/c/7623545）
3. **[riscv][jspi] Clear EPT entry on stack return**  
   [RISC-V][JSPI] 在栈返回时清空 EPT（扩展页表）表项（https://chromium-review.googlesource.com/c/7608971）
4. **[riscv][maglev] Handle equal inputs in Float64Max/Min**  
   [RISC-V][Maglev编译器] 处理 Float64Max/Min 操作中输入值相等的场景（https://chromium-review.googlesource.com/c/7599842）
5. **[wasm-interpreter] Port JSToWasmInterpreterWrapper into torque**  
   [WASM解释器] 将 JSToWasmInterpreterWrapper 迁移至 Torque 语言实现（https://chromium-review.googlesource.com/c/v8/v8/+/7455469）
   ### 格式化提交记录
6. **[riscv] Remove kCArgsSlotsSize/kCArgSlotCount**  
   [RISC-V] 移除 kCArgsSlotsSize/kCArgSlotCount 两个常量（https://chromium-review.googlesource.com/c/v8/v8/+/7649603）

## 版本测试及遗留问题
