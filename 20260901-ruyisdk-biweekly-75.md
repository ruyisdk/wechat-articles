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

### 版本测试及遗留问题

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


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 hypot、hypotf、expm1f、lgamma 和 lgammaf 至现有的 glibc libmvec 框架。
  - 基于 C908 针对 strstr 接口进行了初步调优。
- newlib:
  - 移植了 acospi、asinpi、atan2、atanpi 至现有的 newlib 向量数学框架。

### GCC

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

### OpenJDK

### Go

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
