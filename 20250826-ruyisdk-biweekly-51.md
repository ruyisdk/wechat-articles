# RuyiSDK 双周进展汇报  第 051 期·2025 年 08 月 26 日

## 卷首语

## 包管理器

由于 RuyiSDK 团队正在对当前的 CI 流程深度整合以确保所有发布内容都能通过严格的测试，且主要成员正在
[2025 深圳国际电子展暨嵌入式展（elexcon2025）][elexcon]现场，RuyiSDK 包管理器的 0.40.0
版本将在下一期正式发布。您仍可通过以下渠道下载 RuyiSDK 包管理器的 0.39.0 版本：

* [PyPI][ruyi-0.39.0-pypi]: `pip install ruyi`
* [GitHub Releases][ruyi-0.39.0-gh]
* [ISCAS 镜像源][ruyi-0.39.0-iscas]

[elexcon]: https://www.elexcon.com/
[ruyi-0.39.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.39.0
[ruyi-0.39.0-pypi]: https://pypi.org/project/ruyi/0.39.0/
[ruyi-0.39.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/tags/0.39.0/

RuyiSDK 团队仍在常态化维护 RuyiSDK 软件源。如您已有 RuyiSDK 包管理器了，您可通过 `ruyi update` 获取近两周的更新：我们保证这些内容兼容 RuyiSDK 包管理器的近 3 个正式版本。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * Sipeed LicheePi 4A 的 RevyOS：新增 0.20250729.0 版本。
    * Sipeed LicheePi Console 4A 的 RevyOS：新增 20250720 与 20250729 版本。
    * Milk-V Meles 的 RevyOS：新增 1.20250729.0 版本。
    * SpacemiT K1 的 Bianbu Desktop 与 Bianbu Minimal，SD 卡版本：新增 v2.0.0 到 v3.0.1 之间的所有版本。
    * Milk-V Mars CM 的 Debian Desktop SDK：新增历史版本 `1.0.5+3.6.1`。
* 工程化迭代：
    * 修复了 `board-image/bianbu-bpi-f3` 与 `board-image/bianbu-desktop-spacemit-k1-sd` 的文件校验和。
    * 更新了 `board-image/bianbu-{desktop,minimal}-spacemit-k1-sd` 两包的上游版本元数据。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE
Eclipse 插件本期无进展，欢迎对Eclipse插件开发有兴趣的小伙伴加入开发团队，详情参考 [J159 RuyiSDK IDE 开发实习生](https://github.com/lazyparser/weloveinterns/blob/master/open-internships.md) ，期待您的加入。

## GCC

## LLVM

## V8
PLCT提交并合入的代码：

1. **[riscv] Optimize StackPointerGreaterThanOp Compare and Branch**  
   [RISC-V] 优化 StackPointerGreaterThanOp 的比较与分支操作  
   [chromium-review.googlesource.com/c/6862026](https://chromium-review.googlesource.com/c/6862026)
2. **[riscv] Optimize addi and signextend into addiw**  
   [RISC-V] 将 addi（立即数加法）与 signextend（符号扩展）优化合并为 addiw 指令  
   [chromium-review.googlesource.com/c/6861481](https://chromium-review.googlesource.com/c/6861481)
3. **[highway] fix compilation on riscv64**  
   [Highway 库] 修复在 riscv64 架构上的编译问题  
   [chromium-review.googlesource.com/c/6841716](https://chromium-review.googlesource.com/c/6841716)
4. **[riscv][turboshaft] Direct call for known functions**  
   [RISC-V][Turboshaft 编译器优化模块] 对已知函数采用直接调用方式  
   [chromium-review.googlesource.com/c/6838685](https://chromium-review.googlesource.com/c/6838685)

PLCT 审核并合入的代码：

1. **[risc-v] Only save clobbered registers when calling RecordWrite**  
   [RISC-V] 调用 RecordWrite 时仅保存被破坏的寄存器  
   [chromium-review.googlesource.com/c/6873602](https://chromium-review.googlesource.com/c/6873602)
2. **[riscv] Lower maximal code range size on riscv32 (2GB -> 256MB)**  
   [RISC-V] 降低 riscv32 上的最大代码范围大小（从 2GB 调整为 256MB）  
   [chromium-review.googlesource.com/c/6867912](https://chromium-review.googlesource.com/c/6867912)
3. **[riscv][liftoff] Block trampoline pool in OOL stack frame setup**  
   [RISC-V][Liftoff] 在 OOL 栈帧设置中阻塞蹦床池  
   [chromium-review.googlesource.com/c/6859316](https://chromium-review.googlesource.com/c/6859316)
4. **[riscv][wasm] Reverse order of spilled parameters in frame setup**  
   [RISC-V][WebAssembly] 在帧设置中反转溢出参数的顺序  
   [chromium-review.googlesource.com/c/6839045](https://chromium-review.googlesource.com/c/6839045)
5. **[riscv] Allow trampoline blocking to generate code in jump table tests**  
   [RISC-V] 允许蹦床阻塞在跳转表测试中生成代码  
   [chromium-review.googlesource.com/c/6842298](https://chromium-review.googlesource.com/c/6842298)
6. **[riscv] Fix alignment of jump table entries in assembler tests**  
    [RISC-V] 修复汇编测试中跳转表条目的对齐问题  
    [chromium-review.googlesource.com/c/6813493](https://chromium-review.googlesource.com/c/6813493)

## 操作系统支持矩阵

- [OrangePi RV2: Add Debian Trixie test report (basic).](https://github.com/ruyisdk/support-matrix/pull/357)
- [docs: Replace device names with placeholders](https://github.com/ruyisdk/support-matrix/pull/359)
- [docs: Correct sys_ver in LicheePi4A RevyOS README](https://github.com/ruyisdk/support-matrix/pull/360)
- [VF2: fix link typo](https://github.com/ruyisdk/support-matrix/pull/361)
- [Duo: Bump Buildroot to v2.0.1](https://github.com/ruyisdk/support-matrix/pull/363)
- [EIC7700X Board information supplement](https://github.com/ruyisdk/support-matrix/pull/364)
- [Add new boards, support status,test reports,documents and CI updates ](https://github.com/ruyisdk/support-matrix/pull/350)
