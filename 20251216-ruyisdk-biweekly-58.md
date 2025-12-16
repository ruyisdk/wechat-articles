# RuyiSDK 双周进展汇报 第 058 期·2025 年 12 月 16 日

## 卷首语

## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.44.0
版本预期将在 12 月底正式发布。您仍可通过以下渠道下载 RuyiSDK 包管理器的 0.43.0 版本：

* [PyPI][ruyi-0.43.0-pypi]: `pip install ruyi`
* [GitHub Releases][ruyi-0.43.0-gh]
* [ISCAS 镜像源][ruyi-0.43.0-iscas]

[ruyi-0.43.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.43.0
[ruyi-0.43.0-pypi]: https://pypi.org/project/ruyi/0.43.0/
[ruyi-0.43.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.43.0/

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增设备支持：
    * Milk-V Megrez: 搭载使用 SiFive P550 微架构的 ESWIN EIC7700X CPU，兼容各类 RockOS 镜像。
* 完善了设备支持：
    * OpenBSD: 更新到 7.8。
    * FreeBSD Mini Live: 更新到 15.0。
    * Milk-V Pioneer 的 RevyOS: 更新到 20251115。
    * SiFive Unmatched 的 OpenWrt: 更新到 24.10.4。
    * Sipeed Laptop 4A 的 RevyOS: 更新到 20251115。
    * Sipeed LicheePi 4A 的 RevyOS: 更新到 20251115。
    * Sipeed LicheePi Console 4A 的 RevyOS: 更新到 20251115。
    * Sipeed LicheeRV Nano 的 Buildroot SDK: 更新到 20251202。
    * Sipeed Meles 的 RevyOS: 更新到 20251115。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE
**VSCode 插件：**

**Eclipse 插件：**

## GCC

## LLVM

## V8
