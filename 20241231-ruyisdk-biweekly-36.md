# RuyiSDK双周进展汇报  第036期·2024年12月31日

## 卷首语

## 包管理器

RuyiSDK 0.25 对应的包管理器版本也为 0.25.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.25.0-gh] 或 [ISCAS 镜像源][ruyi-0.25.0-iscas]下载体验。

[ruyi-0.25.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.25.0
[ruyi-0.25.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.25.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 新增了 `ruyi config` 子命令，方便用户通过命令行或脚本方式查询、修改 RuyiSDK 包管理器配置。该命令用法受到了 `git config` 的启发，详见 `ruyi config --help` 输出。
* 新增了 `ruyi telemetry` 子命令，方便用户通过命令行或脚本方式查询、变更遥测偏好。详见 `ruyi telemetry --help` 输出。
    * 特别地：在您表明遥测偏好前，每次运行 `ruyi` 您都会收到提醒。您现在可以通过 `ruyi telemetry off` 关闭遥测数据收集，或通过 `ruyi telemetry consent` 明确接受遥测数据收集与上传了。
* 修复了搭配 arpy 1.x 使用时，无法解压 Debian 格式软件包的问题。
* 新增了两篇规范文档：RuyiSDK 官方软件源的包版本规范，以及 RuyiSDK 中的板卡型号、系统镜像命名规范。您可移步 RuyiSDK 包管理器的仓库 `docs/` 目录阅读。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE
RuyiSDK IDE V0.0.2 版本发布，下载地址为：https://mirror.iscas.ac.cn/ruyisdk/ide/0.0.2/ 请按照设备环境选择合适的安装包。
V0.0.2 主要针对 Milk-V Duo example 示例在 RuyiSDK IDE 中的编译器安装配置、构建、目标程序传输、运行等进行验证并创建使用文档。在 RuyiSDK IDE 的 Welcome 中定制了 RuyiSDK 和 Milk-V Duo 的文档链接。


## GCC
提交了Zilsd/Zclsd扩展支持的patch，补充了相应的测试用例。开始更新Profiles命名规范，同步LLVM已有的实现方式。

## V8
1. 增加对 Embedded Object 的 reloc 支持，减少加载此类对象的指令数量。
2. 审阅并合入 Syntacore 对浮点数四舍五入的指令生成的优化。

## 操作系统支持矩阵

| PR                                                 | Content                                          | Status |
| -------------------------------------------------- | ------------------------------------------------ | ------ |
| https://github.com/ruyisdk/support-matrix/pull/120 | CI: Add CI for package index sync                | Merged |
| https://github.com/ruyisdk/support-matrix/pull/121 | fix typo in Duo_S link                           | Merged |
| https://github.com/ruyisdk/support-matrix/pull/123 | visionfive2: Add NixOS                           | Merged |
| https://github.com/ruyisdk/support-matrix/pull/125 | m0sense: Add RT-Thread                           | Merged |
| https://github.com/ruyisdk/support-matrix/pull/126 | BPI-F3: bianbu update to 2.0.4                   | Merged |

## SDK
