# RuyiSDK 双周进展汇报 第 081 期 · 2026 年 11 月 19 日

## 卷首语

>

## 基础开发环境


### 包管理器

由于 RuyiSDK 发版周期调整，RuyiSDK 包管理器的 0.55.0 版本预期将在 11 月底正式发布。欢迎下载 RuyiSDK 包管理器当前最新版本 0.54.0 试用。

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

目前有以下内容正在开发中：

* 对格式错误的软件源（如有些插件或软件包正在调试中等情况下）更加宽容，不要崩溃。
* 根据 XDG 基础目录规范，正确无视了使用相对路径的相应配置。
* 在 `ruyi repo get` 中暴露 `repo.disabled` 配置项。
* 更新了下载失败的排查指南文案，加入了服务器问题与终端网络环境等因素。
* 工程化迭代：
  * 更新了依赖版本。
  * 现已官方支持 Python 3.15 运行环境。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

### RuyiSDK IDE

- 去除新闻页面无用的按钮
- 更新 l10n tools 文档
- 完善插件的构建脚本及其对应的测试
- 使用发布到 OpenVSX 上的插件，解决第三方插件的依赖问题
- 打包三个 Linux 平台的 ruyi 程序以便用户快速开始体验 RuyiSDK

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增软件包：
  * `emulator/qemu-{system,user}-riscv-ame`: 基于上游 QEMU 11.1.0，加入了 AME 扩展的最新草案版本 v0.6 的支持。此扩展支持由达摩院贡献。
  * `emulator/qemu-{system,user}-riscv-rvp`: 基于上游 QEMU 11.1.0，加入了 RVP 扩展的最新草案版本 v0.6 的支持。
* 更新软件包：
  * `board-image/armbian-starfive-visionfive2-minimal`: 更新到了 26.11.0-trunk.120。
  * `board-image/armbian-orangepi-rv2-minimal`: 更新到了 26.11.0-trunk.120。
  * `board-image/buildroot-sdk-sipeed-licheervnano`: 更新到了 0.20261109.0。
  * `board-image/freebsd-riscv64-mini-live`: 更新到了 14.5。
  * `board-image/openbsd-riscv64-live`: 更新到了 8.0。
  * `board-image/canmv-*-k230`: 修复了下载链接。
  * `board-image/openbsd-riscv64-live`: 移除了上游不再支持或提供的版本 7.6.0。
  * `board-images/openwrt-sifive-unmatched`: 更新到了 25.12.6。

您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

### 开发板支持矩阵

- 更新 Sipeed Lichee Pi 4A 的 RevyOS 20260504 中英文测试报告。[PR #413](https://github.com/ruyisdk/support-matrix/pull/413)
- 修复 CI 中构建依赖的安装问题。[PR #414](https://github.com/ruyisdk/support-matrix/pull/414)

### 开发板示例仓库

- 新增 Milk-V Jupiter2 的 ONNX Runtime 中文部署与推理示例。[PR #57](https://github.com/ruyisdk/board-docs/pull/57)
- 新增 SpacemiT V100-C2201 中英文板卡文档及 HelloWorld、CoreMark 示例。[PR #58](https://github.com/ruyisdk/board-docs/pull/58)
- 开发板文档前端开放 SpacemiT K3 CoM260 Kit 的 ROS 2 第 16 至 19 章课程入口，并改为按课程目录确定展示范围。[PR #17](https://github.com/DuoQilai/board-docs-frontend/pull/17)、[PR #19](https://github.com/DuoQilai/board-docs-frontend/pull/19)

### 官网&文档

- 文档：更新了 ruyi 包管理器的介绍和使用说明文档 [PR #154](https://github.com/ruyisdk/docs/pull/154)

## 基础组件


### 基础C库

- GLIBC:
  - 移植了 tanh, tanhf, tanpi, tanpif 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 hypotf, lgammaf, log10f, log1pf, powf, sincosf, sincospif, sinf, sinhf, sinpif, sqrtf, tanf, tanhf, tanpif 至现有的 newlib 向量数学框架。

### GCC
本期交付了可在 RV32 和 RV64 上直接运行的 **3 个 P 扩展示例**，覆盖图像匹配、定点点积和数字滤波。 **13 个提交进入 GCC 主线**，其中 8 个改进位操作和旋转，4 个支持向量点积，1 个修复通用循环优化。在 K1 实机上，32 位掩码的标量置位、清位和翻转位微基准均节省约 **27% 的执行周期**。

#### P 扩展｜用图像与信号演示一条指令处理多个数据

把原有 RV64 图像示例移植到 RV32 后，两种平台现在可以搜索同一个 16×16 图块。RV32 每条打包指令比较 4 个像素，RV64 比较 8 个。程序遍历 289 个候选位置，准确找回了向右 5 像素、向上 3 像素的位移。新增的 Q15 定点示例用 64 位累加器计算两串 16 位采样的点积，也能用一组滤波系数平滑输入波形。

![左图为图像块在原图与移位图中的匹配位置，右图为 Q15 滤波器的输入与输出波形。](https://raw.githubusercontent.com/pz9115/wechat-articles/c7dc81acf835238a858f40c54eb5213f6db248be/images/biweekly-81/p-examples.png)

同一份工作交给 P 扩展后，三个示例执行的指令数都明显下降。以 RV64 上的图像匹配为例，比较一个图块从 2,189 条指令减到 438 条。下表为 QEMU 在 `-O3`、允许非对齐访存配置下记录的动态指令降幅。

| 单次调用的工作量 | RV32 | RV64 |
| --- | ---: | ---: |
| 图像匹配 · 比较一个 16×16 图块 | 75.7% | **80.0%** |
| Q15 点积 · 1,024 对采样 | 70.7% | 74.9% |
| Q15 滤波 · 32 抽头、64 个输出 | 69.5% | 73.2% |

示例仓库附有预编译工具链和两份交互式教程，可直接运行标量 C 和 P 扩展版本，对照图像、波形和生成的指令。[示例仓库](https://github.com/pz9115/RVP-Example/tree/cb77e9e686c7c61c5c9a0a20a83bba3ae8776f20) · [图像教程](https://github.com/pz9115/RVP-Example/blob/cb77e9e686c7c61c5c9a0a20a83bba3ae8776f20/RVP_Tutorial.ipynb) · [信号处理教程](https://github.com/pz9115/RVP-Example/blob/cb77e9e686c7c61c5c9a0a20a83bba3ae8776f20/DSP_Tutorial.ipynb)

#### B 扩展｜让 GCC 自动选出更短的位操作序列

过去 GCC 在设置一个比特时，会先生成掩码，再用一次“或”运算写回。本期优化让一条 `bset` 直接完成写回，RV64 函数主体从 3 条指令缩到 2 条。K1 上，使用 32 位掩码的标量置位、清位和翻转，执行周期都减少约 27%。图中最后一行是同样的翻转操作放进数组循环后的结果。编译器原本就能把常量准备移出循环，因此两版的执行周期基本持平。[GCC 主线提交](https://github.com/gcc-mirror/gcc/commit/fb66e0c3e24743e415c50eff069e61a935134e92)

![K1 实机上八个微基准的动态指令和执行周期降幅，标量字掩码翻转周期减少 27.14%，数组循环持平。](https://raw.githubusercontent.com/pz9115/wechat-articles/c7dc81acf835238a858f40c54eb5213f6db248be/images/biweekly-81/b-k1.png)

优化覆盖了取位后取反、单比特掩码、负计数或窄位宽计数的旋转、字节与字拼接，以及移位加法与后续运算的组合。移位加法接左旋或右旋时，K1 周期减少约 19.8%。接除法或取余时，动态指令减少 8.30%，周期持平。拼接两个 32 位字在 gem5 乱序模型上节省 32.77% 的周期。同一模型上的 SQLite 变长整数解码函数，周期增加 0.63%。

#### 其他进展

- **GCC 向量点积**的 Zvdota / Zvbdota 支持已进入主线。开发者可从 C/C++ 调用整数、BF16、FP8 点积及批量 FP32 点积。[上游提交系列](https://github.com/gcc-mirror/gcc/compare/fb66e0c3e24743e415c50eff069e61a935134e92...6b58ef48245e22dcb1edfa75137ff0b426c9299b)
- **GCC 通用优化与社区协作**方面，修复了循环依赖分析的缓存索引，编译器可复用已有结果，避免在嵌套循环里重复分析。[缓存修复](https://github.com/gcc-mirror/gcc/commit/19a2172b22961d74074fb602e9b82d44ef6e1fc7)
- **Binutils 扩展支持**方面，Shlcofideleg v2 已投稿。[Shlcofideleg 投稿](https://sourceware.org/pipermail/binutils/2026-November/152703.html)
- **RISE 持续集成**首次跑通 pre-commit 的手动试运行。Linux 位操作、Linux 向量和 Newlib 向量三种配置已能自动将补丁测试结果与生产基线对比。[试运行](https://github.com/riseproject-dev/gcc-precommit-ci/actions/runs/44233565953) · [对比结果](https://github.com/riseproject-dev/gcc-precommit-ci/issues/2)

### LLVM

本期提交 PR 如下

- [RISCV][P-ext] Restrict P widening shift legalization to left shifts
  https://github.com/llvm/llvm-project/pull/242773
  将 RV32 P 扩展中使用 `WSLL`/`WSLA` 的扩宽移位合法化限制为左移，修复右移被错误选择为左移指令的问题。已合并
- [RISCV][P-ext] Add scalar ssh1sadd intrinsic
  https://github.com/llvm/llvm-project/pull/239234
  新增标量饱和移位加法 intrinsic `__riscv_ssh1sadd_i32`，支持 RV32 的 `ssh1sadd` 及 RV64 的 `pssh1sadd.w` 指令选择。已合并
- [RISCV][P-ext] Add scalar comparison intrinsics
  https://github.com/llvm/llvm-project/pull/239245
  新增标量相等及有符号、无符号大小比较 intrinsics，支持 RV32 原生指令和 RV64 打包字指令，并通过交换操作数或按位取反实现其他比较形式。已合并
- [RISCV][P-ext] Add scalar saturating and rounding shift intrinsics
  https://github.com/llvm/llvm-project/pull/241730
  新增标量饱和及舍入移位 intrinsics，支持有符号移位量控制左右移、RV32/RV64 指令选择及常量移位量的立即数形式。已合并
- [RISCV][P-ext] Add scalar mhacc.h0/h1 intrinsics
  https://github.com/llvm/llvm-project/pull/242195
  新增选取低半字或高半字的标量乘法高位累加 intrinsics，支持有符号和混合符号形式，并实现 RV32/RV64 代码生成。已合并
- [RISCV][P-ext] Add Scalar Zip/UnZip Intrinsics
  https://github.com/llvm/llvm-project/pull/241430
  新增标量交错与解交错 intrinsics，并补全 `zip*hp` 的代码生成支持。已合并
- [RISCV][P-ext] Support Scalar Narrowing Clip
  https://github.com/llvm/llvm-project/pull/241979
  新增标量窄化裁剪 intrinsics，支持将 64 位值移位后饱和窄化为 32 位值，涵盖有符号、无符号及舍入变体，并补充窄化舍入算术右移支持。已合并
- [RISCV][P-ext] Add the missing zext_invec pattern
  https://github.com/llvm/llvm-project/pull/242288
  补全 `zext_invec` 从 `v8i8` 到 `v2i32` 的零扩展匹配，修复已标记为合法但缺少指令选择模式的问题。已合并
- [RISCV][P-ext] Fold packed shifts with zero
  https://github.com/llvm/llvm-project/pull/242432
  折叠多种移位量为零的打包移位操作，直接返回原操作数，消除冗余移位。已合并
- [RISCV][P-ext] Use EVT in `combinePExtWidening*Acc`
  https://github.com/llvm/llvm-project/pull/242687
  在扩宽累加合并中使用 `EVT` 处理值类型，修复假定简单值类型导致非标准位宽整数触发错误的问题。已合并
- [RISCV][P-ext] Replace some checks with pattern matching (NFC)
  https://github.com/llvm/llvm-project/pull/243022
  使用 SelectionDAG 模式匹配重写饱和运算合并及符号扩展检查，简化实现，保持功能不变。已合并
- [RISCV][P-ext] Fix assertion when legalizing i64 shift amounts on RV32
  https://github.com/llvm/llvm-project/pull/243366
  放宽 RV32+P 下移位量合法化的断言，允许通用合法化展开 64 位移位量，修复处理右移时的断言失败。已合并
- [RISCV][P-ext] Fix crash selecting WADDA[U]/WSUBA[U] with a zero accumulator
  https://github.com/llvm/llvm-project/pull/244093
  为扩宽加减累加指令使用 `buildGPRPair` 构造累加寄存器对，避免零累加值被选为 `X0_Pair` 后触发断言。已合并
- [RISCV][GlobalISel] Preserve KCFI type on indirect calls
  https://github.com/llvm/llvm-project/pull/240364
  在 GlobalISel 间接调用指令上保留 KCFI 类型信息，使 KCFI pass 能生成间接调用检查，与 SelectionDAG 的行为保持一致。已合并
- [RISCV][P-ext] Fold shifts with out-of-range signed shift amounts
  https://github.com/llvm/llvm-project/pull/243813
  根据 P 扩展有符号移位量的语义，折叠常量移位量超出元素位宽的移位操作，生成零值或等价的符号填充、最高位提取操作。正在 review

### V8
本期亮点：
本期审阅并合入了来自Andrew Gaul的若干性能优化patch，这些优化与修复工作均采用"人机协作"模式完成：由 riscvlint 等工具发现优化点，AI（Claude）辅助起草补丁与基准验证，全部改动均经 ISCAS 维护者人工评审、附量化性能数据与回归测试后合入主线，性能提升项如下：
1. 真实硬件SpaceTime K3提升说明和实测效果

| CL | 改动内容 | 性能提升 |
|---|---|---|
| [CL8698757](https://chromium-review.googlesource.com/c/8698757) | 蹦床池之后改发 4 字节短 `jal` 替代 8~12 字节 `auipc+jr` 长跳，新增 far-jump pool 机制保证目标可达 | 获得本期最大单项收益：K3 真机 JetStream 3 总分 +3.5%（75 项中 46 项超噪声，gaussian-blur +27%、wasm 类 +17~22%）；生成代码 -1.7MB（-2.2%），其中 Maglev -2.7%、TurboFan/regexp -3.8% |
| [CL8716968](https://chromium-review.googlesource.com/c/8716968) | TurboFan/Liftoff 构建可编码浮点常量时改用 Zfa 的 `fli` 指令 | 每个常量从 3 条指令（li+slli+fmv.d.x）变 1 条 `fli.d`，JetStream 3 生成代码消除 248 处 |
| [CL8697059](https://chromium-review.googlesource.com/c/8697059) | 空寄存器列表的 `PushAll`/`PopAll` 提前返回，跳过 `addi sp,sp,0` 空调整 | Maglev 代码移除约 9 万条无用指令（-361KB，约 -1%） |
| [CL8695943](https://chromium-review.googlesource.com/c/8695943) | Maglev Int32 比较直接比较寄存器，省去重复的 sext.w/zext.w 扩展复制 | Maglev 指令数 -0.47%（12 个 JetStream 3 基准、无指针压缩） |
| [CL8780855](https://chromium-review.googlesource.com/c/8780855) | Latin-1 正则前导的 `slli t1,a1,0` 伪 move 改为直接使用源寄存器 | 消除 2,704 条单周期指令（X100 可重命名消除 mv 但不能消除 slli） |
| [CL8701856](https://chromium-review.googlesource.com/c/8701856) | 调整溢出检查中 xor/and 的发射顺序，符合 SpaceTime X100 硬件宏融合要求 | 4,557 处依赖链从 2 cycle 降为 1 cycle（占总指令 0.01%，未单独跑分） |
| [CL8700095](https://chromium-review.googlesource.com/c/8700095) | Smi 0 经 `zero_reg` 直接存储（x64 优化移植），参数入栈不再物化零常量 | 消除零常量物化指令（未量化） |
| [CL8721932](https://chromium-review.googlesource.com/c/8721932) | 按 RVV v1.0 规范删除 SIMD 移位前冗余的移位量掩码计算 | 减少 SIMD 代码的指令发射（未量化） |

2. V8内置模拟器上获得的提升（可提升V8的开发和验证效率）

| CL | 改动内容 | 性能提升 |
|---|---|---|
| [CL8703878](https://chromium-review.googlesource.com/c/8703878) | `IsShortInstruction` 从 .cc 移入头文件内联（原占模拟器 23% 采样） | richards -34%（28.9s→19.0s）、ML -32%（40.2s→27.3s），本组单项最大 |
| [CL8765048](https://chromium-review.googlesource.com/c/8765048) | 缓存"任一调试功能是否启用"，免每条指令检查 stop_at/watch/断点/trace 等 6 项 | richards -27%（17.0s→12.4s）、ML -28%（24.9s→17.9s） |
| [CL8813064](https://chromium-review.googlesource.com/c/8813064) | 解码提速：字段读走 operand_ 快照、32 位指令类型查静态表、RVC getter 内联 | richards -20%（11.7s→9.3s）、ML -22%（17.1s→13.4s） |
| [CL8707133](https://chromium-review.googlesource.com/c/8707133) | `UNSUPPORTED()` 报告外提为函数，避免 -fstack-protector 给每个解码函数加栈保护 | richards -3%（18.6s→18.0s） |
| [CL8642931](https://chromium-review.googlesource.com/c/8642931) | 移除运行时改写 `v8_flags.trace_sim` | 减少热路径多余写入（未量化） |

3. 本期提交并合入的 patch 如下

（1）[riscv] Don't deduplicate heap number requests by their double bits
[RISC-V] 不要依据双精度比特对堆数值请求做去重 [CL8737461](https://chromium-review.googlesource.com/c/8737461)

（2）[riscv64] Fix 32-bit sign-extension for liftoff stack arguments
[RISC-V64] 修复 Liftoff 栈参数的 32 位符号扩展 [CL8736943](https://chromium-review.googlesource.com/c/8736943)

（3）[riscv][simulator] Model fence and AMO acquire/release ordering
[RISC-V][模拟器] 建模 fence 与 AMO 获取/释放内存序 [CL8739701](https://chromium-review.googlesource.com/c/8739701)

（4）[riscv] Store zero-valued constants through the zero register
[RISC-V] 通过零寄存器存储零值常量 [CL8700095](https://chromium-review.googlesource.com/c/8700095)

（5）[riscv64] Reject negative varargs length in StackOverflowCheck
[RISC-V64] 在栈溢出检查中拒绝负的可变参数长度 [CL8701857](https://chromium-review.googlesource.com/c/8701857)

（6）[riscv] Fix FP select when the zero constant is the left operand
[RISC-V] 修复零常量为左操作数时的浮点选择指令 [CL8795387](https://chromium-review.googlesource.com/c/8795387)

（7）[riscv][compiler] Check skipped write barrier for Smis
[RISC-V][编译器] 校验 Smi 跳过的写屏障 [CL8793548](https://chromium-review.googlesource.com/c/8793548)

（8）[riscv] Compute CAS address before sign-extending expected value
[RISC-V] 在对期望值做符号扩展前先计算 CAS 地址 [CL8752939](https://chromium-review.googlesource.com/c/8752939)

（9）[riscv][maglev] Fix StringCodePointAt at the end of a SlicedString
[RISC-V][Maglev] 修复 SlicedString 末尾处的 StringCodePointAt [CL8800253](https://chromium-review.googlesource.com/c/8800253)

（10）[riscv][compiler] Sign-extend switch input in AssembleArchTableSwitch
[RISC-V][编译器] 在 AssembleArchTableSwitch 中对 switch 输入做符号扩展 [CL8793344](https://chromium-review.googlesource.com/c/8793344)

（11）[riscv] Fix Mulh32 missing sign extension
[RISC-V] 修复 Mulh32 缺失符号扩展问题 [CL8813054](https://chromium-review.googlesource.com/c/8813054)

（12）[riscv][compiler] Avoid scratch register exhaustion in table switch
[RISC-V][编译器] 避免 table switch 耗尽临时寄存器 [CL8814796](https://chromium-review.googlesource.com/c/8814796)

（13）[riscv] Prevent far-jump pools from splitting RISC-V short branches
[RISC-V] 防止远跳转池打断 RISC-V 短分支 [CL8813180](https://chromium-review.googlesource.com/c/8813180)

4. 本期审阅并合入的 patch 如下

（1）[riscv][maglev] Test the sign of the or for a minus-zero product
[RISC-V][Maglev] 检测负零乘积或运算结果的符号 [CL8701837](https://chromium-review.googlesource.com/c/8701837)

（2）[riscv] Inline InstructionBase::IsShortInstruction
[RISC-V] 内联 InstructionBase::IsShortInstruction [CL8703878](https://chromium-review.googlesource.com/c/8703878)

（3）[riscv] Decode constant pool marker as unsigned
[RISC-V] 无符号解析常量池标记 [CL8493273](https://chromium-review.googlesource.com/c/8493273)

（4）[maglev] Compare Int32 values on riscv without re-extending them
[Maglev] 在 RISC-V 上比较 Int32 值，避免重复扩展 [CL8695943](https://chromium-review.googlesource.com/c/8695943)

（5）[riscv] Skip the stack adjustment for empty register lists
[RISC-V] 寄存器列表为空时跳过栈调整 [CL8697059](https://chromium-review.googlesource.com/c/8697059)

（6）[riscv] Link near long calls through ra
[RISC-V] 通过 ra 寄存器链接近长调用 [CL8680346](https://chromium-review.googlesource.com/c/8680346)

（7）[riscv] Order the overflow checks' xors so the and can fuse
[RISC-V] 调整溢出检查异或顺序，使与指令可融合 [CL8701856](https://chromium-review.googlesource.com/c/8701856)

（8）[riscv] Keep forward jumps short after the trampoline pool
[RISC-V] 跳板池之后保持向前跳转使用短跳转 [CL8698757](https://chromium-review.googlesource.com/c/8698757)

（9）[riscv] Report unsupported instructions out of line in the simulator
[RISC-V] 模拟器中离线上报不支持指令 [CL8707133](https://chromium-review.googlesource.com/c/8707133)

（10）[riscv] Remove redundant SIMD shift masking
[RISC-V] 删除冗余 SIMD 移位掩码操作 [CL8721932](https://chromium-review.googlesource.com/c/8721932)

（11）[riscv] Hoist atomic exchange address calculation
[RISC-V] 提升原子交换地址计算逻辑 [CL8724475](https://chromium-review.googlesource.com/c/8724475)

（12）[riscv] Skip the shift by zero in a Latin-1 regexp's prologue
[RISC-V] 在 Latin-1 正则序言中跳过零移位 [CL8780855](https://chromium-review.googlesource.com/c/8780855)

（13）[riscv] Skip the simulator's debugging checks unless one is enabled
[RISC-V] 未开启调试时跳过模拟器调试检查 [CL8765048](https://chromium-review.googlesource.com/c/8765048)

（14）[riscv] Make the simulator's AMOs atomic read-modify-writes
[RISC-V] 模拟器 AMO 实现为原子读改写 [CL8759153](https://chromium-review.googlesource.com/c/8759153)

（15）[riscv] Speed up instruction decoding in the simulator
[RISC-V] 优化模拟器指令解码速度 [CL8813064](https://chromium-review.googlesource.com/c/8813064)


### OpenJDK

本期审阅并合入的JDK主线PR链接:
- https://github.com/openjdk/jdk/pull/32604 (8391466: RISC-V: Remove unreachable non-acquiring CAS/GetAndSet/GetAndAdd match rules)
- https://github.com/openjdk/jdk/pull/32720 (8391881: RISC-V: jni_fast_Get<Primitive>Field registers the wrong pc for the speculative load)
- https://github.com/openjdk/jdk/pull/32727 (8390450: RISC-V: Add Xuantie vendor feature detection)
- https://github.com/openjdk/jdk/pull/32745 (8391942: RISC-V: Remove redundant null checks in needs_acquiring_load_reserved())
- https://github.com/openjdk/jdk/pull/31955 (8387725: RISC-V: Redundant memory barrier around various CAS instrucions)
- https://github.com/openjdk/jdk/pull/32718 (8391873: RISC-V: Prevent non-acquire CAS patterns from matching nodes that need acquire)
- https://github.com/openjdk/jdk/pull/32776 (8392015: Remove broken and untested VerifyStackAtCalls debug flag)
- https://github.com/openjdk/jdk/pull/32785 (8392041: RISC-V: TestFloat16ScalarOperations.java fails after JDK-8391717 with fastdebug)
- https://github.com/openjdk/jdk/pull/32635 (8391177: RISC-V: Optimize conditional arithmetic with Zicond)
- https://github.com/openjdk/jdk/pull/32806 (8392127: RISC-V: Replace assert with guarantee in patch_offset_in_jal and patch_offset_in_conditional_branch)

这些 PR 主要围绕 OpenJDK RISC-V 的硬件支持、性能优化和稳定性改进展开，可概括为四点：

- 扩展硬件支持：新增 Zibi 立即数比较分支指令支持，并补充玄铁处理器的厂商特性检测，更好地利用硬件能力（#32624、#32727）。
- 优化代码生成：减少访存时不必要的地址计算，利用 Zicond 优化条件算术运算，并在原子指令已提供所需内存序时消除外围冗余屏障（#32644、#32635、#31955）。
- 修复正确性问题：纠正 JNI 快速字段访问中推测性加载的 PC 记录，避免需要 acquire 语义的原子操作匹配到较弱的指令规则，修复半精度 FMA 的支持条件，并让分支偏移合法性检查在 release
  构建中也生效（#32720、#32718、#32785、#32806）。
- 清理冗余实现：删除不可达的非 acquire 原子操作匹配规则、多余的空指针检查，以及已损坏且缺乏测试的 VerifyStackAtCalls 调试选项和相关代码，降低维护成本（#32604、#32745、#32776）。

### Go

距离 Go 1.28特性冻结仅剩1周，因此本期变更基本聚焦于修复bug

本期提出的主线CL:

- 864281: math: optimize archExp/archExp2 on riscv64 | https://go-review.googlesource.com/c/go/+/864281 优化 riscv64 指数性能
- 864283: runtime/riscv64: use ABIInternal convention in cgocallbackg | https://go-review.googlesource.com/c/go/+/864283 cgocallback 使用ABIInternal
- 864243: test: disable fixedbugs/issue80271.go on riscv64 | https://go-review.googlesource.com/c/go/+/864243 修复blocker issue80271
- 765200: crypto/internal/fips140/aes: blockAsm enable zvkned for riscv64 | https://go-review.googlesource.com/c/go/+/765200 AES 块加解密【合入】
- 864662: database/sql: enable strict alloc checks for riscv64 | https://go-review.googlesource.com/c/go/+/864662 riscv64 开启 sql 分配内存的严格测试
- 864264: runtime: enable TestUnsafePoint on riscv64 | https://go-review.googlesource.com/c/go/+/864264 riscv64 开启 unsafepointer 测试

本期审阅的主线CL:

- 861706: cmd/asm/internal/asm: add tests for Zfa instructions on riscv64 | https://go-review.googlesource.com/c/go/+/861706 zfa 相关测试
- 732700: cmd/internal/obj/riscv: add assembly support of Zfa extension | https://go-review.googlesource.com/c/go/+/732700 添加zfa 扩展支持


### QEMU

## 社区动态


---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
