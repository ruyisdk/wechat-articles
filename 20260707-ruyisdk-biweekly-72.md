# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

## 卷首语

## 基础开发环境

### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.51.0 版本预期将在 7 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.50.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* 迁移大部分 RuyiSDK 打包脚本到新的 `ruyi admin build-package` 打包工作流。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新软件包：
    * `analyzer/dynamorio-riscv`: DynamoRIO RISC-V 性能分析工具，11.91.20630 版本。
    * `board-util/wlink`: 社区独立实现的 WCH-Link 刷写与调试工具，0.1.2 版本。
    * `source/opencv`: OpenCV 上游源码，4.13.0 版本。感谢 [Tanmay Gulhane][trg-rgb] 的贡献！
    * `toolchain/gnu-ruyisdk`: 由 RuyiSDK 团队维护、构建的 GNU 工具链，0.20260625.0 版本。在 GNU binutils 2.46、GCC 16.1.1、glibc 2.43 的基础上支持了所有 2026 年 6 月前已批准（ratified）的 RISC-V 扩展。
    * `toolchain/llvm-ruyisdk`: 由 RuyiSDK 团队维护、构建的 LLVM 工具链，0.20260625.0 版本。在 LLVM 22.1.8 的基础上支持了所有 2026 年 6 月前已批准（ratified）的 RISC-V 扩展，具体是新增了对 Svrsw60t59b 与 Ziccid 的支持。
* 新增设备支持：
    * SpacemiT K3 Pico-ITX: 兼容各类 Bianbu 镜像。感谢 [weilinfox][weilinfox] 的贡献！
* 完善了设备支持：
    * `board-image/armbian-starfive-visionfive2-minimal`: StarFive VisionFive2 的 Armbian。感谢 [SmulllLu][smullllu] 的贡献！

[smullllu]: https://github.com/SmulllLu
[trg-rgb]: https://github.com/trg-rgb
[weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### RuyiSDK VSCode 插件

- 更新 i18n 翻译
- 抑制启动时 ruyi detect 信息
- 支持新闻阅读本地已有缓存
- 新增为虚拟环境的 sysroot 使用 projection 
- 新增软件源管理

### RuyiSDK Eclipse 插件

- 项目: 发布 0.1.5 。
- venv: 支持新的 sysroot 配置方式。
- venv: 根据是否包含 sysroot 筛选列出的工具链。
- venv: 让用户在向导中始终检查虚拟环境文件夹的名称。
- venv: 向项目右键菜单中添加删除 venv 的操作。
- packages: 从树中移除多余的有关包状态的提示内容。

### 版本测试及遗留问题

0.50.0 版本延迟测试发布的 VSCode 插件测试[报告](https://github.com/ruyisdk-test/ruyisdk-vscode-extension-test/tree/v0.1.5)。

VSCode 插件新增缺陷：

| 缺陷 | 问题等级 | 备注 |
| --- | --- | --- |
| [抑制如意侦测消息后重启方式 #180](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/180) | 建议 |  |
| [管理仓库中对系统仓库（ruyisdk）的操作失败 #181](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/181) | 建议 |  |
| [删除ruyi cli的新闻阅读状态后，扩展的新闻状态仍是已读 #182](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/182) | 建议 |  |
| [ruyi news界面左上角为英文 #183](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/183) | 建议 |  |
| [Ruyi board docs 扩展页为英文 #186](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/186) | 建议 |  |
| [ruyi venv 列表emulator和toolchain列表版本标签英文 #187](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/187) | 建议 |  |
| [Ruyi 新闻搜索提示英文 #188](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/188) | 建议 |  |

延迟发布的 Eclipse 插件测试[报告](https://github.com/ruyisdk-test/ruyisdk-eclipse-plugins-test/tree/v0.1.5)。

Eclipse 插件遗留缺陷：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [命令执行提示框可以任意关闭且无法重新打开 #82](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/82)   | 建议 |   |
| [虚拟环境建立的项目绑定问题 #84](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/84) | 建议 |  |
| [安装插件时 Eclipse 提示未签名 #85](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/85) | 建议 |  |
| [有一些可以自动获取的东西，不需要手动填写 #90](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/90) | 建议 |  |
| [UI：新闻界面切换仅未读“勾号”不明显 #98](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/98) | 建议 |  |
| [ruyi-venv中的venv path需要手动点击右侧列表，显示项目路径 #152](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/152) | 建议 |  |
| [ruyi-venv名称可以默认设置为ruyi-venv-profile属性 #153](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/153) | 建议 |  |

Eclipse 插件新增缺陷：

| 缺陷 | 问题等级 | 备注 |
| --- | --- | --- |
| [New Virtual environment添加虚拟环境时响应时间过长 #177](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/177) | 建议 |  |
| [venv创建Ruyi-venv名称默认情况下finish按钮报错 #178](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/178) | 建议 |  |
| [在使用不包含 sysroot 的工具链 （例如 xscc） 时，可通过指定其他工具链，此时仍包含xscc #179](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/179) | 建议 |  |
| [eclipse 插件暂不支持0.49版本ruyi的复制，软连接，rootfs投影方式 #180](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/180) | 建议 |  |

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 strpbrk 和 strspn 的通用版本 RVV 优化。
  - 在阿里玄铁 C908 平台进一步调优了基于 RVV 和 xthead 标量访问扩展的 memcpy 平台特定优化，并完成了 memset 和 memmove 的初步调优。
- newlib:
  - 先前提交到 newlib 上游的 rawmemchr, memcmp 的通用版本 RVV 优化已合入主线（https://sourceware.org/pipermail/newlib/2026/022437.html）。
  - 移植了 atanh 到当前的 newlib 向量数学库框架。

### GCC
- 完成了ruyisdk-gcc 16.1，ruyisdk-binutils 2.46的整合工作，支持多种新扩展及全面的RV Profiles
  - https://github.com/ruyisdk/riscv-gcc
  - https://github.com/ruyisdk/riscv-binutils
- Rebase了Zcmt的Binutils支持，重新设计了link relaxation实现
  - https://sourceware.org/pipermail/binutils/2026-June/149842.html
- 提交了Zama16b和Ziccamoc扩展的支持patch
  - https://sourceware.org/pipermail/binutils/2026-June/149847.html
  - https://sourceware.org/pipermail/binutils/2026-June/149848.html
- 修复了Zvdota扩展的altfmt识别问题，已合入上游
  - https://sourceware.org/git/?p=binutils-gdb.git;a=commit;h=cd28fb866379c5dbbe431feb24aa62d369554f80
- 正在推进P扩展的intrinsic支持更新中
  - https://github.com/ruyisdk/riscv-gcc/pull/12
### LLVM
- [compiler-rt][msan] Add MSan support for RISC-V 64-bit Linux | https://github.com/llvm/llvm-project/pull/206674 提供RISC-V msan 功能

本期提交 PR 如下：

1. [RISCV][P-ext] Select signed widening add/sub accumulate to wadda/wsuba
https://github.com/llvm/llvm-project/pull/205475
添加 wadda/wsuba 的 codegen 支持
已合并

2. [RISCV][P-ext] Add codegen for packed reduction sum
https://github.com/llvm/llvm-project/pull/206004
添加 packed reduction sum (predsum[u].*)的 codegen 支持
已合并

3. [RISCV][P-ext] Avoid redundant accumulator extend for reduction sum
https://github.com/llvm/llvm-project/pull/206430
优化 reduction sum 生成的多余 sext.w/zext.w 指令
已合并

4. [Clang][RISCV] packed reduction sum intrinsics
https://github.com/llvm/llvm-project/pull/206441
添加 packed reduction sum 的 intrinsic 支持
已合并

5. [RISCV][P-ext] Support Packed Merge.
https://github.com/llvm/llvm-project/pull/207110
添加  Packed Merge 的 intrinsic 支持
已合并

6. [RISCV][P-ext] Use brev8 for bitreverse with Zbkb
https://github.com/llvm/llvm-project/pull/207338
当存在 Zbkb 拓展时将 bitreverse 下降为 brev8 指令，完成 FIXME
已合并

7. [RISCV] Canonicalize the true operand of vselect to fold more vmerge.vvm instructions
https://github.com/llvm/llvm-project/pull/206449
将 vselect 的 true 操作数规范化，以便折叠更多的 vmerge.vvm 指令
已合并

8. [VectorCombine] Use TCK_CodeSize for size-optimized functions
https://github.com/llvm/llvm-project/pull/202207
改进 size-optimized functions 下 VectorCombine 的成本模型选择，使其使用 `TCK_CodeSize`
已合并

9. [VectorCombine] foldShuffleChainsToReduce - add FADD/FMUL handling
https://github.com/llvm/llvm-project/pull/201302
为 `foldShuffleChainsToReduce` 增加 `FADD`/`FMUL` 处理，提升向量归约链折叠能力
已合并

10. [CodeGen] Fix ShrinkWrap crash when FindIDom receives empty predecessor/successor list
https://github.com/llvm/llvm-project/pull/198995
修复 ShrinkWrap 在 `FindIDom` 收到空 predecessor/successor 列表时的崩溃问题
已合并

11. [LV][RISCV] Add crash test for wide pointer stride in convertToStridedAccesses
https://github.com/llvm/llvm-project/pull/200985
为 `convertToStridedAccesses` 中 wide pointer stride 场景补充 RISC-V 崩溃回归测试
已合并

12. [RISCV][P-ext] Support packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207574
支持 packed reverse intrinsics
正在 review

13. [RISCV][P-ext] Improve codegen for packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207575
优化  packed reverse intrinsics codegen
正在 review

14. [RISCV][P-ext] Add codegen for packed absolute difference sum
https://github.com/llvm/llvm-project/pull/207314
添加 packed absolute difference sum codegen 支持
正在 review

15. [RISCV][LLVM][Clang] Add experimental Zvvm config intrinsics
https://github.com/llvm/llvm-project/pull/203774
添加 Zvvm config 相关 intrinsics 支持
正在 review，遇到和LLVM上游和RISC-V规范冲突问题，暂时需要等待规范更新


### V8

本期提交patch如下：
1. **[riscv] sandbox: Replace CPT with TPT**
   [RISC-V][沙箱] 将代码指针表（CPT）替换为可信指针表（TPT）（https://chromium-review.googlesource.com/c/7983344）

2. **[riscv] Add RISC-V ZVFH extension to CPU feature list**
   [RISC-V] 将ZVFH向量半精度浮点扩展添加至CPU特性标识列表（https://chromium-review.googlesource.com/c/7980709）

3. **[riscv][maglev] Sign extend index register in DataView bounds check**
   [RISC-V][Maglev] 在DataView边界校验逻辑中对索引寄存器执行符号扩展（https://chromium-review.googlesource.com/c/7980016）

4. **[Revert "[riscv][maglev] Sign extend index register in DataView bounds check"]**
   [回退提交] 撤销上一条Maglev索引寄存器符号扩展修改（https://chromium-review.googlesource.com/c/7992036）

5. **[Reland [riscv][maglev] Sign extend index register in DataView bounds check]**
   [重提提交] 重新合入Maglev索引寄存器符号扩展修复（https://chromium-review.googlesource.com/c/7992037）

6. **[riscv] Enable ZVFH support for Liftoff WebAssembly SIMD**
   [RISC-V] 为Liftoff WebAssembly SIMD开启ZVFH向量半精度浮点扩展支持（https://chromium-review.googlesource.com/c/7980710）

7. **[riscv][wasm][jspi] Initialize suspend builtin return value**
   [RISC-V][WASM][JSPI] 初始化线程挂起内置函数的返回值（https://chromium-review.googlesource.com/c/8017623）

8. **[riscv]Implement fp16 rounding operations for RISCV**
   [RISC-V] 实现半精度浮点（fp16）舍入运算指令（https://chromium-review.googlesource.com/c/8017624）

9. **[riscv] Unify floating-point rounding ops to support fp16**
   [RISC-V] 统一浮点舍入运算底层逻辑，新增fp16半精度浮点适配（https://chromium-review.googlesource.com/c/8028101）

10. **[riscv][compiler] Scheduler resource allocation table**
    [RISC-V][编译器] 新增指令调度器资源分配表（https://chromium-review.googlesource.com/c/8037086）
### OpenJDK

本期提交的JDK-25u主线patch:
- https://github.com/openjdk/jdk25u-dev/pull/541 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台回合Shenandoah GC一处load_reference_barrier调用对象错误问题修复

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30865 (8382691: RISC-V: Clean up redundant restore_locals() in TemplateTable::invokeinterface)  为ARM64和RISC-V平台移除一处模板解释器接口函数调用场景非必要的locals变量恢复操作以提升性能
- https://github.com/openjdk/jdk/pull/30837 (8382606: Enable VectorMinMaxTransforms.java IR tests for RISC-V)  为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30823 (8382522: Disable stringop-overflow in safepointMechanism.cpp)  为RISC-V平台修复一处GCC编译器构建JDK报警问题
- https://github.com/openjdk/jdk/pull/30634 (8377715: Thawing frame can undo deoptimization)  为RISC-V平台打开一项掩码版本矢量访存白盒测试用例
- https://github.com/openjdk/jdk/pull/30893 (8382878: RISC-V: Missing InlineSkippedInstructionsCounter in ZGC barriers stubs)  为RISC-V平台修复一处ZGC场景内敛指令数评估准确性问题
- https://github.com/openjdk/jdk/pull/30901 (8382934: LateInlineQueueDrainTest.java fails without diagnostic option)  修复一处jtreg回归测试用例选项设置缺陷
- https://github.com/openjdk/jdk/pull/30890 (8380753: C2: RegMask::find_first_set() incorrectly returns partially contained sets for scalable vector registers)  为ARM64和RISC-V平台修复一处C2 JIT编译器可扩展矢量寄存器分配问题
- https://github.com/openjdk/jdk/pull/30945 (8383196: Shenandoah: Interpreter barriers clobber interpreter registers)  为ARM64和RISC-V平台修复一处模板解释器场景寄存器使用缺陷
- https://github.com/openjdk/jdk/pull/30990 (8383601: RISC-V: ShenandoahBarrierSetAssembler::load_reference_barrier calls "weak" on "phantom" path)  为RISC-V平台修复一处Shenandoah GC一处load_reference_barrier调用对象错误问题

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台模板解释器模块对JEP 401的支持，能够在纯解释模式下跑通JEP 401相关测试用例，成功通过兼容性测试。
目前已着手调试和实现RISC-V平台C1& C2 JIT模块对JEP 401的支持，优先解决兼容性问题，短期目标能够在解释模式下跑通JEP 401新增测试用例。
本期详细修改如下：
- https://github.com/openjdk/valhalla/commit/2e7c204830c23d9b88daee1a7926aed9ad99ea8b 
- https://github.com/openjdk/valhalla/commit/39763548c92ec744e31edc4b52aa42275414d8ad 
- https://github.com/openjdk/valhalla/commit/9bda478af718f97e396f7f40a4a2a2c33d71afbc 
- https://github.com/openjdk/valhalla/commit/de1c6297cec79d18b5800187d3c504ae06c027ce 

### Go

- 796060: runtime: enable vgetrandom vDSO support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/796060  开启 vdso 提升 crypto 性能
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 启动sigaction

### QEMU模拟器
- target/riscv/kvm: skip FP/Vector sync on KVM_PUT_RUNTIME_STATE 减少寄存器同步压力
