# RuyiSDK双周进展汇报  第034期·2024年12月03日

## 卷首语

## 包管理器

RuyiSDK 0.23 对应的包管理器版本也为 0.23.0，已于昨日发布。您可移步
[GitHub Releases][ruyi-0.23.0-gh] 或 [ISCAS 镜像源][ruyi-0.23.0-iscas]下载体验。

[ruyi-0.23.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.23.0
[ruyi-0.23.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.23.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 出于项目验收要求，调整了默认遥测模式为 `on`。后续会随着 RuyiSDK 软件源的更新，周期性上传匿名化的使用统计数据。遥测服务端位于中国大陆境内，由 RuyiSDK 团队管理。
* 修复了与外部依赖 `semver` 2.x 版本的兼容性。
* 允许了在 CI 环境以 `root` 身份运行 `ruyi`。
* 每次发版会同时附带可重现（reproducible）的源码包了，有助于发行版打包工作等。

**注意：**由于活跃用户数等指标是项目 KPI，RuyiSDK 0.23
版本增加了遥测数据的上传功能，并**在所有环境默认开启**，不仅限于
CI。您可自行决定是否主动上传这部分匿名统计信息，以便
RuyiSDK 团队改进产品；您也可以选择删除先前的遥测数据，以及是否禁用遥测。您可用
`ruyi self clean --telemetry` 删除所有的遥测信息，包括设备信息。详情请见 RuyiSDK 0.19
的发布说明：[《RuyiSDK 双周进展汇报 第 030 期·2024年09月30日》][ruyisdk-biweekly-30]。

在遥测模式为 `on` 时，每次 `ruyi` 被调用时都会告知您您的遥测数据将在何时上传。您可以做以下操作之一以屏蔽该提示。

* 设置遥测模式为 `local` 或 `off`；
* 对数据上传行为给予同意。

具体的 `ruyi` 配置文件写法示例如下。该配置文件一般位于 `~/.config/ruyi/config.toml`
位置，如不存在，创建即可。

```toml
# 在 [telemetry] 一节体现以下内容之一。如不存在此节，创建即可：
[telemetry]

# 您可以变更遥测模式为 local 或 off:
mode = "local"

# 或告知 ruyi 您在当前日期时间给予了同意：
upload_consent = 2024-12-32T25:61:00+08:00
# 此日期格式并不合法，这是有意为之，请您自行填入您操作的当前时刻。例如执行以下命令：
#
#     echo "upload_consent = $(date -Iseconds)"
#
# 输出内容即可用于上述用途。
```

[ruyisdk-biweekly-30]: ./20240930-ruyisdk-biweekly-30.md

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

## GCC
Multiversion function的支持已合入gcc上游，继续完善P扩展的支持，重新提交了RISC-V Profiles的支持patch,正在沟通RV64ILP32规范格式问题。

## V8

## 操作系统支持矩阵

## SDK
