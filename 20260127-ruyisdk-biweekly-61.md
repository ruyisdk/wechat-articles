# RuyiSDK 双周进展汇报 第 061 期·2026 年 01 月 27 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！

本期包管理器、 VSCode 和 Eclipse 插件都提供了新的版本，包管理器主要提供了中文支持（部分插件中文支持还在完善），VSCode 和 Eclipse 插件也均对虚拟环境的支持进行了完善，更多更新详见下方，欢迎大家下载体验。

每个组件都提供了多种下载或安装方式，您可以任意选择一个：
* Ruyi 包管理器 (v0.45.0) ：
   * [PyPI](https://pypi.org/project/ruyi/0.45.0/) 安装：pip install ruyi
   * 手动下载安装：
      * GitHub Releases：https://github.com/ruyisdk/ruyi/releases/tag/0.45.0
      * ISCAS 镜像源：https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.45.0/
   * 使用文档：https://ruyisdk.org/docs/Package-Manager/
   > [!NOTE]
   > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
   > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
   > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
   >
   > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。
* RuyiSDK VSCode Extension (0.1.1) ：
   * VSCode Extensions 中搜索 `RuyiSDK` 安装
   * 手动下载安装(install from VSIX):
      * GitHub Releases：https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.1/
      * ISCAS 镜像源：https://mirror.isrc.ac.cn/ruyisdk/ide/plugins/vscode/
   * 使用文档：https://ruyisdk.org/docs/IDE/
* RuyiSDK Eclipse Plugins (0.1.1) ：
   * 手动下载安装：
      * GitHub Releases：https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.1/
      * ISCAS 镜像源：https://mirror.isrc.ac.cn/ruyisdk/ide/plugins/eclipse/
   * 使用文档：https://ruyisdk.org/docs/VSCode-Plugins/
   
我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于春节前发布，让我们共同期待 RuyiSDK 在新的一年里带来更多惊喜！

## 包管理器

RuyiSDK 0.45 已于今日发布，对应的包管理器版本也为 0.45.0。
本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 由 `pipx` 安装的 `ruyi` 可以正常创建虚拟环境了。
* 包管理器（本体部分）现已支持简体中文本地化。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * Milk-V Meles 的 RevyOS: 更新到 20251226。
    * Milk-V Pioneer 的 RevyOS: 更新到 20251226。
    * Sipeed Laptop 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi Console 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheeRV Nano 的 Buildroot SDK: 更新到 20251230。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

- 解压包模板功能添加suggested folder（一键选择解压到当前目录或子目录）
- 重构虚拟环境功能
- 修复vscode marketplace的图片失效问题

### Eclipse 插件

- 修复新闻模块第三方库的依赖问题。
- 虚拟环境模块支持自动探测工作区中的项目。
- 测试 Update Site 以准备上架 Eclipse Marketplace 。

## GCC

添加了Zalasr扩展支持，更新了P扩展文档手册。

## LLVM

xtheadvector 分支更新内容如下：
- [[LLVM][Clang][MC][XTHeadVector] add missing vncvt.x.x.w](https://github.com/ruyisdk/llvm-project/pull/167)


## V8
本期亮点：在SG2042平台上修复了两个Chromium主线上的构建bug

提交的patch如下：
1. **[riscv] Fix incorrect code gen**  
   [RISC-V] 修复不正确的ZBA指令代码生成逻辑（https://chromium-review.googlesource.com/c/7484947）
2. **[deoptimizer] fix comment**  
   [反优化器] 修复注释错误（https://chromium-review.googlesource.com/c/7459395）
3. **[riscv][maglev] Materialize undefined for undefined nan on exception**  
   [RISC-V][Maglev编译器] 针对异常场景下未定义的NaN，显式生成undefined值（https://chromium-review.googlesource.com/c/7484969）
4. **[riscv][acqrel] Added atomic acquire load and release store instructions**  
   [RISC-V][内存屏障] 添加原子获取加载（acquire load）和释放存储（release store）指令（https://chromium-review.googlesource.com/c/7489051）
5. **[riscv][wasmfx] Retire empty target stack for resume_throw**  
   [RISC-V][wasmfx] 清理resume_throw流程中空的目标栈（https://chromium-review.googlesource.com/c/7484970）
6. **[riscv][sandbox] Migrate TrustedPointerTable to range-based type checks**  
   [RISC-V][沙箱] 将TrustedPointerTable迁移为基于范围的类型检查机制（https://chromium-review.googlesource.com/c/7495671）
7. **[riscv] Implement AssembleArchSelect**  
   [RISC-V] 实现AssembleArchSelect功能（https://chromium-review.googlesource.com/c/7502457）
8. **[riscv] Skip pop simd128 in DeoptimizationEntry**  
   [RISC-V] 在反优化入口（DeoptimizationEntry）中跳过simd128的出栈操作（https://chromium-review.googlesource.com/c/7498990）
9. **[riscv] Eliminate -Wexit-time-destructors warnings**  
   [RISC-V] 消除-Wexit-time-destructors编译警告（https://chromium-review.googlesource.com/c/7508964）
10. **[riscv] Implement FP16 in simulator**  
    [RISC-V] 在模拟器中实现FP16（半精度浮点）功能（https://chromium-review.googlesource.com/c/7266607）


## 版本测试及遗留问题

RuyiSDK 0.45.0 版本已通过[发版测试](https://gitee.com/yunxiangluo/ruyisdk-test/blob/master/20260120/README.md)。该版本测试是基于 0.45.0-beta.20260119 版本开展的，0.45.0
版本将基于 0.45.0-beta.20260119 版本代码发版。下面的表格记录了当前版本新增未修复缺陷：

| 缺陷      | 问题等级 |判定依据 |
| ----------- | ----------- | --- |
| [Occasional pygit2 failures during testing #415](https://github.com/ruyisdk/ruyi/issues/415) | 一般 | 已有 issue 回复 |

VSCode 插件版本测试基于 ruyisdk-vscode-extension [0.1.1-beta.1](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.1-beta.1) 测试版本开展手动测试，并以该版本为基础
发版。下面的表格记录了当前版本新增待改进内容，均已有修复计划：

| 缺陷 | 问题等级 | 备注 |
| ----- | ----- | ----- |
| [查看未读新闻命令失效 #106](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/106) | 建议 | 和 #108 为同一问题 |
| [新闻UI界面已读状态未更新 #108](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/108) | 建议 | 已知问题，已有修复计划 |

Eclipse 插件版本测试基于 ruyisdk-eclipse-plugins [v0.1.1](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.1) 版开展手动测试并发版。
下面的表格记录了当前版本新增待改进内容，和上一版本相比没有增减：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [命令执行提示框可以任意关闭且无法重新打开 #82](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/82)   | 建议 |   |
| [开发板选择框中开发板型号未排序 #83](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/83) | 建议 |  |
| [虚拟环境建立的项目绑定问题 #84](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/84) | 建议 |  |
| [安装插件时 Eclipse 提示未签名 #85](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/85) | 建议 |  |
| [打开 Ruyi Package Explorer 时必须选择某款开发板 #86](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/86) | 建议 |  |
| [虚拟环境建立的 quirks 过滤问题 #87](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/87) | 建议 |  |
| [虚拟环境建立的 ruyi update 错误处理问题 #88](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/88) | 建议 |  |
| [虚拟环境建立的 profile 排序问题 #89](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/89) | 建议 |  |
| [有一些可以自动获取的东西，不需要手动填写 #90](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/90) | 建议 |  |
| [RuyiSDK IDE 主文档的更新 #123](https://github.com/ruyisdk/docs/issues/123) | 一般 | 已有修复计划 |

参与当前版本测试的实习生：

+ [@Cyl18](https://github.com/Cyl18)
+ [@YXCZS](https://github.com/YXCZS)
+ [@jxy687](https://github.com/jxy687)
