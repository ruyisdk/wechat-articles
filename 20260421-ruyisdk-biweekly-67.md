# RuyiSDK 双周进展汇报 第 067 期·2026 年 04 月 21 日

## 卷首语


## 包管理器

RuyiSDK 0.48 预计将于下周发布，对应的包管理器版本也为 0.48.0。该版本的 Beta 测试版 0.48.0-beta.20260421 已于今日发布。您可前往以下位置之一下载 RuyiSDK 包管理器：

* 从 [PyPI](https://pypi.org/project/ruyi/0.48.0b20260421/) 安装：`pip install ruyi==0.48.0b20260421`
* 手动下载安装：
    * [GitHub Releases](https://github.com/ruyisdk/ruyi/releases/tag/0.48.0-beta.20260421)
    * [ISCAS 镜像源](https://mirror.iscas.ac.cn/ruyisdk/ruyi/testing/0.48.0-beta.20260421/)
* [使用文档](https://ruyisdk.org/docs/intro/)（[English](https://ruyisdk.org/en/docs/intro/)）

> [!NOTE]
> 对于 `ruyi` 的单文件二进制发行版，您必须将下载的文件重命名为一字不差的 `ruyi` 才能正常使用。

请注意：从 RuyiSDK 0.48.0 开始，Ubuntu 22.04 LTS 与 Python 3.10 环境不再受到支持。相关用户，尤其是发行版打包者、CI 环境维护者与仍在使用旧版 Python 运行环境的用户，在升级前请提前确认兼容性影响并完成验证。

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 新增了为虚拟环境指定自备 sysroot 的支持，现可在创建虚拟环境时使用目录形式的 sysroot 来源，不再局限于使用软件源中的现成 sysroot 软件包。
* 工程化迭代：
    * 调整了运行与构建环境基线，现已提升至 Ubuntu 24.04 LTS 与 Python 3.11。
    * 面向 RuyiSDK 一方与三方打包场景补充了软件包构建相关能力，并完善了构建配方机制及相关插件宿主实现。
    * 修复了部分类型标注与国际化细节问题。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 软件源格式更新：
    * 在软件源元数据中显式加入了软件源名称字段，便于后续更清晰地展示软件源信息。
* 完善了设备支持：
    * 为 Milk-V Duo 对应 profile 补充了 xthead quirk 指定，以改善相关目标场景下的配置准确性。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件


### Eclipse 插件

- 程序设计：清理 OSGi 配置文件。
- 程序设计：重新设计异常系统，重写部分错误信息。
- 程序设计：移除冗余封装，整理代码并适度封装逻辑。
- 兼容性：支持 Ruyi 0.47。
- 虚拟环境模块：调整向导页布局使其内容不被遮挡。
- 虚拟环境模块：不再自动更新索引。

## GCC
完成 P 扩展工具链向草案 020 版本的升级适配，确保实现与最新规范保持一致。
启动 RVP GCC intrinsic 更新工作，围绕草案变更内容推进接口与实现的同步完善。

## LLVM


## V8
本期提交的patch：
1. **[wasm][riscv] Disable partial OOB write optimization for Memory64**
   [WASM][RISC-V] 禁用 Memory64 的部分越界写入优化（https://chromium-review.googlesource.com/c/7733062）
2. **[riscv] Reland [wasm-wide-arith] Turboshaft x64 implementation of wide multiplication ops.**
   [RISC-V] 重新合入「[WASM 大位宽计算] Turboshaft x64 宽乘法指令实现」（https://chromium-review.googlesource.com/c/7722162）
3. **[riscv] Fix sign during Float64Round**
   [RISC-V] 修复 Float64Round 中的符号处理问题（https://chromium-review.googlesource.com/c/7734228）
4. **[riscv] Fix floating-point rounding in RISC-V simulator**
   [RISC-V] 修复 RISC-V 模拟器中的浮点舍入问题（https://chromium-review.googlesource.com/c/7722161）
5. **[riscv][wasm] Fix vector register save/restore order in growable stacks**
   [RISC-V][WASM] 修复可增长栈中向量寄存器的保存/恢复顺序（https://chromium-review.googlesource.com/c/7736871）
6. **[riscv][wasm][wasmfx] Preserve the target arg_buffer.**
   [RISC-V][WASM][WasmFX] 保留目标参数缓冲区 arg_buffer（https://chromium-review.googlesource.com/c/7743620）
7. **[riscv] Fix ToUint8Clamp in Maglev**
   [RISC-V] 修复 Maglev 中 ToUint8Clamp 实现问题（https://chromium-review.googlesource.com/c/7741807）
8. **[riscv] Remove OptimizedWord32Compare optimization**
   [RISC-V] 移除 OptimizedWord32Compare 优化（https://chromium-review.googlesource.com/c/7761051）
9. **[riscv] Modify the conversion of kNearest mode in Round**
   [RISC-V] 调整 Round 指令中 kNearest 模式的转换逻辑（https://chromium-review.googlesource.com/c/7767929）
10. **[riscv][compiler][fastapi] Fix type expectations for uint64 parameters**
    [RISC-V][编译器][Fast API] 修复 uint64 类型参数的类型匹配问题（https://chromium-review.googlesource.com/c/7769991）
11. **[riscv] Disable unaligned access support in V8 RISC-V backend**
    [RISC-V] 在 V8 RISC-V 后端关闭非对齐访问支持（https://chromium-review.googlesource.com/c/7763908）
12. **[riscv][interpreter] Move interrupt budget reduction to function entry**
    [RISC-V][解释器] 将中断预算递减逻辑移至函数入口处（https://chromium-review.googlesource.com/c/7769992）
13. **[wasm-interpreter] Port JSToWasmInterpreterWrapper into torque**
    [WASM 解释器] 将 JSToWasmInterpreterWrapper 迁移至 Torque 实现（https://chromium-review.googlesource.com/c/7455469）
14. **[riscv] Add Zfa extension**
    [RISC-V] 添加 Zfa 浮点扩展指令支持（https://chromium-review.googlesource.com/c/7768270）

本期审阅并合入的patch：
1. **[sandbox] Fix address space limit detection for RISC-V**
    [沙箱] 修复 RISC-V 架构下地址空间上限检测问题（https://chromium-review.googlesource.com/c/7731448）
