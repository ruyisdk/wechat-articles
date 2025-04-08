# RuyiSDK 双周进展汇报  第 042 期·2025 年 04 月 08 日

## 卷首语

## 包管理器

RuyiSDK 0.31 对应的包管理器版本也为 0.31.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.31.0-gh] 或 [ISCAS 镜像源][ruyi-0.31.0-iscas]下载体验。

[ruyi-0.31.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.31.0
[ruyi-0.31.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.31.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* RuyiSDK 设备安装器在需要安装的软件包不止一个可用版本的时候，会额外允许您选择一个非默认（最新）的版本了。如果您的开发板需要旧版本的系统，该功能对您可能有所帮助。
* 新增了实验模式开关：环境变量 `RUYI_EXPERIMENTAL`，用于启用一些我们暂不承诺兼容性的实验性功能。
* 新增了实验性功能：实体数据库。
    * 该功能有助于 RuyiSDK 为您提供与手头设备关联的有用信息。例如，可用 `ruyi list --related-to-entity device:sipeed-lpi4a` 查询适用于 Sipeed LicheePi 4A 的各种软件包了。
    * 初期支持 CPU 微架构（如香山南湖、玄铁 C910 等等）、CPU 型号（如香山南湖、玄铁 TH1520 等等）、设备型号（如 Sipeed LicheePi 4A 等等）、软件包等四种实体类型。
    * 这些功能为预览版，后续不排除作出不兼容变更以适应需求，因此仅在启用实验模式时才可用。如您有使用场景，请保持您的 `ruyi` 与软件源为最新。
* 工程化迭代：
    * 为避免 CI 物理机资源的临时下线等原因影响到发版，将 RISC-V 架构的构建任务也暂时迁移至 GitHub Actions 公开免费提供的实例上了。
    * 将构建 `ruyi` 的单文件分发版本所用的 Python 版本升级到了 3.13.2。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC
- 修复了zicbop 的回归测试问题，正在实现 zvfbfa 扩展支持。

## LLVM

- 在 17.1.6 版本中修复了 vector reduction 内建指令的指令选择问题。

## V8
- Atomic views 适配 Tuboshaft IR；修复trap handler崩溃的问题
- 优化后端 opcde , 删除 RiscvCtz/RiscvPopcnt

## 操作系统支持矩阵

- [BPI-F3/openHarmony: Fix date](https://github.com/ruyisdk/support-matrix/pull/212)
- [Duo/OpenWrt: new test report](https://github.com/ruyisdk/support-matrix/pull/213)
- [Duo/OpenWrt: remove others.yml](https://github.com/ruyisdk/support-matrix/pull/214)
- [Add Fedora and update Debian test reports for Mars; fix some typos.](https://github.com/ruyisdk/support-matrix/pull/216)
- [Star64/Armbian: update link](https://github.com/ruyisdk/support-matrix/pull/235)
- [Ports documentation from oscompare](https://github.com/ruyisdk/support-matrix/pull/163)
- [LicheePi4A: add openEuler 25.03](https://github.com/ruyisdk/support-matrix/pull/237)
- 网页前端 [VeRForTe](https://github.com/panglars/VeRForTe):
  - 新增：Others
  - 支持 GitHub Markdown 语法
