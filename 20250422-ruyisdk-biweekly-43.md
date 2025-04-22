# RuyiSDK 双周进展汇报  第 043 期·2025 年 04 月 22 日

## 卷首语

## 包管理器

RuyiSDK 0.32 对应的包管理器版本也为 0.32.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.32.0-gh] 或 [ISCAS 镜像源][ruyi-0.32.0-iscas]下载体验。

[ruyi-0.32.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.32.0
[ruyi-0.32.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.32.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 新增了贡献指南文档，使社区成员更容易参与项目贡献。
* 为流程合规，现在要求所有向 RuyiSDK 发起的拉取请求（Pull Requests）都包含开发者原创声明（Developer's Certificate of Origin, DCO）了。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * 新增支持了适用于 SpacemiT K1 设备的特殊刷写策略。
    * 修复了设备安装器调用 `fastboot` 失败的问题。
    * 更新了 Sipeed LicheeRV Nano 的 Buildroot SDK 镜像。
    * 更新了 Sipeed LicheePi 4A 的 RevyOS 镜像版本并修复问题。
    * 更新了 Milk-V Meles 的 RevyOS 镜像。
* 重命名了软件包 `board-image/revyos-sg2042-milkv-pioneer` 为 `board-image/revyos-milkv-pioneer` 以符合当前的软件包命名规范。
* 实体数据库更新：
    * 设备实体定义现已与设备安装器支持范围对齐。补充了 Milk-V、Sipeed、Canaan、StarFive、WCH 等厂商的设备定义。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 优化了 ruyisdk.org 官网数据统计页面的性能。
* 集成了 GitHub Releases 渠道的下载量到官网数据统计页面的 RuyiSDK 包管理器下载计数中，使统计数据更准确、全面。
* 将原先位于 RuyiSDK 包管理器仓库、需要手工配置生效的镜像源同步脚本迁移到了服务端。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC
添加了zama16b，sdtrig，zvfbfmin扩展的支持，重新提交了ssnpm的patch

## LLVM

## V8

## 操作系统支持矩阵

## 官网

+ 优化了 RuyiSDK [数据总览](https://ruyisdk.org/Home/StatisticalDataPages/)

