# RuyiSDK 双周进展汇报 第 065 期·2026 年 03 月 24 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！
 
本期包管理器 0.47.0 发布，主要新增了多软件源（多仓库）支持，并修复了一些已知的问题。欢迎大家下载试用！

此外，[香山编译器正式接入RuyiSDK生态，深化协同构建全栈开发能力](https://mp.weixin.qq.com/s/MIFlZk3BqFBC6W72Cu5lGg)，也欢迎香山用户下载使用。



⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.47.0🚀
    * 从 [PyPI](https://pypi.org/project/ruyi/0.47.0/) 安装：`pip install ruyi`
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.47.0)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.47.0/)
    * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

    > [!NOTE]
    > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
    > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
    > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
    >
    > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

* RuyiSDK VSCode Extension 0.1.2
    * VSCode/VSCodium Extensions 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装 (Install from VSIX):
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
    * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.2
    * Eclipse Marketplace 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.2/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
    * [使用文档](https://ruyisdk.org/docs/IDE/)

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479 

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 4 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 包管理器
RuyiSDK 0.47 已于今日发布，对应的包管理器版本也为 0.47.0。 本次 RuyiSDK 包管理器的更新主要包含了以下内容：

- 新增多软件源（overlay）支持，允许厂商、企业、个人在官方软件源基础上叠加自定义软件源，并按优先级解析软件包。
- 修复单文件二进制发行版中 `rich` 模块缺失导致的运行时错误。
- 修复 `ruyi admin format-manifest` 对 `strip_components = 0` 的处理问题。
- 改进 `ruyi list profiles` 的输出，在多软件源环境下更清晰、更安全。
- 在 PyPI 的 `pyproject.toml` 中补充 SEO 关键字，便于在 PyPI 搜索到 Ruyi。

## IDE

### VSCode 插件

- [修复创建虚拟环境时 sysroot 缺失127](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/127)
- 重构虚拟环境 profile 提取逻辑

### Eclipse 插件

- 重构代码，集中插件内所有对 Ruyi 包管理器的调用，为将来铺路。
- 调研并编写代码测试基于 OIDC 的 Discourse 用户登录逻辑。

## GCC
- 提交了Zibi扩展的工具链支持，修复了RVP在RV32构建时intrinsic生成不正确的问题。

## LLVM

上游：
- [RISCV]Lower one active interleaved load to normal segmented load (#185602) https://github.com/llvm/llvm-project/pull/185602
生成stride load指令。已经合并
- [InstCombine] Fold fcmp (C - [su]itofp X), C to integer compares https://github.com/llvm/llvm-project/pull/185826
将含有整数转换成的浮点数的比较转换成整数比较。正在 review
- [PatternMatch][NFC] Add m_IToFP and m_FPToI https://github.com/llvm/llvm-project/pull/188040
新增 m_IToFP 和 m_FPToI 两个 IR 模式匹配函数。已经合并


P 扩展：
- add missing blank lines https://github.com/riscv/riscv-p-spec/pull/229
修复 P spec 文档格式错误，已合并。

- Minor fixes for typos and inconsistencies - https://github.com/topperc/p-ext-intrinsics/pull/2
修复 topperc P intrinsics spec 文档多处指令、函数名错误，以及一些格式修复，已合并。

## V8
本期提交的patch：
1. **[riscv][wasm] Fix walking WasmLiftoffSetupFrame**
   [RISC-V][WASM] 修复 WasmLiftoffSetupFrame 栈帧遍历问题（https://chromium-review.googlesource.com/c/7660033）
2. **[riscv][wasm] Really fix walking WasmLiftoffSetupFrame**
   [RISC-V][WASM] 彻底修复 WasmLiftoffSetupFrame 栈帧遍历问题（https://chromium-review.googlesource.com/c/7665010）
3. **[riscv] Optimize memory access for allocatable double registers in DeoptimizationEntry**
   [RISC-V] 在 DeoptimizationEntry 中优化可分配双精度寄存器的内存访问（https://chromium-review.googlesource.com/c/7669917）
4. **[riscv] Fix vector lmul calculation for RVV**
   [RISC-V] 修复 RVV 向量扩展的 LMUL 计算问题（https://chromium-review.googlesource.com/c/7669710）
5. **[riscv][liftoff] Separate floating-point and simd registers**
   [RISC-V][Liftoff] 分离浮点寄存器与 SIMD 寄存器（https://chromium-review.googlesource.com/c/7658971）
6. **[base] Refactor CPU detection code into architecture-specific files**
   [基础库] 将 CPU 检测代码重构至对应架构专用文件中（https://chromium-review.googlesource.com/c/7683553）
7. **[riscv][wasmfx] Trap on null for resume_throw_ref**
   [RISC-V][WasmFX] 为 resume_throw_ref 实现空指针陷阱（https://chromium-review.googlesource.com/c/7685620）
8. **[riscv][maps] Prepare for splitting MAP_TYPE into multiple values**
   [RISC-V][Maps] 为拆分 MAP_TYPE 为多个枚举值做准备（https://chromium-review.googlesource.com/c/7687330）
9. **[Reland "[riscv][superspread] port to riscv"]**
   [RISC-V][Superspread] 完成 RISC-V 架构移植（https://chromium-review.googlesource.com/c/7683933）

## 版本测试及遗留问题
