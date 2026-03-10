# RuyiSDK 双周进展汇报 第 064 期·2026 年 03 月 10 日

## 卷首语

## 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.47.0 版本预期将在 3 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.46.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增软件包：
    * `toolchain/xscc`: XSCC 编译器，由香山编译器（计算所与开芯院联合）团队提供。此软件包仅支持 `x86_64` 架构。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权限的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

- 多版本管理对不受支持的Ruyi包管理器版本添加outdated标记
- 上架 [Open VSX](https://open-vsx.org/extension/RuyiSDK/ruyisdk-vscode-extension)
- 发布 0.1.2 版本！

### Eclipse 插件

- 重写项目中英文文档。
- 支持在内置的终端内执行 ruyi device provision 程序。
- 引入 Maven Wrapper 管理 Maven 并更新相关配置。
- 引入 PMD 对代码做静态分析，移除未使用的函数和变量。

## GCC

- 更新了Binutils版本到2.46 release
- Rebase了Svrsw60t59b和Zibi扩展的Binutils实现.

## LLVM

- [IA][RISCV] Make the isDeInterleaveMask check the contents of shuffle
 https://github.com/llvm/llvm-project/pull/185384
- [InstCombine] make foldBinOpIntoSelectOrPhi fold on all operands
 https://github.com/llvm/llvm-project/pull/183692

## V8
本期亮点：
下文提到的第5项代码提交，将JSToWasmInterpreterWrapper迁移至Torque语言， 统一了V8内置组件的开发范式。这意味着如意V8团队作为RISC-V架构维护者不再仅局限于“适配移植”层面，而是开始深度跟进并参与到V8核心主体功能（WASM解释器核心逻辑）的架构改进与原生实现中，为后续RISC-V架构下V8核心功能的原生优化奠定了基础。

本期提交的patch：
1. **[riscv][sandbox] Fix CrashFilter to detect ASAN shadow memory addresses**  
   [RISC-V][沙箱] 修复 CrashFilter 使其能检测 ASAN 影子内存地址（https://chromium-review.googlesource.com/c/7641970）
2. **[riscv][ic] Introduce homomorphic state for ICs sharing a handler**  
   [RISC-V][内联缓存] 为共享处理程序的内联缓存（IC）引入同态状态（homomorphic state）（https://chromium-review.googlesource.com/c/7623545）
3. **[riscv][jspi] Clear EPT entry on stack return**  
   [RISC-V][JSPI] 在栈返回时清空 EPT（扩展页表）表项（https://chromium-review.googlesource.com/c/7608971）
4. **[riscv][maglev] Handle equal inputs in Float64Max/Min**  
   [RISC-V][Maglev编译器] 处理 Float64Max/Min 操作中输入值相等的场景（https://chromium-review.googlesource.com/c/7599842）
5. **[wasm-interpreter] Port JSToWasmInterpreterWrapper into torque**  
   [WASM解释器] 将 JSToWasmInterpreterWrapper 迁移至 Torque 语言实现（https://chromium-review.googlesource.com/c/v8/v8/+/7455469）
   ### 格式化提交记录
6. **[riscv] Remove kCArgsSlotsSize/kCArgSlotCount**  
   [RISC-V] 移除 kCArgsSlotsSize/kCArgSlotCount 两个常量（https://chromium-review.googlesource.com/c/v8/v8/+/7649603）

## 版本测试及遗留问题

本版本基于 ruyisdk-vscode-extension [v0.1.2-beta.1](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.2-beta.1) 开展手动测试。

测试报告见 [针对RuyiSDK VSCode插件的测试](https://github.com/ruyisdk-test/ruyisdk-vscode-extension-test/blob/v0.1.2/README.md)

新增缺陷：

| 缺陷 | 问题等级 | 备注 |
| --- | --- | --- |
| [创建虚拟环境时profile中文乱码 #122](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/122) | 一般 | 已有修复 commit |
| [同时安装ruyi最新版和其他版本时，启动旧版ruyi会提示更新ruyi最新版。 #115](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/115) | 一般 | 已有 issue 回复  |

