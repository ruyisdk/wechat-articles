# RuyiSDK 双周进展汇报 第 060 期·2026 年 01 月 13 日

## 卷首语


## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.45.0
版本预期将在 1 月底正式发布。您仍可通过以下渠道下载 RuyiSDK 包管理器的 0.44.0 版本：

* [PyPI][ruyi-0.44.0-pypi]: `pip install ruyi`
* [GitHub Releases][ruyi-0.44.0-gh]
* [ISCAS 镜像源][ruyi-0.44.0-iscas]

[ruyi-0.44.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.44.0
[ruyi-0.44.0-pypi]: https://pypi.org/project/ruyi/0.44.0/
[ruyi-0.44.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.44.0/

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


## LLVM


## V8

本期提交的patch：
1. **[riscv][wasmfx] Implement resume_throw** [RISC-V][wasmfx] 实现 resume_throw 功能（https://chromium-review.googlesource.com/c/7412876） 
2. **[riscv][wasmfx] Fix cmp width in WasmFXResumeThrow** [RISC-V][wasmfx] 修复 WasmFXResumeThrow 中比较指令的位宽问题（https://chromium-review.googlesource.com/c/7417239） 
3. **[riscv] Support Wasm interpreter drumbrake** [RISC-V] 为Wasm解释器提供调试断点（drumbrake）支持（https://chromium-review.googlesource.com/c/7364683） 
4. **[riscv] Enable trap handling for memory64** [RISC-V] 为 memory64 启用内存陷阱处理机制（https://chromium-review.googlesource.com/c/7365201） 
