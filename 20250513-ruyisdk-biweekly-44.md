# RuyiSDK 双周进展汇报  第 044 期·2025 年 05 月 13 日

## 卷首语

## 包管理器

RuyiSDK 0.33 对应的包管理器版本也为 0.33.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.33.0-gh] 或 [ISCAS 镜像源][ruyi-0.33.0-iscas]下载体验。

[ruyi-0.33.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.33.0
[ruyi-0.33.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.33.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 将设备安装器的数据源迁移到了实体数据库，以降低维护成本、避免频繁更新时潜在的合并冲突等。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * 新增支持了 Milk-V Meles 的 16G RAM 型号，支持 RevyOS 系统。
* 实体数据库更新：
    * 设备实体定义更新：设备型号变体现已被拆分为单独实体类型 `device-variant` 了。
    * 新增了“设备适用系统信息”实体 `image-combo`。
* 现已弃用旧版设备安装器支持，请尽快更新您的 RuyiSDK 包管理器。该支持将于 RuyiSDK 0.35 移除。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 新增了官方软件源的新闻条目阅读 API。
* 新增了按版本号查询 RuyiSDK 版本发行注记的 API。
* 将官方软件源当前目录结构下的所有子目录都纳入了下载量统计范围。
* 改进了服务容器的构建方式。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC
更新了RUYISDK仓库中的gcc版本到gcc16, binutils版本到binutils-2.45。支持了Profiles特性，包括RV20/22/23A|B, 使用-march=Profiles可直接使能Profiles规定的强制支持扩展
支持了`Sha`扩展组合，该扩展为RVA23S64中针对RISC-V虚拟化特性提出的最新扩展组合，用于高效实现虚拟化特性。修复回归测试中发现的gcc错误，限制了错误测试case中
`-mgeneral-regs-only`选项对应的架构范围，已被上游接收

## LLVM

## V8

## 操作系统支持矩阵

## 官网
