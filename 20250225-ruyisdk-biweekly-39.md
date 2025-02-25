# RuyiSDK双周进展汇报  第039期·2025年02月25日

## 卷首语

## 包管理器

RuyiSDK 0.28 对应的包管理器版本也为 0.28.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.28.0-gh] 或 [ISCAS 镜像源][ruyi-0.28.0-iscas]下载体验。

[ruyi-0.28.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.28.0
[ruyi-0.28.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.28.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 运行不依赖软件源的命令时，如软件源仓库尚未拉取到本地，现在不会多余做拉取动作了。
* `ruyi list` 现在支持基本的过滤查询了：使用 `--category-is` 查询某个分类下的软件包，使用
  `--name-contains` 查询名称中包含特定字样的软件包。
* 考虑到软件包的数量持续增加，不带任何参数的 `ruyi list` 不再受到支持。如果您有依赖先前行为的脚本等，请按照提示修改使用方式。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增了以下软件包：
    * `source/wiringx`: wiringX 项目的官方源码。wiringX 是模块化的 GPIO 支持组件。
* 更新了以下软件包：
    * `board-image/bianbu-bpi-f3`
    * `board-image/revyos-milkv-meles`
    * `board-image/revyos-sg2042-milkv-pioneer`
* 修复了 `board-image/revyos-milkv-meles` 的 `boot` 分区的文件类型标记。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE
继续 RuyiSDK IDE Plugins 插件功能开发：
- 增加启动时执行 `ruyi update` 命令，并展示未读的 `ruyi news` 信息
- 实现关于缓存/配置路径的 RuyiPaths 工具类

## GCC

实现了Xqc系列自定义厂商扩展支持，等待上游review中，继续维护p扩展实现，修复了工具链构建中的一些问题。

## LLVM

- 在 17.1.6 版本中修复了缺少 `th.vloxei` 和 `th.vsoxei` 指令的问题
- 在 17.1.6 版本中新增对部分内建函数操作数合法性检查的过程
- 在 17.1.6 版本中修复部分包装函数名称不符合 RVV 1.0 规范的问题，选择这些包装函数将同时提供 1.0 和 0.7.1 规范下的函数名，以便更方便地进行迁移
- 在 19.1.6 版本中修复了 MC 汇编器生成部分指令会出现编译器内部错误的问题

## V8
- Review并合入 Leaptiering 支持
- 添加模拟器中对 fp16 类型指令的模拟例程
- 继续增加 Maglev 的特性支持
  
## 操作系统支持矩阵
