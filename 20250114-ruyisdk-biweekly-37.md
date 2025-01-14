# RuyiSDK双周进展汇报  第037期·2025年01月14日

## 卷首语

## 包管理器

RuyiSDK 0.26 对应的包管理器版本也为 0.26.0，已于昨日发布。您可移步
[GitHub Releases][ruyi-0.26.0-gh] 或 [ISCAS 镜像源][ruyi-0.26.0-iscas]下载体验。

[ruyi-0.26.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.26.0
[ruyi-0.26.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.26.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 为 `ruyi telemetry status` 新增了 `--verbose` (`-v`) 选项，供用户在 `ruyi telemetry consent` 之后继续查看自身遥测数据的上传计划。
* 修复了使用厂商工具链创建虚拟环境时，工具链 `-mcpu` 取值可能不被正确映射的问题。如果您受影响，请在 `ruyi update` 之后重建虚拟环境。
* 继续加强了平台兼容性保障。
    * 新增了一篇平台兼容性技术文档，明确了当前 `ruyi` 支持的第三方依赖的基线版本。
    * 以 CI 检查的方式确保了 `ruyi` 的所有变更都不影响 `ruyi` 在 Ubuntu 22.04 下通过测试套件。
* 工程化相关变更。
    * 修复了源码包内遗漏了一层子目录结构的问题。
    * 更新 Poetry 至 2.0 版本，顺带更新了 `ruyi` 的 Python 项目元数据（`pyproject.toml`）。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新了 `board-image/revyos-sipeed-lpi4a`。
* 配合 `ruyi` 0.26.0 相应更改，支持了新的 profile API，以便为虚拟环境正确配置 `-mcpu`。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC
更新了Profiles实现规则，在GLIBC中添加了IFUNC符号用于调用，更新了新32位的GDB支持，开始启动GDB SIM的调试工作。

## V8
1. Refactor Relocation支持部分的代码。
2. 修复 strict 模式下的构建错误问题。

## 操作系统支持矩阵
