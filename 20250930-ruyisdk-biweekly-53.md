# RuyiSDK 双周进展汇报  第 053 期·2025 年 09 月 30 日

## 卷首语

## 包管理器

## IDE
**VSCode 插件：** 新增 VS Code 插件对 Ruyi 的检测与安装支持。主要包括：
- 新增 ruyi.detect 命令：启动自动检测，缺失时提示安装或打开指南
- 新增 ruyi.install 命令：通过 PyPI 安装/升级 Ruyi，仅支持 Linux
- 在 extension.ts 注册命令并触发检测
-  [feat: add Ruyi detect & install commands](https://github.com/ruyisdk/ruyisdk-vscode-extension/pull/1)

**Eclipse 插件：**
本期无新增特性，欢迎对Eclipse插件开发有兴趣的小伙伴加入开发团队，详情参考 [J159 RuyiSDK IDE 开发实习生](https://github.com/lazyparser/weloveinterns/blob/master/open-internships.md) ，期待您的加入。

## GCC

修复了Binutils中p扩展支持的一些编码问题，更新了GCC回归测试中发现的部分错误。
提交了Zvabd的binutils支持，正在处理Binutils寄存器对使用编号不正确的问题。

## LLVM

**upstream:**
- [[LLDB] Fix GetIndexOfChildMemberWithName to handle anonymous struct in base classes](https://github.com/llvm/llvm-project/pull/158256)

**xtheadvector:**
- [[LLVM][XTHeadVector] fix vwcvt, vwcvtu](https://github.com/ruyisdk/llvm-project/pull/163)

## V8
**PLCT提交并合入的patch：**
1. **[riscv] Fix SimdCrossCompilerDeterminismTest.TestTernOp failed.**  
   [RISC-V] 修复 SimdCrossCompilerDeterminismTest.TestTernOp 测试失败问题  
   [chromium-review.googlesource.com/c/6965545](https://chromium-review.googlesource.com/c/6965545)
2. **[riscv] Add Extension Zimop**  
   [RISC-V] 添加 Zimop 扩展  
   [chromium-review.googlesource.com/c/6955146](https://chromium-review.googlesource.com/c/6955146)
3. **[riscv] Fix build for v8_enable_external_code_space**  
   [RISC-V] 修复 v8_enable_external_code_space 的构建问题  
   [chromium-review.googlesource.com/c/6934203](https://chromium-review.googlesource.com/c/6934203)
4. **[riscv][wasmfx][jspi] Allow JSPI to suspend multiple stacks at once**  
   [RISC-V][wasmfx][JSPI] 允许 JSPI 同时挂起多个栈  
   [chromium-review.googlesource.com/c/6937846](https://chromium-review.googlesource.com/c/6937846)
5. **[riscv] Fix custom-descriptors-inlining.js failed**  
   [RISC-V] 修复 custom-descriptors-inlining.js 执行失败问题  
   [chromium-review.googlesource.com/c/6928701](https://chromium-review.googlesource.com/c/6928701)

**审阅并合入的patch：**
1. **[riscv] Only compile vlen intrinsic for RVV targets**  
   [RISC-V] 仅为 RVV 目标编译 vlen 内在函数  
   [chromium-review.googlesource.com/c/6959231](https://chromium-review.googlesource.com/c/6959231)
2. **[riscv] Fix IsNodeUnsigned bug**  
   [RISC-V] 修复 IsNodeUnsigned 函数的漏洞  
   [chromium-review.googlesource.com/c/6958729](https://chromium-review.googlesource.com/c/6958729)
3. **[riscv] Support architectures with 256-bit vector units**  
   [RISC-V] 支持带有 256 位向量单元的架构  
   [chromium-review.googlesource.com/c/6948289](https://chromium-review.googlesource.com/c/6948289)
4. **[riscv] Replace more auipc+jalr into addi+jal**  
   [RISC-V] 将更多 auipc+jalr 指令组合替换为 addi+jal  
   [chromium-review.googlesource.com/c/6874383](https://chromium-review.googlesource.com/c/6874383)
5. **[riscv] Refactor WASM Simd128 operations**  
   [RISC-V] 重构 WebAssembly 的 Simd128 操作  
   [chromium-review.googlesource.com/c/6948067](https://chromium-review.googlesource.com/c/6948067)
6. **[riscv] Add more checks in IsNodeUnsigned to eliminate slli instructions**  
   [RISC-V] 在 IsNodeUnsigned 中添加更多检查以消除 slli 指令  
   [chromium-review.googlesource.com/c/6933681](https://chromium-review.googlesource.com/c/6933681)
7. **[riscv] Fix compilation error and disassembling error when enabling the RISC-V C extension**  
   [RISC-V] 修复启用 RISC-V C 扩展时的编译错误和反汇编错误  
   [chromium-review.googlesource.com/c/6934163](https://chromium-review.googlesource.com/c/6934163)

## 操作系统支持矩阵

- [Mars: debian: add trixie (mainline version)](https://github.com/ruyisdk/support-matrix/pull/367)
- [Add Tizen](https://github.com/ruyisdk/support-matrix/pull/368)
- [Bit-Brick_K1,LicheePi4A@OpenKylin 2.0 SP2](https://github.com/ruyisdk/support-matrix/pull/369)
- [Test LicheePi4A/Tizen](https://github.com/ruyisdk/support-matrix/pull/370)
- [Update mangopi_mq](https://github.com/ruyisdk/support-matrix/pull/371)
- [test LicheePi3A: Bianbu Desktop/Desktop Lite](https://github.com/ruyisdk/support-matrix/pull/372)
- Opennovation.org 工程软件在 RISC-V 上的测试验证：https://github.com/QA-Team-lo/engineering-riscv

## 版本测试及遗留问题

RuyiSDK 0.41.0 版本已通过[发版测试](https://gitee.com/yunxiangluo/ruyisdk-test/blob/master/20250922/README.md)。该
版本测试是基于 0.41.0-beta.20250922 和 0.41.0-beta.20250926 两个测试版本开展的，预期 0.41.0 版本将基于
 0.41.0-beta.20250926 版本代码发版。下面的表格记录了 0.41.0-beta.20250922 版本缺陷，该缺陷已在 0.41.0-beta.20250926
版本修复：

| 缺陷      | 问题等级 |判定依据 |
| ----------- | ----------- | --- |
| [[Feature Request] Provide information prompts when automatically running ruyi update #352](https://github.com/ruyisdk/ruyi/issues/352) | 修复 | 在 0.41.0-beta-20250926 修复 |

同时可以参考下面的表格来跟踪历史遗留问题的修复进度：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [关于 fastboot 的文档提示 #95](https://github.com/ruyisdk/docs/issues/95)   | 严重 | 建立新的 [issue](https://github.com/ruyisdk/ruyisdk/issues/52) 进行更新，且已拟订相关修复版本号为 0.42.0 版本  |
| [关于使用 pip 安装 ruyi 的文档提示 #96](https://github.com/ruyisdk/docs/issues/96)   | 严重 | 已有文档整体更新计划，已有具体时间节点和时间表安排  |
| [有一部分包无法下载 #37](https://github.com/ruyisdk/packages-index/issues/37)     | 一般 | 已有相关 issue 回复且已经在修复中 |
| [BananaPi BPI-F3 eMMC storage variant did not refer to any combo #101](https://github.com/ruyisdk/packages-index/issues/101)     | 一般 | 软件自带修复功能，且已有相关 issue 回复 |

这些遗留问题并不会影响 Ruyi 包管理器核心功能的实现，但可能影响用户体验，故建议在下载和更新您的 Ruyi 包管理器版本前了
解。其中 packages-index 相关问题将主要影响 ``ruyi device provision`` 功能，请不要使用 ``BananaPi BPI-F3`` 开发板的
 ``BananaPi BPI-F3 (eMMC storage)`` 镜像和 ``Pine64 Star64`` 开发板的 ``Armbian for Pine64 Star64`` 镜像，相关缺陷修
复后可以通过 ``ruyi update`` 解决。
