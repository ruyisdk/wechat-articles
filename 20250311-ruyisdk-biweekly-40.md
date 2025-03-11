# RuyiSDK 双周进展汇报  第 040 期·2025 年 03 月 11 日

## 卷首语

## 包管理器

RuyiSDK 0.29 对应的包管理器版本也为 0.29.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.29.0-gh] 或 [ISCAS 镜像源][ruyi-0.29.0-iscas]下载体验。

[ruyi-0.29.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.29.0
[ruyi-0.29.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.29.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 修复了 `ruyi news list` 命令的机读模式（porcelain mode）支持。
* 为 `ruyi news read` 增加了机读模式（porcelain mode）支持，返回格式与 `ruyi news list` 相同。
* 软件源格式更新：
    * 不再支持以 JSON 格式撰写软件源全局配置与软件包描述。RuyiSDK 官方软件源已于 0.18 版本完成了升级，预期不受此变更影响。如您仍未升级您的 `ruyi` 版本，建议您重新安装 `ruyi` 并重做虚拟环境（如有）。
    * 为软件包版本描述新增了可选的 `upstream_version` 字段，用来记录相应上游对该版本的称呼。由于 RuyiSDK 软件源普遍采用语义化版本，经常需要对不采用语义化版本的上游版本号进行映射；新增该字段有助于 RuyiSDK 生态的软件包管理工具正确理解该类映射关系。
    * 为未来的软件包级别的公共信息作了向后兼容的预留。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC

## LLVM

## V8

## 操作系统支持矩阵
