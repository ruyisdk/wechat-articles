# RuyiSDK双周进展汇报  第038期·2025年02月11日

## 卷首语

## 包管理器

RuyiSDK 0.27 对应的包管理器版本也为 0.27.0，已于昨日发布。您可移步
[GitHub Releases][ruyi-0.27.0-gh] 或 [ISCAS 镜像源][ruyi-0.27.0-iscas]下载体验。

[ruyi-0.27.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.27.0
[ruyi-0.27.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.27.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 新增了 `ruyi telemetry upload` 命令。如果您乐意配合，现在在 CI 等临时性场合也能确保遥测数据在任务结束、环境被清理之前得到上传了。
* 支持分别指定软件包版本的服务等级了。如果某个软件包的某个版本存在已知问题，在安装或解压该版本时，`ruyi` 会输出提示信息，该信息可由打包人员在软件源维护。后续也将支持按照服务等级过滤软件包：届时将可以跳过存在已知问题的版本，或仅使用经过验证的版本等。
* 工程化相关变更。
    * 支持了 pygit2 1.17.0。`ruyi` 的单文件分发版本已经切换至该版本了。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新了以下软件包：
    * `board-image/buildroot-sdk-milkv-duo`
    * `board-image/buildroot-sdk-milkv-duo256m`
    * `board-image/buildroot-sdk-milkv-duos-sd`
    * `board-image/uboot-revyos-sipeed-lpi4a-16g`
    * `board-image/uboot-revyos-sipeed-lpi4a-8g`
* 修复了一些软件包得到自动化版本升级之后，无法正常下载的问题。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE
RuyiSDK Eclipse Plugins 插件 v0.0.1 发布：
- 新增 RuyiSDK 菜单及官网访问命令。

插件使用说明：
1. 下载 [org.ruyisdk.ide_0.0.1.jar](https://github.com/xijing21/eclipse-plugins/releases/download/v0.0.1/org.ruyisdk.ide_0.0.1.jar)。
2. 访问 https://mirror.iscas.ac.cn/ruyisdk/ide/0.0.3/ 下载 ruyisdk-0.0.3 并解压。
3. 将 org.ruyisdk.ide_0.0.1.jar 放入 ruyisdk ide 的 dropins 目录。
4. 执行 ./ruyisdk 重启 IDE。
5. 通过菜单栏 RuyiSDK > Official Website 访问官网。

## GCC
更新了P扩展草案的工具链支持至0.14版本，更新了Profiles的规范格式说明。

## V8

## 操作系统支持矩阵

- [CI: Fix restrict field](https://github.com/ruyisdk/support-matrix/pull/156)
- [duo/duo256m: Add NixOS](https://github.com/ruyisdk/support-matrix/pull/157)
- [Refactor Tools](https://github.com/ruyisdk/support-matrix/pull/158)
- [Updator: Allow bootstrap a new image, Add pulgin to update images from mirrorsite](https://github.com/ruyisdk/support-matrix/pull/159)
