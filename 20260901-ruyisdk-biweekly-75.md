# RuyiSDK 双周进展汇报 第 075 期 · 2026 年 09 月 01 日

## 卷首语

>

## 基础开发环境


### 包管理器

RuyiSDK 0.52 已于 2026 年 9 月 1 日发布，对应的包管理器版本也为 0.52.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 为未来的“RuyiSDK 认证”做了包管理器方面的预留。
* 修复了实验性的 `ruyi entity list` 命令只接受多个 `-t` 参数中的第一个的问题。感谢 [weilinfox][weilinfox] [报告](https://github.com/ruyisdk/ruyi/issues/492)此问题，感谢 [Mr-Eric666][Mr-Eric666] 的[贡献](https://github.com/ruyisdk/ruyi/pull/493)！
* 工程化迭代：
  * 更新了依赖版本。
  * 使 `ruyi` 的代码写法兼容了 argcomplete 3.7.2 及更高的版本。
  * pygit2 上游已从 1.20.0 版本开始提供 RISC-V 二进制，故移除了 pygit2 的本地构建逻辑，降低维护成本。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 修复了“最新包管理器版本”API 返回的 macOS 二进制条目的“操作系统/架构”键名不对的问题。感谢 [weilinfox][weilinfox] [报告](https://github.com/ruyisdk/ruyi-backend/issues/113)此问题！

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

[Mr-Eric666]: https://github.com/Mr-Eric666
[weilinfox]: https://github.com/weilinfox

### RuyiSDK IDE

- feat: 新增复制包ID功能
- feat: 新增 l10n CI
- fix: 共用 toolchain 和 sysroot 组件
- fix: 修改 repo 后没有重新加载 package tree
- fix: package tree 的中文翻译错误
- docs: 完善 Sipeed Lichee Pi 4A 的相关文档。
- test: VSCodium 平台 RuyiSDK 插件适配，Java、JavaScript、Go、Python 语言相关插件测试。
- ci: 维护 CI 脚本，提高安全性。
- feat: 调整 IDE 侧边栏图标样式，提高辨识度。

### 版本测试及遗留问题

本版本测试增加了 macOS 14 平台测试，并给出相应的测试报告。

Ruyi 包管理器遗留缺陷：

| 缺陷      | 问题等级 |判定依据 |
| ----------- | ----------- | --- |
| [Occasional pygit2 failures during testing #415](https://github.com/ruyisdk/ruyi/issues/415) | 一般 | 已有 issue 回复 |
| [ruyi entity list 传入多个 -t 参数时只消费其中一个 #492](https://github.com/ruyisdk/ruyi/issues/492) | 一般 | 下一版本修复 |

RuyiSDK Eclipse IDE 遗留缺陷：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [命令执行提示框可以任意关闭且无法重新打开 #82](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/82)   | 建议 |   |
| [虚拟环境建立的项目绑定问题 #84](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/84) | 建议 |  |
| [安装插件时 Eclipse 提示未签名 #85](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/85) | 建议 |  |
| [New Virtual environment添加虚拟环境时响应时间过长 #177](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/177) | 建议 |  |
| [用户无法直观获知项目当前启用的虚拟环境 #191](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/191) | 建议 |  |
| [select package 不可用 #196](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/196) | 建议 |  |

RuyiSDK VSCode IDE 遗留缺陷：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [版本切换过程中中英文切换不灵活 #231](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/231)   | 建议 |   |

## 社区与内容建设


### packages-index 资源更新

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 软件源格式更新：
  * 支持为软件包附着供应商元数据：位于 manifest TOML 的 `metadata.vendor.data` 字段，其类型为 `供应商 ID: 键值对` 的字典（TOML 表格）；支持布尔型与字符串类型的值。
  * 预留 `metadata.vendor.data.ruyisdk.certified` 为表示“RuyiSDK 认证”状态的元数据字段。
* 更新软件包：
  * `board-image/armbian-spacemit-musepipro-minimal`: SpacemiT Muse Pi Pro 的 Armbian。感谢 [SmulllLu][SmulllLu] 的贡献！
  * `toolchain/gnu-ruyisdk`: RuyiSDK GNU 工具链，增加了实验性的 macOS AArch64 (Apple Silicon) 支持。
* 新增设备支持：
  * 知合 (Zhihe Computing) A210 SODIMM: 兼容其官方提供的 EVB 系统镜像。感谢 [weilinfox][weilinfox] 的贡献！

您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

[SmulllLu]: https://github.com/SmulllLu

### 开发板支持矩阵

- 新增 VisionFive 2 Lite 的 Ubuntu 24.04 和 Debian 工程版中英文测试报告。[PR #390](https://github.com/ruyisdk/support-matrix/pull/390)、[PR #391](https://github.com/ruyisdk/support-matrix/pull/391)
- 更新 K510 的 Buildroot 中英文测试报告。[PR #392](https://github.com/ruyisdk/support-matrix/pull/392)

### 开发板示例仓库

- 新增 SpacemiT K3 Pico-ITX 板卡文档，并补充 CoreMark、HelloWorld 和 llama-server 示例。[PR #33](https://github.com/ruyisdk/board-docs/pull/33)
- 新增 BPI-CANMV-K230D-Zero 中英文板卡说明，并补充中文 CanMV Linux SDK 安装指南，涵盖 RV64ILP32、RV64LP64 镜像烧录流程。[PR #41](https://github.com/ruyisdk/board-docs/pull/41)、[PR #42](https://github.com/ruyisdk/board-docs/pull/42)
- 为 15 款开发板补充或完善英文 HelloWorld 入门文档。[PR #36](https://github.com/ruyisdk/board-docs/pull/36)、[PR #37](https://github.com/ruyisdk/board-docs/pull/37)
- 完善仓库维护机制：自动生成中英文开发板索引并通过 CI 校验，补充命名、版本与双语文档规范，统一 Ruyi 安装版本引用并建立定期更新机制，同时新增双语覆盖报告。[PR #34](https://github.com/ruyisdk/board-docs/pull/34)、[PR #35](https://github.com/ruyisdk/board-docs/pull/35)、[PR #38](https://github.com/ruyisdk/board-docs/pull/38)、[PR #39](https://github.com/ruyisdk/board-docs/pull/39)、[PR #40](https://github.com/ruyisdk/board-docs/pull/40)

### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 hypot、hypotf、expm1f、lgamma 和 lgammaf 至现有的 glibc libmvec 框架。
  - 基于 C908 针对 strstr 接口进行了初步调优。
- newlib:
  - 移植了 acospi、asinpi、atan2、atanpi 至现有的 newlib 向量数学框架。

### GCC
持续推进p扩展GCC intrinsic支持，目前总体进度如下：

RV32 API tester: 901 PASS / 64 FAIL / 20 SKIP
RV64 API tester: 928 PASS / 57 FAIL

https://github.com/ruyisdk/riscv-gcc/commits/p-rebase

协助RISE基金会完善了CI维护工作：
https://github.com/riseproject-dev/gcc-precommit-ci/pull/1
https://github.com/riseproject-dev/gcc-postcommit-ci/pull/4
https://github.com/riseproject-dev/riscv-gnu-toolchain-ci/pull/1

### LLVM

本期提交 PR 如下

- [ValueTracking][InstCombine] Preserve samesign when flipping icmp strictness
  https://github.com/llvm/llvm-project/pull/209097
  在将非严格整数比较规范化为严格比较时保留 `samesign` 标志，同时避免常量调整跨越溢出或符号边界。已合并
- [InstCombine] Use samesign constraints in unsigned known-bits folds
  https://github.com/llvm/llvm-project/pull/209675
  在无符号比较的 known-bits 折叠中传播 `samesign` 的符号位约束，从而支持更多整数范围端点折叠。已合并
- [RISCV][P-ext] Add packed multiply-parts intrinsics
  https://github.com/llvm/llvm-project/pull/218875
  新增 P 扩展乘法分部操作的 LLVM intrinsic、SelectionDAG、Clang 接口及 RV32/RV64 代码生成测试。已合并
- [RISCV][P-ext][NFC] Overload scalar mqacc/mqracc intrinsics by element width
  https://github.com/llvm/llvm-project/pull/219345
  按元素宽度重载并合并标量 mqacc/mqracc intrinsic，减少重复定义，不改变生成代码。已合并
- [RISCV][P-ext] Support Packed "Q-format" Multiply Parts Accumulate
  https://github.com/llvm/llvm-project/pull/217918
  实现 P 扩展 Q-format 乘法分部累加，覆盖 Clang、LLVM IR、指令选择及 RV32/RV64 测试。已合并
- [RISCV] Support Packed Multiply High Accumulate
  https://github.com/llvm/llvm-project/pull/217591
  新增 packed multiply-high accumulate intrinsic 及对应代码生成，并补充 Clang 接口和双目标测试。已合并
- [Clang][RISCV] Add packed saturating and rounding shift intrinsics
  https://github.com/llvm/llvm-project/pull/217692
  为 pssha、psshar、psshl 和 psshlr 增加 Clang builtin、头文件封装及代码生成测试。已合并
- [RISCV][P-ext] Select immediate forms for packed saturating shifts
  https://github.com/llvm/llvm-project/pull/217688
  完善 packed saturating shift 常量操作数的立即数形式选择，并保留超出立即数字段范围时的寄存器形式。已合并
- [RISCV] Lower vector i1-to-fp i1 to VSELECT 1.0/0.0
  https://github.com/llvm/llvm-project/pull/219426
  在 RISC-V 指令选择阶段将向量 i1 到浮点类型的转换下降为选择 1.0/0.0 的 VSELECT。已合并
- [Clang][RISCV] Add packed widening multiply intrinsics
  https://github.com/llvm/llvm-project/pull/217534
  添加 packed widening multiply intrinsics 支持。已合并
- [Clang][RISCV] Add packed widening add/sub intrinsics
  https://github.com/llvm/llvm-project/pull/219348
  添加 packed widening add/sub intrinsics 支持。已合并
- [RISCV] Support Packed Multiplication with Horizontal Addition
  https://github.com/llvm/llvm-project/pull/218430
  实现 packed multiplication with horizontal addition 的 Clang、LLVM intrinsic、后端选择及 RV32/RV64 测试。正在 review

### V8

本期亮点：V8 RISC-V后端增加了Zcb扩展的汇编、反汇编、内置模拟器和代码生成支持。目前V8已经完整支持Zca，Zcb，Zcd，Zcf，开启压缩指令集扩展后，AOT内置库的静态代码尺寸从2.70MB减小到2.43MB，减小幅度达10%。

本期提交并合入的patch：
1. **[riscv] Replace JAL with AUIPC/JALR in lazy compile jump slots**
[RISC‑V] 将惰性编译跳转槽的 JAL 指令替换为 AUIPC/JALR 指令组合（https://chromium‑review.googlesource.com/c/8301500）

2. **[riscv] Add ZCB extension and unify RVC register checks**
[RISC‑V] 添加 ZCB 压缩扩展支持，并统一 RVC 压缩指令的寄存器校验逻辑（https://chromium‑review.googlesource.com/c/8271868）

3. **[riscv][sandbox] Harden TailCalls after code update**
[RISC‑V][沙箱] 加固代码更新完成后的尾调用安全处理逻辑（https://chromium‑review.googlesource.com/c/8311072）

4. **[riscv] Fix OSR code check in OnStackReplacement**
[RISC‑V] 修复栈上替换（OSR）流程里的代码校验逻辑（https://chromium‑review.googlesource.com/c/8311188）

5. **[riscv] Harden jump offset range checks in the assembler and deoptimizer**
[RISC‑V] 强化汇编器与反优化器中跳转偏移量的范围检查（https://chromium‑review.googlesource.com/c/8305697）

6. **[riscv] Remove unused ER creation in builtins‑riscv**
[RISC‑V] 删除 riscv 内置函数中未被使用的 ER 对象创建代码（https://chromium‑review.googlesource.com/c/8284941）

7. **[riscv][maglev] Zero‑extend Int32 index in element address**
[RISC‑V][Maglev] 在数组元素地址计算时对 Int32 索引做零扩展（https://chromium‑review.googlesource.com/c/8221145）

8. **[riscv] Implement Zcb extension in RISC‑V simulator**
[RISC‑V] 在 RISC‑V 模拟器中实现 Zcb 压缩扩展指令集（https://chromium‑review.googlesource.com/c/8268575）

9. **[riscv] Add Zcb compressed extension support**
[RISC‑V] 新增 Zcb 压缩扩展指令集后端支持（https://chromium‑review.googlesource.com/c/8263250）

本期审核并合入的patch：
1. **[riscv] Fix typo of RoundingMode in simulator**
[RISC‑V] 修复模拟器中 RoundingMode 拼写错误（https://chromium‑review.googlesource.com/c/8251431）

2. **[riscv] Fix emulator sNaN check**
[RISC‑V] 修复模拟器信号 NaN（sNaN）检测逻辑（https://chromium‑review.googlesource.com/c/8253666）

3. **[riscv] Fix some issues**
[RISC‑V] 修复若干代码问题（https://chromium‑review.googlesource.com/c/8253281）

4. **[riscv] Make Smi int32 checks safe with pointer compression**
[RISC‑V] 保证指针压缩模式下 Smi int32 校验逻辑安全可靠（https://chromium‑review.googlesource.com/c/8236678）

5. **[riscv] Avoid clobbering live input registers**
[RISC‑V] 避免生成代码时覆盖仍处于活跃状态的输入寄存器（https://chromium‑review.googlesource.com/c/8263861）

6. **[riscv] Fix integer masking and pointer branch comparisons**
[RISC‑V] 修复整数掩码运算以及指针分支比较逻辑缺陷（https://chromium‑review.googlesource.com/c/8265241）

7. **[riscv] Store Liftoff constants using their value width**
[RISC‑V] Liftoff 按照常量实际位宽执行常量存储操作（https://chromium‑review.googlesource.com/c/8267767）

8. **[riscv] Fix atomic stores of tagged and compressed values**
[RISC‑V] 修复标记指针、压缩值的原子存储实现（https://chromium‑review.googlesource.com/c/8267768）

### OpenJDK

本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/32123 (8388192: [lworld] Some code is not guarded by Arguments::is_valhalla_enabled())  为各CPU平台添加必要的value type特性开关判断

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/31576 (8386292: Shenandoah: Simplify and strengthen C1 barriers)  为各CPU平台清理ShenandoahGC C1 barrier汇编器实现
- https://github.com/openjdk/jdk/pull/31627 (8387078: RISC-V: x27 can be allocated in CompressedOops mode)  CompressedOops场景下将RISC-V x27设置为可分配寄存器
- https://github.com/openjdk/jdk/pull/28894 (8374184: RISC-V: implement GCM intrinsic with Zvkg and Zvkned extension)  为RISC-V平台实现GCM加密解密intrinsic实现
- https://github.com/openjdk/jdk/pull/31717 (8387381: RISC-V: assert failed with fastdebug build on systems with different core types)  为RISC-V平台修复异构芯片场景断言错误
- https://github.com/openjdk/jdk/pull/30816 (8379706: Cleanup and clarify BarrierSetAssembler::try_resolve_weak_handle_in_c2)  为各CPU平台清理barrier汇编器实现
- https://github.com/openjdk/jdk/pull/31793 (8387789: RISC-V: Optimize G1 post-write barrier conditional card mark)  为RISC-V平台优化G1GC barrier实现
- https://github.com/openjdk/jdk/pull/31779 (8387747: Enable long vector multiply IR tests for RISC-V)  为RISC-V平台打开矢量乘法IR测试
- https://github.com/openjdk/jdk/pull/31806 (8387857: RISC-V: Add UseZvbb to RVA23U64Profile)  为RISC-V平台补齐RVA23扩展集合
- https://github.com/openjdk/jdk/pull/27409 (8368180: RISC-V: Remove redundant ext_Zicboz.enable_feature())  为RISC-V平台删除冗余的Zicboz扩展使能

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）RISC-V移植工作进展：
RISC-V平台JEP 401兼容性相关工作已随Value Class PR合并到JDK主线仓，通过兼容性测试，且支持值类型Flattening优化（UseArrayFlattening & UseFieldFlattening）。
下一步工作：继续调研方法调用场景下Value Class值类型参数传递内联优化在X86和ARM64上的实现细节（InlineTypePassFieldsAsArgs & InlineTypeReturnedAsFields）。
Value Class PR详细修改如下：
- https://github.com/openjdk/jdk/pull/31120 (8389219: Implement JEP 401: Value Objects (Preview))

### Go

提交主线代码

- 752981: crypto/sha256: enable zvknha for riscv64 | https://go-review.googlesource.com/c/go/+/752981 基于 vlenb 侦测要求重新编写
- https://github.com/emmansun/gmsm/pull/586 提交sm3/sm4 支持

review主线代码

- 824984: cmd/compile: fix large riscv64 move/zero | https://go-review.googlesource.com/c/go/+/824984 修复SSA无法移动大范围数据
- 748921: cmd/compile: use SLLW for Lsh32x(64|32|16|8) on riscv64 | https://go-review.googlesource.com/c/go/+/748921 算术左移启用sllw指令
- 735520: riscv64: add disassembly support and tests for zacas | https://go-review.googlesource.com/c/arch/+/735520 arch库添加zacas 指令测试
- 801682: internal/cpu: restrict RISC-V GODEBUG options to optional extensions | https://go-review.googlesource.com/c/go/+/801682 严格设定godebug profile 等级

### QEMU

## 社区动态
- [【内测开启】Ruyi Imager — RISC‑V 开发板图形化镜像刷写工具，欢迎大家体验测试！](https://ruyisdk.cn/t/topic/2803)：Ruyi Imager图形化镜像烧录工具开启内测，支持多平台与多款RISC‑V开发板，无需ruyi命令行即可完成镜像烧录，欢迎社区测试反馈。

---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
