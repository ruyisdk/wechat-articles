# RuyiSDK 双周进展汇报 第 060 期·2026 年 01 月 13 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！

若您在开发中需要部署 GNU/LLVM 工具链、QEMU 模拟器，或为 RISC-V 开发板烧录镜像，欢迎使用 RuyiSDK 包管理器 Ruyi（最新版 v0.44.0）。我们也为您提供了 VSCode 和 Eclipse 插件，助您一键获取所需工具，快速搭建开发环境。RuyiSDK 拥有丰富的工具链生态，并提供基于虚拟环境的隔离构建能力，希望能为您的开发工作带来实实在在的便利。

我们提供了多种安装方式和下载入口，欢迎试用：
* Ruyi 包管理器 (v0.44.0) ：
   * PyPI 安装：pip install ruyi
   * 手动下载安装：
      * GitHub Releases：https://github.com/ruyisdk/ruyi/releases/tag/0.44.0
      * ISCAS 镜像源：https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.44.0/
   * 使用文档：https://ruyisdk.org/docs/Package-Manager/
* RuyiSDK VSCode Extension (0.1.0) ：
   * VSCode Extensions 中搜索 `RuyiSDK` 安装
   * 手动下载安装(install from VSIX):
      * GitHub Releases：https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.0/
      * ISCAS 镜像源：https://mirror.isrc.ac.cn/ruyisdk/ide/plugins/vscode/
   * 使用文档：https://ruyisdk.org/docs/IDE/
* RuyiSDK Eclipse Plugins (0.1.0) ：
   * 手动下载安装：
      * GitHub Releases：https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.0/
      * ISCAS 镜像源：https://mirror.isrc.ac.cn/ruyisdk/ide/plugins/eclipse/
   * 使用文档：https://ruyisdk.org/docs/VSCode-Plugins/
   
我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 1 月底发布，让我们共同期待 RuyiSDK 在新的一年里带来更多惊喜！


## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.45.0 版本预期将在 1 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.44.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * Milk-V Meles 的 RevyOS: 更新到 20251226。
    * Milk-V Pioneer 的 RevyOS: 更新到 20251226。
    * Sipeed Laptop 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi Console 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheeRV Nano 的 Buildroot SDK: 更新到 20251230。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权限的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

* 上架 [VSCode Marketplace](https://marketplace.visualstudio.com/items?itemName=RuyiSDK.ruyisdk-vscode-extension)
* 重构虚拟环境检测逻辑

### Eclipse 插件

- 新闻详情展示渲染后的 Markdown 。
- 虚拟环境模块添加刷新功能。

## GCC
更新了P扩展intrinsic的支持，添加了zvzip扩展的binutils实现。

## V8

本期提交的patch：
1. **[riscv][wasmfx] Implement resume_throw** [RISC-V][wasmfx] 实现 resume_throw 功能（https://chromium-review.googlesource.com/c/7412876） 
2. **[riscv][wasmfx] Fix cmp width in WasmFXResumeThrow** [RISC-V][wasmfx] 修复 WasmFXResumeThrow 中比较指令的位宽问题（https://chromium-review.googlesource.com/c/7417239） 
3. **[riscv] Support Wasm interpreter drumbrake** [RISC-V] 为Wasm解释器提供调试断点（drumbrake）支持（https://chromium-review.googlesource.com/c/7364683） 
4. **[riscv] Enable trap handling for memory64** [RISC-V] 为 memory64 启用内存陷阱处理机制（https://chromium-review.googlesource.com/c/7365201） 
