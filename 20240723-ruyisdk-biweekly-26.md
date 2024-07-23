# RuyiSDK双周进展汇报  第026期·2024年07月23日

## 卷首语

## 包管理器

RuyiSDK 0.15 对应的包管理器版本也为 0.15.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.15.0-gh] 或 [ISCAS 镜像源][ruyi-0.15.0-iscas]下载体验。

[ruyi-0.15.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.15.0
[ruyi-0.15.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.15.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

*   为多语言支持做好准备：在需要输出本地化内容，如软件包的手工下载步骤说明等内容时，当用户系统的区域、语言配置与当前内容的可选区域、语言版本不完全匹配时，现在会尽可能地匹配了。

    > 例如：如果您将系统配置为新加坡英语，而某条内容仅提供美国英语与中国大陆中文两种版本，那么
    > `ruyi` 0.15.0 将为您展示美国英语内容，而非崩溃。

*   支持了不依赖 Docker 的构建方式，以方便发行版打包者，或不使用官方支持架构、系统组合的用户尝鲜
    `ruyi`。

    > 需要注意的是：因为目前 RuyiSDK 官方软件源的内容分发形式以二进制为主，所以想在非官方支持系统上使用
    > `ruyi` 的用户将需要组织起来，自行搭建另一套软件源。RuyiSDK 团队无法保证此种情况下的用户体验。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 软件源的结构不再与 `ruyi` 0.7.0 或更低版本兼容。是时候升级到最新版本了。
* `emulator/box64-upstream` 已更新到 0.3.0。
* 用 Box64 运行 WPS Office 的操作文档已更新。
* Ruyi 设备安装器现已新增支持以下设备型号与系统：
    * Canaan Kendryte K230D：由 RuyiSDK 受权打包的 CanMV Linux SDK 镜像，附带演示程序。提供 LP64 与 RV64ILP32 两种 ABI。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

## IDE

## GCC

## LLVM

## V8

## OpenJDK

## 官网

## 操作系统支持矩阵
