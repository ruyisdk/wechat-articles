# RuyiSDK 双周进展汇报 第 062 期·2026 年 02 月 10 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！

金蛇辞旧，骏马迎新。在这辞旧迎新的美好时节，首先㊗️**大家新春快乐，阖家幸福，万事如意！** 🎉

本期是农历乙巳年的最后一次更新。回首这一年，RuyiSDK 一步一个脚印，稳步前行：包管理器基础功能逐步成熟稳定，现已支持完整的插件架构和本地化（i18n）特性，让中文开发者使用更加亲切；VSCode 和 Eclipse 插件从零起步，如今双双上架官方市场，为不同偏好的开发者提供便利的工具支持。

在底层技术生态方面，我们持续深耕，围绕 RISC-V 扩展指令集进行了大量的实现与优化工作：推动 GNU 工具链对更多扩展特性的支持，向 LLVM 上游提交了多项编译器优化补丁，并显著提升了 V8 引擎及 Node.js 在 RISC-V 平台上的稳定性与兼容性。

这个过程离不开社区伙伴的支持和贡献，每一份代码提交、每一个问题反馈，都是推动 RuyiSDK 向前的重要力量。

展望 2026 年，我们将持续打磨产品体验，增加对更多设备的支持，共同丰富 RuyiSDK 的软件生态。

**本期主要更新亮点包括：** 包管理器 0.46.0 版本发布，新增完整的中文本地化支持；Eclipse 插件成功登陆 Eclipse Marketplace（VSCode插件新版本虽迟但会到，将另行告知）；V8 引擎多项优化补丁合入上游，Node for RISC-V 稳定性显著提升。更多更新详见下方，欢迎大家下载体验。

⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.46.0🚀
    * 从 [PyPI](https://pypi.org/project/ruyi/0.46.0/) 安装：`pip install ruyi`
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.46.0)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.46.0/)
    * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

    > [!NOTE]
    > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
    > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
    > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
    >
    > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

* RuyiSDK VSCode Extension 0.1.1 （本期未同步更新）
    * VSCode Extensions 中搜索 `RuyiSDK`或者`RISC-V`等关键字查询 安装 RuyiSDK 插件
    * 手动下载安装 (Install from VSIX):
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.1/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
    * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.2🚀
    * Eclipse Marketplace 中搜索 `RuyiSDK`或者`RISC-V`等关键字查询 安装 RuyiSDK 插件
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
    * [使用文档](https://ruyisdk.org/docs/IDE/)

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 3 月底发布，我们将持续给您带来更新！

🎊  **新春佳节，瑞气盈门。愿您在新的一年里，代码无 Bug，提交顺利合，生活美满，事业腾飞！** 🎊


## 包管理器

RuyiSDK 0.46 已于今日发布，对应的包管理器版本也为 0.46.0。

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 完善了插件架构，现已支持包管理器插件内字符串的本地化：
    * 新增 `RUYI.has_feature()` 以便探测特定的功能特性是否受到当前运行环境支持。为支持旧版
      RuyiSDK 包管理器，您可首先使用 `hasattr(RUYI, "has_feature")` 检查该方法是否存在，再进行使用（不然您的插件则会崩溃）；如该方法不存在，则您所要探测的功能肯定不受支持。
    * 新增 `i18n-v1` 功能特性，对应新增的 `RUYI.i18n` 接口：
        * `RUYI.i18n.locale: str` 是当前运行环境的区域（locale）取值；
        * `RUYI.i18n.msg(msgid: str, locale: str | None = None) -> str | None`
          从当前软件源的 `messages.toml` 查询给定 ID 在给定 locale（默认为当前 locale）的消息字符串。目前建议用
          `format()` 方法对取得的字符串进行变量替换（格式化）。
* 您在 PyPI 上可以用更多关键词搜索到我们了。
* 工程化迭代：
    * 为 CI 任务的执行环境配置了初步的安全加固措施，其中包含初步的网络流量审计，以预防 CI 相关的供应链攻击。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 为 RuyiSDK 设备安装器所用到的插件增加了完整的简体中文支持。
* 更新软件包：
    * `toolchain/gnu-upstream`: RuyiSDK 从上游源码构建的 GNU 工具链，0.20260201.0 版本。包含 GNU binutils 2.45、GCC 15.2.0 以及 glibc 2.43。
* 完善了设备支持：
    * Sipeed LicheeRV Nano 的 Buildroot SDK: 更新到 20260114。感谢 [@smullllu] 的贡献！

[@smullllu]: https://github.com/smullllu

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

- 添加新人引导
- 优化新闻读取逻辑（使用porcelain mode）
- 添加关键词以便VSCode marketplace搜索

### Eclipse 插件

- 上架 Eclipse Marketplace 并更新文档: https://marketplace.eclipse.org/content/ruyisdk 。
- 调整 Ruyi 安装向导中错误的按钮状态。
- 更新依赖的第三方库和 Maven 插件，限制构建环境为 Linux Java 21+ 。

## GCC
提交了 svrsw60t59b 扩展支持及 Zibi 扩展的RFC patch，等待新版本 binutils 合入中。

## LLVM

upstream 进展：

- [InstCombine] fold gepi _, (srem x, y) to gepi _, (urem x, y) if y is power-of-2  https://github.com/llvm/llvm-project/pull/180148
- [DAGCombiner] Fold trunc(build_vector(ext(x), ext(x)) -> build_vector(x,x)#179857 
https://github.com/llvm/llvm-project/pull/179857

## V8
本期亮点：来自软件所的工程师 wangruikang 解决了node.js长久以来存在的疑难bug（ https://ruyisdk.cn/t/topic/403 ）， patch提交至上游并合入（CL7540554），Node for RISC-V 的稳定性得到提升。
本期提交的patch：
1. **[riscv] Only Enable CheckMemoryAccess in V8_COMPRESS_POINTERS mode**  
   [RISC-V] 仅在 V8_COMPRESS_POINTERS 模式下启用 CheckMemoryAccess 功能（https://chromium-review.googlesource.com/c/7555683）
2. **[riscv] Fix ACCESS BELOW STACK POINTER error**  
   [RISC-V] 修复“访问栈指针下方内存”的错误（https://chromium-review.googlesource.com/c/7550210）
3. **[riscv] Add check stack pointer when access memory**  
   [RISC-V] 新增内存访问时的栈指针检查逻辑（https://chromium-review.googlesource.com/c/7543083）
4. **[riscv][baseline] Inline fast ToBoolean checks for Smis and static roots**  
   [RISC-V][基线编译器] 为 SMI 和 静态根对象 内联快速 ToBoolean 检查逻辑（https://chromium-review.googlesource.com/c/7543084）
5. **[riscv][ic] Introduce CallNamedInterceptorSetter builtin**  
   [RISC-V][内联缓存] 新增 CallNamedInterceptorSetter 内置函数（https://chromium-review.googlesource.com/c/7540545）
6. **[riscv][wasmfx] Implement cont.bind.**  
   [RISC-V][wasmfx] 实现 cont.bind 功能（https://chromium-review.googlesource.com/c/7538513）
7. **[riscv] Skip assembler tests when extension been not supported**  
   [RISC-V] 当扩展未被支持时跳过汇编器测试（https://chromium-review.googlesource.com/c/7533867）
8. **[riscv][wasmfx] Prepare arg buffer for cont.bind**  
   [RISC-V][wasmfx] 为 cont.bind 准备参数缓冲区（https://chromium-review.googlesource.com/c/7533863）
9. **[riscv][cleanup] Use EnumSet<CpuFeature> in multiple places**  
   [RISC-V][代码清理] 更广泛地使用 EnumSet<CpuFeature> 优化代码（https://chromium-review.googlesource.com/c/7529664）
10. **[riscv] Implement word64/word32 Select for Tst/CmpZero operations**  
    [RISC-V] 为 Tst/CmpZero 操作实现 word64/word32 类型的 Select 功能（https://chromium-review.googlesource.com/c/7515447）
11. **[riscv] Fix CWasmEntry uses wrong root register**  
    [RISC-V] 修复 CWasmEntry 误用根寄存器的问题（https://chromium-review.googlesource.com/c/7519177）

本期审核并合入的patch：
1. **[riscv] Fix ISA feature parsing error from /proc/cpuinfo**  
   [RISC-V] 修复从 `/proc/cpuinfo` 文件解析 ISA 特性时的错误（https://chromium-review.googlesource.com/c/7320200）
2. **[riscv] Support fractional LMUL check in simulator**  
   [RISC-V] 在模拟器中支持分数型 LMUL（向量长度乘数）的校验逻辑（https://chromium-review.googlesource.com/c/7531795）
3. **[riscv] Fix sp handling in MacroAssembler::LeaveFrame**  
   [RISC-V] 修复 MacroAssembler::LeaveFrame 方法中栈指针（sp）的处理逻辑问题（https://chromium-review.googlesource.com/c/7540554）
4. **[riscv] Fix illegal instruction caused by unsupported SEW and LMUL configuration**  
   [RISC-V] 修复因不支持的 SEW（向量元素宽度）和 LMUL 配置组合导致的非法指令问题（https://chromium-review.googlesource.com/c/7502635）

## 版本测试及遗留问题
