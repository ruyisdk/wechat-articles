# RuyiSDK 双周进展汇报 第 063 期·2026 年 02 月 24 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家马年吉祥，开工大吉！

今天 RuyiSDK 团队结束新春假期，已经逐步恢复到正常的开发节奏中来。在这里先给大家拜个晚年：㊗️各位在新的一年里，身体健康、工作顺利、代码无 Bug、提交顺利合！🎉

新的一年，我们将继续以社区需求为导向，稳步完善包管理器与 IDE 工具链体验，拓展对更多 RISC-V 设备与系统场景的支持，也欢迎大家多在[社区](https://ruyisdk.cn/)提出需求、分享使用体验，一起把 RuyiSDK 打造成更顺手、更可靠的 RISC-V 开发工具箱。


⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.46.0
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

* RuyiSDK VSCode Extension 0.1.1
    * VSCode Extensions 中搜索 `RuyiSDK`或者`RISC-V`等关键字查询 安装 RuyiSDK 插件
    * 手动下载安装 (Install from VSIX):
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.1/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
    * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.2
    * Eclipse Marketplace 中搜索 `RuyiSDK`或者`RISC-V`等关键字查询 安装 RuyiSDK 插件
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
    * [使用文档](https://ruyisdk.org/docs/IDE/)

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479 

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 3 月底发布，我们将持续给您带来更新！

## 包管理器
本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 修复了 `ruyi admin format-manifest` 命令会错误丢弃 `strip_components = 0` 属性的问题，该修复将于 ruyi 的下一个正式版发布。

## IDE

### VSCode 插件
新的插件包正在测试中，预计月底将发布上架，主要更新包括：
- 添加新人引导
- 优化新闻读取逻辑（使用porcelain mode）

### Eclipse 插件

- 调整 Update Site 更新策略。
- 虚拟环境模块将自动刷新工作区。
- 重构日志模块。

## GCC
  更新了Binutils模块至2.46版本，Glibc模块至2.43版本，正在修复回归测试中发现的错误。

## LLVM

upstream 进展：

- [RISC-V] Add riscv_simd.h for P extension intrinsics https://github.com/llvm/llvm-project/pull/181115

## V8
本期提交的patch：
1. **[riscv][ic] Introduce CallNamedInterceptorGetter builtin**  
   [RISC-V][内联缓存] 新增 CallNamedInterceptorGetter 内置函数（https://chromium-review.googlesource.com/c/7557490）
2. **[riscv][wasm][shared] Add waitqueue type and get/set**  
   [RISC-V][WASM][共享内存] 添加 waitqueue 类型及对应的获取/设置方法（https://chromium-review.googlesource.com/c/7561255）
3. **[riscv] Refactor popcnt implementation in Turbofan**  
   [RISC-V] 重构 Turbofan 编译器中 popcnt（位计数）功能的实现（https://chromium-review.googlesource.com/c/7567282）
4. **[riscv][wasmfx] Implement resume_throw_ref**  
   [RISC-V][wasmfx] 实现 resume_throw_ref 功能（https://chromium-review.googlesource.com/c/7573930）
5. **[riscv] Reland "[wasm][turboshaft] Optimize code generator for unconditional traps"**  
   [RISC-V][wasm][turboshaft] 优化无条件陷阱的代码生成器（https://chromium-review.googlesource.com/c/7599841）
6. **[riscv][wasm] Improve write-barrier treatment**  
   [RISC-V][WASM] 优化写屏障（write-barrier）的处理逻辑（https://chromium-review.googlesource.com/c/7599840）
7. **[riscv][builtins] Fix stack overflow handling in ResumeGeneratorTrampoline**  
   [RISC-V][内置函数] 修复 ResumeGeneratorTrampoline 中栈溢出的处理逻辑（https://chromium-review.googlesource.com/c/7599839）
8. **[riscv] Add WasmCodePointer bounds masking**  
   [RISC-V] 为 WasmCodePointer 添加边界掩码（bounds masking）机制（https://chromium-review.googlesource.com/c/7566742）

