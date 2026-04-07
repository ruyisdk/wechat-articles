# RuyiSDK 双周进展汇报 第 066 期·2026 年 04 月 07 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！春意渐浓，RuyiSDK 双周进展已更新到第 66 期。
 
本期看点集中在以下几个方面：

- 包管理器：为 4 月底的版本更新做收尾，同时为后续 0.48.0 的功能演进打基础。兼容性基线将提升到 Ubuntu 24.04 LTS，虚拟环境与遥测上报等能力也在持续演进，以更好地服务企业级与 CI 场景。
- IDE：VSCode 与 Eclipse 插件持续打磨交互与配置体验，为不同偏好的开发者提供更顺手的集成环境。
- 工具链与上游：GCC、LLVM、V8 等项目围绕 RISC‑V P 扩展与 SIMD 等方向持续贡献补丁，优化指令选择与仿真层实现，为运行时与编译器生态提供更坚实的基础。

更多进展细节详见下方各板块，欢迎试用并在 GitHub 或社区中反馈建议，期待更多伙伴一起共建 RISC‑V 软件开发生态。

⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.47.0
    * 从 [PyPI](https://pypi.org/project/ruyi/0.47.0/) 安装：`pip install ruyi`
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.47.0)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.47.0/)
    * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

    > [!NOTE]
    > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
    > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
    > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
    >
    > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

* RuyiSDK VSCode Extension 0.1.2
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

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 4 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.48.0 版本预期将在 4 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.47.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* 为 4 月底 Ubuntu 26.04 LTS 正式发布做准备，提升 RuyiSDK 官方软件源二进制包的兼容基线至 Ubuntu 24.04 LTS。
* 允许用户为 Ruyi 虚拟环境自行提供 sysroot，方便为大型软件项目准备依赖。
* 允许 RuyiSDK 包管理器向官方与第三方软件源安全上报软件包安装、卸载等遥测数据。
* 支持在本地环境用 ruyi 命令协调构建 RuyiSDK 出品的软件包。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权限的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。


## IDE

### VSCode 插件

- 更新 Ruyi 包管理器旧版本检测机制

### Eclipse 插件

- 包管理器：重新设计界面；显示人类友好的设备名称；显示包的基本信息；根据所选设备筛选包列表；显示操作确认对话框。
- 配置管理与 Ruyi 安装向导：重新设计界面；将相关配置条目置于同一页；允许配置 Ruyi 目前所支持的所有配置；移除不需要在插件持久化的配置。
- 推广：在 Eclipse 内置浏览器中展示 RuyiSDK.cn 网站。
- 其他：清理已被淘汰的 API。

## GCC
- 更新了P扩展的工具链实现到草案0.20版本,开始进行gcc-precommit-ci的维护工作，更新了zibi扩展的binutils patch.

## LLVM

- https://github.com/llvm/llvm-project/pull/190303
为 P 扩展添加 add(vec, splat(scalar)) 到 PADD_*S 的指令选择支持

- https://github.com/llvm/llvm-project/pull/181115
添加了更多的 intrinsic 支持

## V8
本期提交的patch：
1.  **[riscv] Fix SIMD lane load source register**
    [RISC-V] 修复SIMD通道加载的源寄存器问题（https://chromium-review.googlesource.com/c/7695806）
2.  **[riscv][turboshaft] Direct call for known functions**
    [RISC-V][Turboshaft] 对已知函数实现直接调用（https://chromium-review.googlesource.com/c/7695807）
3.  **[riscv] Add simd in LiftoffAssembler::Push/Pop**
    [RISC-V] 在Liftoff汇编器的Push/Pop中增加SIMD支持（https://chromium-review.googlesource.com/c/7695091）
4.  **[riscv][wasm][wasmfx] Implement switch instruction**
    [RISC-V][WASM][WasmFX] 实现switch指令（https://chromium-review.googlesource.com/c/7699360）
5.  **[riscv] Fix build for cross compile**
    [RISC-V] 修复交叉编译构建问题（https://chromium-review.googlesource.com/c/7699576）
6.  **[riscv][base] Refactor EmbeddedVector: decouple from Vector**
    [RISC-V][基础库] 重构EmbeddedVector，使其与Vector解耦（https://chromium-review.googlesource.com/c/7707695）
7.  **[riscv][liftoff] Separate floating-point and simd registers**
    [RISC-V][Liftoff] 分离浮点寄存器与SIMD寄存器（https://chromium-review.googlesource.com/c/7658971）
8.  **[riscv] Fix lmul calculation in SetSimd128Half for VLEN 256/512**
    [RISC-V] 修复VLEN为256/512时SetSimd128Half中的lmul计算问题（https://chromium-review.googlesource.com/c/7676638）
9.  **[riscv] Fix Segment fault in native**
    [RISC-V] 修复原生代码中的段错误（https://chromium-review.googlesource.com/c/7720660）
10. **[riscv] Enable kWord64Select**
    [RISC-V] 启用kWord64Select特性（https://chromium-review.googlesource.com/c/7699088）
11. **[riscv] Fix segment fault in SimulatorTrapHandlerTestWithCodegen.ProbeMemory_MultiStruct**
    [RISC-V] 修复SimulatorTrapHandlerTestWithCodegen.ProbeMemory_MultiStruct测试中的段错误（https://chromium-review.googlesource.com/c/7722697）


