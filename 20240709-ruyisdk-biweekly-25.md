# RuyiSDK双周进展汇报  第025期·2024年07月09日

## 卷首语


## 包管理器

RuyiSDK 0.14 对应的包管理器版本也为 0.14.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.14.0-gh] 或 [ISCAS 镜像源][ruyi-0.14.0-iscas]下载体验。

[ruyi-0.14.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.14.0
[ruyi-0.14.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.14.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 正式引入插件架构：`ruyi` 虚拟环境的 profile 相关处理现在完全由插件负责了。
* 支持了 Debian 软件包格式 `*.deb` 的解包操作。
* 再次完善了对“预发布版本”的判断：先前会对非完全由数字结尾的该类版本号判断错误。
  但该潜在问题不会被当前的 RuyiSDK 软件源内容触发。
* 修复了 riscv64 Python 3.12 环境下 `pygit2` 的构建失败问题：先前需要在
  `pygit2` 构建开始之后、试图在其虚拟环境中执行 `setup.py` 前，人工干预，在该环境中安装
  `setuptools`——从 Python 3.12 起该包已经不会被自动安装。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 增加了从上游源码打包的 Box64 架构模拟器：`emulator/box64-upstream`。
* 增加了办公套件 `extra/wps-office`。请注意：由于是商业软件的缘故，首次运行该软件包时需要操作接受一份《最终用户许可协议》。
* 您可按照 `ruyi news` 的指引，在您的 RISC-V 桌面设备上用 Box64 运行
  WPS Office 进行办公了。

为了支持刷写方式复杂、需要夹杂人工干预、镜像文件需要手工下载等复杂情况下的设备初始化，我们正在将设备安装器重构为基于插件架构的形式。
由于本开发周期临时加入了 Box64 运行 WPS Office 的 PoC 内容，设备安装器的插件化重构工作暂缓，但仍将在未来的版本上线。届时旧版
`ruyi` 的设备安装器功能将不可用，请先升级再进行体验。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

## IDE


## GCC


## LLVM


## V8


## OpenJDK


## 官网

[RuyiSDK 社区参与的 MoonBit 第三次 Meetup 活动回顾来了！🎉](https://mp.weixin.qq.com/s/7JuZMKcxpENoygn1YfnCLA)

由 MoonBit 联合 RuyiSDK 和 Intel 举办的第三次 Meetup 活动圆满结束啦！本次活动嘉宾云集，涵盖了从云原生开发平台到 WebAssembly 模块化技术、编程语言垃圾回收技术的最新进展、RuyiSDK 包管理器以及 RevyOS 最新进展多个热点话题。

截止今日7月8日，订阅人数一共37人（增加1人）。RuyiSDK网站访问人数502人（增加103人），访问页面1424次（增加339次）。RuyiSDK 微信交流群 70人（进群请微信加小助手ruyisdk_helper）。

## 操作系统支持矩阵
