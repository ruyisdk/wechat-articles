# RuyiSDK 双周进展汇报 第 075 期 · 2026 年 09 月 01 日

## 卷首语

>

## 基础开发环境


### 包管理器

RuyiSDK 0.52 已于 2026 年 9 月 1 日发布，对应的包管理器版本也为 0.52.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 为未来的“RuyiSDK 认证”做了包管理器方面的预留。
* 修复了实验性的 `ruyi entity list` 命令只接受多个 `-t` 参数中的第一个的问题。感谢 [weilinfox][weilinfox] [报告](https://github.com/ruyisdk/ruyi/issues/492)此问题，感谢 [Mr-Eric666][Mr-Eric666] 的[贡献](https://github.com/ruyisdk/ruyi/pull/493)！
* 工程化迭代：
  * 更新了依赖版本。
  * 使 `ruyi` 的代码写法兼容了 argcomplete 3.7.2 及更高的版本。
  * pygit2 上游已从 1.20.0 版本开始提供 RISC-V 二进制，故移除了 pygit2 的本地构建逻辑，降低维护成本。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 修复了“最新包管理器版本”API 返回的 macOS 二进制条目的“操作系统/架构”键名不对的问题。感谢 [weilinfox][weilinfox] [报告](https://github.com/ruyisdk/ruyi-backend/issues/113)此问题！

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

[Mr-Eric666]: https://github.com/Mr-Eric666
[weilinfox]: https://github.com/weilinfox

### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 软件源格式更新：
  * 支持为软件包附着供应商元数据：位于 manifest TOML 的 `metadata.vendor.data` 字段，其类型为 `供应商 ID: 键值对` 的字典（TOML 表格）；支持布尔型与字符串类型的值。
  * 预留 `metadata.vendor.data.ruyisdk.certified` 为表示“RuyiSDK 认证”状态的元数据字段。
* 更新软件包：
  * `board-image/armbian-spacemit-musepipro-minimal`: SpacemiT Muse Pi Pro 的 Armbian。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `toolchain/gnu-ruyisdk`: RuyiSDK GNU 工具链，增加了实验性的 macOS AArch64 (Apple Silicon) 支持。
* 新增设备支持：
  * 知合 (Zhihe Computing) A210 SODIMM: 兼容其官方提供的 EVB 系统镜像。感谢 [weilinfox][weilinfox] 的贡献！

您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

[SmulllLu]: https://github.com/SmulllLu

### 开发板支持矩阵


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

### GCC

### LLVM

### V8

### OpenJDK

### Go

### QEMU

## 社区动态


---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
