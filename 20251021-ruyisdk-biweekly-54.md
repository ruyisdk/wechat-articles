# RuyiSDK 双周进展汇报 第 054 期·2025 年 10 月 21 日

## 卷首语

## 包管理器

RuyiSDK 0.42 对应的包管理器版本也为 0.42.0，已于 10 月 24 日发布。您可移步
[PyPI][ruyi-0.42.0-pypi]、[GitHub Releases][ruyi-0.42.0-gh] 或 [ISCAS 镜像源][ruyi-0.42.0-iscas]下载体验。

* [PyPI][ruyi-0.42.0-pypi]: `pip install ruyi`
* [GitHub Releases][ruyi-0.42.0-gh]
* [ISCAS 镜像源][ruyi-0.42.0-iscas]

[ruyi-0.42.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.42.0
[ruyi-0.42.0-pypi]: https://pypi.org/project/ruyi/0.42.0/
[ruyi-0.42.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.42.0/

> [!NOTE]
> RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
> 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
> 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
>
> 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 默认遥测模式现已变更为 `local`——收集数据但不会自动上传。
    * 相应地，在终端界面首次运行 `ruyi` 时，`ruyi` 会询问您的数据收集偏好，并帮您写入用户配置文件。
* `ruyi extract` 命令的默认行为变更与其他改进：
    * `ruyi extract` 现在会将所请求的软件包内容解压到以软件包名、版本命名的独立目录下了。之前会直接解压到当前工作目录，如用户不提前阅读文档，可能会将用户的目录弄乱。如仍然需要先前的行为，可传入新增的 `--extract-without-subdir` 选项。
    * `ruyi extract` 现在支持 `--dest-dir` 或 `-d` 选项，以便指定解压到非当前工作目录的其他目录了。
    * `ruyi extract` 也新增了 `--fetch-only` 或 `-f` 选项，与 `ruyi install` 相应选项保持一致。
* 打磨了命令行用户体验：
    * 在受支持的终端下，`ruyi` 会把重要的手工操作用红色加粗样式体现了。
    * 首次运行 `ruyi` 前，当您尝试命令行自动补全时，不会错误地打印出提示信息了。
    * 用来下载软件包但不安装或解压的 `ruyi install -f` 现在支持下载源码类型的软件包了。
    * 若用户下载了 `ruyi` 的单二进制文件发行版，但忘记将其重命名为 `ruyi`，`ruyi` 会在运行时提醒用户这么做了。
* 修复了一些问题：
    * 当 `repo.local` 的值为空字符串或与默认值相等时，不会被判定为自定义了软件源本地路径了。
    * 修复了自动管理软件源远程分支时，变更了 `repo.remote` 之后需要两次 `ruyi update` 才会体现的问题。
    * `ruyi clean --all` 不会残留软件包安装状态记录了。
    * 不再允许使用用户配置文件去覆盖那些不面向用户的配置项了。
* 更新了文档：
    * 写明了 `ruyi` 配置文件的系统全局搜索路径，供打包人员、系统管理员等参考。感谢 [@bkmgit] 的贡献！
* 工程化迭代：
    * `ruyi` 对 `packaging` 的依赖已不再必要，将于 0.43.0 版本移除。届时请打包人员更新依赖声明。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 实体数据库更新：
    * Ruyi 虚拟环境所用的 profiles 现已通过 `profile-v1` 实体类型暴露，如 `profile-v1:generic`。
* 工程化迭代：
    * 修复了一些第三方软件源镜像地址的配置问题。感谢 [@weilinfox] 的贡献！

[@bkmgit]: https://github.com/bkmgit
[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC

## LLVM

## V8

## 操作系统支持矩阵

## 版本测试及遗留问题
