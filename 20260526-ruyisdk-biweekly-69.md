# RuyiSDK 双周进展汇报 第 069 期·2026 年 05 月 26 日

## 卷首语
各位 RuyiSDK 的开发者伙伴，大家好！

RuyiSDK 双周进展已更新到第 69 期。本期我们随 0.49 版本一起，继续夯实全栈开发环境与基础软件栈：包管理器新增机读模式与质检命令，并优化虚拟环境与 sysroot 使用体验；VSCode 与 Eclipse 插件围绕国际化、虚拟环境与交互体验持续打磨；
于此同时，基础 C 库、GCC、LLVM、V8、OpenJDK、Go、QEMU 等组件则围绕 RISC‑V 向量扩展、P 扩展、RVA23 等方向持续向上游贡献补丁，扩展指令集与 CPU 型号支持，提升运行时与编译器生态的完整性和稳定性。

更多进展细节详见下方各板块，欢迎试用并在 GitHub 或社区中反馈建议，期待更多伙伴一起共建 RISC‑V 软件开发生态。


⏬ 每个组件都提供了多种下载或安装方式，您可以任意选择一种：

* RuyiSDK 包管理器 0.49.0🚀
    * 从 [PyPI](https://pypi.org/project/ruyi/0.49.0/) 安装：`pip install ruyi`
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.49.0)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.49.0/)
    * [使用文档](https://ruyisdk.org/docs/Package-Manager/)

    > [!NOTE]
    > RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
    > 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
    > 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
    >
    > 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。对于 `ruyi` 的单文件二进制发行版，您必须将下载的文件重命名为一字不差的 `ruyi` 才能正常使用。
    >
    > 请注意：从 RuyiSDK 0.48.0 开始，Ubuntu 22.04 LTS 与 Python 3.10 环境不再受到支持。相关用户，尤其是发行版打包者、CI 环境维护者与仍在使用旧版 Python 运行环境的用户，在升级前请提前确认兼容性影响并完成验证。

* RuyiSDK VSCode Extension 0.1.3
    * VSCode/VSCodium Extensions 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装 (Install from VSIX):
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-vscode-extension/releases/tag/0.1.3/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/vscode/)
    * [使用文档](https://ruyisdk.org/docs/VSCode-Plugins/)

* RuyiSDK Eclipse Plugins 0.1.3
    * Eclipse Marketplace 中搜索 `RuyiSDK`关键字查询 安装 RuyiSDK 插件
    * 手动下载安装：
        * [GitHub Releases](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/releases/tag/v0.1.3/)
        * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ide/plugins/eclipse/)
    * [使用文档](https://ruyisdk.org/docs/IDE/)

如果您不清楚怎么选择，可以参考不同渠道和下载方式的说明：https://ruyisdk.cn/t/topic/2479 

每一次版本的迭代，都离不开社区伙伴的反馈与贡献。下个版本计划于 6 月底发布，我们将持续给您带来更新！我们诚挚邀请您常来 [RuyiSDK 技术社区](https://ruyisdk.cn/) 交流想法，共同成长。

## 基础开发环境

### 包管理器

RuyiSDK 0.49 将于 2026 年 5 月 26 日发布，对应的包管理器版本也为 0.49.0。本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 为 `ruyi repo list` 支持了机读模式（porcelain mode）。感谢 [@sisungo] 的贡献！
* 新增了 `ruyi admin check` 命令，用于 RuyiSDK 第一方与第三方软件源维护者对软件源的质检。
* 修复了 `ruyi extract` 向当前工作目录解压后报告解压到了 `None` 的小问题。
* 修复了几处 `ruyi` 的首次运行提示、遥测、命令行自动补全三者之间的不良相互作用。
* 不再将 `ruyi version` 调用视为 `ruyi` 的首次运行了，有助于避免特定场景下非预期的输出。
* 为 `ruyi venv` 新增了 `--project-sysroot-from-rootfs` 选项，用来从一个发行版 chroot/rootfs 目录直接将交叉编译所需的必要部分“投射”到新创建的虚拟环境，以避免复制整个目录从而遇到涉及 `/etc`、`/root` 等文件（或文件夹）的权限问题。
* 工程化迭代：
    * 更新了依赖版本。

[@sisungo]: https://github.com/sisungo

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 更新了以下软件到最新版本：
    * `emulator/qemu-system-riscv-upstream`: 更新到了 11.0.0-ruyi.20260421 版本，支持 RVA23。
    * `emulator/qemu-user-riscv-upstream`: 更新到了 11.0.0-ruyi.20260421 版本，支持 RVA23。

本次 RuyiSDK 服务端组件的更新主要包含了以下内容：

* 例行安全更新与依赖更新。
* 修复了数据库连接的稳定性。
* 修复了 Elasticsearch 请求超时不会重试的问题。
* 修复了依赖版本更新导致无法正常解析客户端遥测数据的问题。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。


### RuyiSDK VSCode 插件

- 新增 i18n
- 新增中文翻译
- 为虚拟环境的 sysroot 添加额外包选择框
- 重新设计新闻页面，添加中英文翻译与动画
- 修复一键编译识别 CMake 错误
- 在 ruyisdk home 页面添加 board 文档入口

### RuyiSDK Eclipse 插件

- 包管理器模块：修复设备列表的排序。
- ruyi: 添加必要的环境变量。
- 虚拟环境：支持在“项目”视图中右键项目新建或应用虚拟环境。
- 虚拟环境：在创建时让用户选择已打开的项目而不是输入路径，减少迷惑。
- 虚拟环境：在列表中显示项目名称和虚拟环境的相对路径。
- 项目：发布 v0.1.4。

### 版本测试及遗留问题

RuyiSDK 0.49.0 测试报告尚未发布，只更新部分测试情况。

#### 测试套件

本次测试切换到新编写的基于 pytest 的测试套件，更适合 ruyi 项目 CI 集成。

+ 测试套件 <https://github.com/ruyisdk-test/ruyi-pytest>
+ 测试工程 <https://github.com/ruyisdk-test/ruyi-pytest-ci>
+ 测试报告模板 <https://github.com/ruyisdk-test/ruyi-pytest-reports>

#### Ruyi 测试

上一版本新增缺陷在本版本均修复。

#### RuyiSDK Eclipse IDE 测试

暂无测试情况更新。

#### RuyiSDK VSCode IDE 测试

暂无测试情况更新。


## 基础组件

### 基础C库
- GLIBC:
   - 移植了 cbrtf、cosf、coshf 接口到现有的 glibc libmvec 框架，在测试范围内最大误差相对于 mpfr 均小于等于 1 ULP。
- newlib:
   - 提交了 memccpy、memchr、memcmp、mempcpy、memrchr、rawmemchr 接口的 RVV 优化实现到上游（https://sourceware.org/pipermail/newlib/2026/022437.html）。
   - 实现了 strcasecmp、strncasecmp、strcspn、strncmp、strspn 接口的 RVV 优化。
- MUSL:
   - 实现了 strcasecmp、strncasecmp、strcspn、strncmp、strspn 接口的 RVV 优化。

### GCC
- 更新GCC版本至gcc16.1, 同步了回归测试中发现的错误，更新了白名单。
- 更新了P扩展binutils支持，继续更新intrinsic支持中。

### LLVM

- [RISCV] Add support for Ziccid 1.0
https://github.com/llvm/llvm-project/pull/196459 
为 RISC-V 的 Ziccid 1.0 拓展添加支持
已经合并

- [RISCV][MC][NFC] Update IME vtype layout to match latest spec riscv-isa-release-fa55752-2026-05-04
https://github.com/llvm/llvm-project/pull/195998
更新 RISC-V 的 IME vtype 布局以匹配最新的规范
已经合并

- [RISCV][NFC] Rename Zvvmm instruction file to Zvvm
https://github.com/llvm/llvm-project/pull/196692
重命名 RISC-V 的 Zvvmm 指令文件为 Zvvm，以匹配最新的规范
已经合并

- [RISCV][MC] add experimental Zvvfmm MC support
https://github.com/llvm/llvm-project/pull/196486
为 RISC-V 的 Zvvfmm 拓展增加初步的 MC 汇编支持
已经合并

- [RISCV][MC] Add experimental Zvvmtls and Zvvmttls support
https://github.com/llvm/llvm-project/pull/198229
为 RISC-V 的 Zvvfmm、Zvvmtls 和 Zvvmttls 拓展增加初步的 MC 汇编支持
正在 review

- [RISCV][P-ext] Set BITCAST to Custom for 64-bit packed vectors on RV32 /
[RISCV][P-ext] Custom-lower SELECT for v4i16/v8i8 on RV32
https://github.com/llvm/llvm-project/pull/198267
https://github.com/llvm/llvm-project/pull/198723
将 64-bit 的 packed 向量在 RV32 上的 bitcast 设置为 custom 下降，可以解决在 RV32 上一些指令选择不到 p*.d* 这种寄存器对指令的问题。

- Add missing vxsat to PSADDU.B, PSSUB.B/W, and PSSUBU.W. /
Fix PSSHLR.WS left-shift saturation pseudocode. /
Use Sail's <_s/>_s/>_u (with underscore) in pseudocode.
https://github.com/riscv/riscv-p-spec/pull/282
https://github.com/riscv/riscv-p-spec/pull/283
https://github.com/riscv/riscv-p-spec/pull/284
在 RV-32 上 custom 下降 v4i16/v8i8 的 select, 减少指令数


### V8
本期提交并合入的patch：
1. **[riscv][headers] roots-inl.h should not include objects-inl.h**
   [RISC-V][头文件] 修复 roots-inl.h 不应包含 objects-inl.h 的问题（https://chromium-review.googlesource.com/c/7819506）
2. **[riscv][turboshaft][wasm] Decouple SIMD from WebAssembly**
   [RISC-V][Turboshaft][WASM] 将 SIMD 模块与 WebAssembly 解耦（https://chromium-review.googlesource.com/c/7819100）
3. **[riscv][wasm-wide-arith] implement sub128 for Turboshaft**
   [RISC-V][WASM宽算术] 在 Turboshaft 中实现 sub128 指令（https://chromium-review.googlesource.com/c/7830322）
4. **[riscv] Enable zba/zbb/zbs/zicond when enable rva23u64**
   [RISC-V] 启用 rva23u64 时自动开启 zba/zbb/zbs/zicond 扩展（https://chromium-review.googlesource.com/c/7831421）
5. **[riscv] Delete zero_extend after fcvtmod_w_d in TruncateDoubleToInt32**
   [RISC-V] 在 TruncateDoubleToInt32 中移除 fcvtmod_w_d 后的冗余零扩展操作（https://chromium-review.googlesource.com/c/7839765）
6. **[riscv][debugger] Fix a crash when debugging**
   [RISC-V][调试器] 修复调试过程中出现的崩溃问题（https://chromium-review.googlesource.com/c/7846282）
7. **[riscv][wasm-wide-arith] Implement Add128/Sub128 for riscv64**
   [RISC-V][WASM宽算术] 为 riscv64 实现 Add128/Sub128 指令（https://chromium-review.googlesource.com/c/7847572）
8. **[riscv] Detect RVC in cpu-riscv and rename SIMD flag to RVV**
   [RISC-V] 在 cpu-riscv 中增加 RVC 检测，并将 SIMD 标识重命名为 RVV（https://chromium-review.googlesource.com/c/7834018）
9. **[riscv] Fix AtomicCompareExchange write barrier**
   [RISC-V] 修复 AtomicCompareExchange 写屏障问题（https://chromium-review.googlesource.com/c/7858601）
10. **[riscv]Wide multiplication implementation in liftoff**
    [RISC-V] 在 Liftoff 中实现宽乘法指令（https://chromium-review.googlesource.com/c/7862260）
11. **[riscv][wasm][fuzzer] Optimize CheckMaxSteps with platform-specific code**
    [RISC-V][WASM][模糊测试] 使用平台专属代码优化 CheckMaxSteps（https://chromium-review.googlesource.com/c/7862178）
12. **[riscv]Lower LoadTrustedPointer in the code generators**
    [RISC-V] 在代码生成器中实现 LoadTrustedPointer 指令下沉（https://chromium-review.googlesource.com/c/7866844）
13. **[riscv] Fix condition inversion in kArchLoadTrustedPointer**
    [RISC-V] 修复 kArchLoadTrustedPointer 中的条件反转错误（https://chromium-review.googlesource.com/c/7870367）

### OpenJDK
本期提交的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30705 (8382087: aarch64: remove unused function declarations in macroAssembler_aarch64.hpp)  为ARM64移除未使用的函数声明

本期回合的JDK21u仓库patch:
- https://github.com/openjdk/jdk21u-dev/pull/2691 (8379464: Enable missing stack walking test via jtreg requires for RISC-V)  为RISC-V使能一项栈回溯测试用例
- https://github.com/openjdk/jdk21u-dev/pull/2692 (8378810: Enable missing FFM test via jtreg requires for RISC-V)  为RISC-V使能一项外部函数和内存接口FFM测试用例

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30309 (8380416: Enable CmpUNodeValueTests.java IR tests for RISC-V)   为RISC-V使能一项无符号比较白盒测试用例
- https://github.com/openjdk/jdk/pull/30258 (8379792: UBSAN runtime error: signed integer overflow during compress expand value transform)  为RISC-V和ARM64修复一类有符号整数溢出风险
- https://github.com/openjdk/jdk/pull/28366 (8363996: Obsolete UseCompressedClassPointers)  为各CPU平台4移除UseCompressedClassPointers特性支持
- https://github.com/openjdk/jdk/pull/30364 (8380580: Enable TestCombineAddPWithConstantOffsets.java IR tests for RISC-V)  为RISC-V使能一项访问地址加法优化白盒测试用例
- https://github.com/openjdk/jdk/pull/30107 (8378985: serviceability/sa/TestJhsdbJstackMixedWithXComp.java failed if sender frame is return barrier of Continuation)  为各CPU平台修复协程场景栈回溯问题
- https://github.com/openjdk/jdk/pull/30397 (8380789: RISC-V: TestOpaqueConstantBoolNodes.java fails when running without RVV)  为RISC-V修复一项测试用例硬件匹配问题
- https://github.com/openjdk/jdk/pull/30488 (8381250: Enable VectorLogicalOpIdentityTest.java IR tests for RISC-V)  为RISC-V使能一项矢量逻辑运算优化白盒测试用例
- https://github.com/openjdk/jdk/pull/30545 (8381554: RISC-V: Small refactoring for cmp_klass_compressed macro-assembler routine)  为RISC-V重构压缩对象类指针比较汇编函数逻辑

### Go
本期提交的Go主线CL:
- 782760: crypto/internal/poly1305: implement function update in assembly on riscv64 | https://go-review.googlesource.com/c/crypto/+/782760

本期合并的Go主线CL：
- 663778: cmd/asm, cmd/internal/obj: add zvbb/zvbc for riscv64 | https://go-review.googlesource.com/c/go/+/663778 添加zvbb/zvbc汇编支持
- 762880: riscv64: add support for zvk instructions | https://go-review.googlesource.com/c/arch/+/762880 objdump添加zvk* 指令支持

本期审阅并合入的CL：
- 770200: cmd/compile: simplify closure name | https://go-review.googlesource.com/c/go/+/770200 修复plugin 链接bug
- 758020: cmd/compile, runtime: use fine-grained FENCE instructions on riscv64 | https://go-review.googlesource.com/c/go/+/758020 FENCE指令细化
- 760900: cmd/compile/internal/ssa: prefer registers x8-x15/f8-f15 on riscv64 | https://go-review.googlesource.com/c/go/+/760900 C扩展前置CL，优先C psABI寄存器

### 模拟器QEMU

RuyiSDK QEMU新建开发分支develop（目前基于QEMU v11.0.0），未来开发工作将在该分支上进行。
- https://github.com/ruyisdk/qemu/tree/develop

本期添加了多款CPU Model的支持，包括THead C908/910/920，Spacemit X60，Sifive U74:
- https://github.com/ruyisdk/qemu/commit/98864cb044304c8f79dd435cdd6142a8d350353c
- https://github.com/ruyisdk/qemu/commit/3bca67d3a19a19297c60872d572ceea903115f74
- https://github.com/ruyisdk/qemu/commit/815ff8ad3728c46e538570e4de24126df52fc4e7
- https://github.com/ruyisdk/qemu/commit/3216cf397cc9d43216b8ec5e67dbbd958c30917c
