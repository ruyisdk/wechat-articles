# RuyiSDK 双周进展汇报 第 061 期·2026 年 01 月 27 日

## 卷首语

## 包管理器

RuyiSDK 0.45 已于今日发布，对应的包管理器版本也为 0.45.0。您可前往以下位置之一下载 RuyiSDK 包管理器：

* [PyPI](https://pypi.org/project/ruyi/0.45.0/): `pip install ruyi`
* <https://github.com/ruyisdk/ruyi/releases/tag/0.45.0>
* <https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.45.0/>

> [!NOTE]
> RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
> 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
> 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
>
> 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 由 `pipx` 安装的 `ruyi` 可以正常创建虚拟环境了。
* 包管理器（本体部分）现已支持简体中文本地化。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 完善了设备支持：
    * Milk-V Meles 的 RevyOS: 更新到 20251226。
    * Milk-V Pioneer 的 RevyOS: 更新到 20251226。
    * Sipeed Laptop 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheePi Console 4A 的 RevyOS: 更新到 20251226。
    * Sipeed LicheeRV Nano 的 Buildroot SDK: 更新到 20251230。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

### VSCode 插件

- 解压包模板功能添加suggested folder（一键选择解压到当前目录或子目录）
- 重构虚拟环境功能
- 修复vscode marketplace的图片失效问题

### Eclipse 插件

- 修复新闻模块第三方库的依赖问题。
- 虚拟环境模块支持自动探测工作区中的项目。
- 测试 Update Site 以准备上架 Eclipse Marketplace 。

## GCC

添加了Zalasr扩展支持，更新了P扩展文档手册。

## LLVM

xtheadvector 分支更新内容如下：
- [[LLVM][Clang][MC][XTHeadVector] add missing vncvt.x.x.w](https://github.com/ruyisdk/llvm-project/pull/167)


## V8
本期亮点：在SG2042平台上修复了两个Chromium主线上的构建bug

提交的patch如下：
1. **[riscv] Fix incorrect code gen**  
   [RISC-V] 修复不正确的ZBA指令代码生成逻辑（https://chromium-review.googlesource.com/c/7484947）
2. **[deoptimizer] fix comment**  
   [反优化器] 修复注释错误（https://chromium-review.googlesource.com/c/7459395）
3. **[riscv][maglev] Materialize undefined for undefined nan on exception**  
   [RISC-V][Maglev编译器] 针对异常场景下未定义的NaN，显式生成undefined值（https://chromium-review.googlesource.com/c/7484969）
4. **[riscv][acqrel] Added atomic acquire load and release store instructions**  
   [RISC-V][内存屏障] 添加原子获取加载（acquire load）和释放存储（release store）指令（https://chromium-review.googlesource.com/c/7489051）
5. **[riscv][wasmfx] Retire empty target stack for resume_throw**  
   [RISC-V][wasmfx] 清理resume_throw流程中空的目标栈（https://chromium-review.googlesource.com/c/7484970）
6. **[riscv][sandbox] Migrate TrustedPointerTable to range-based type checks**  
   [RISC-V][沙箱] 将TrustedPointerTable迁移为基于范围的类型检查机制（https://chromium-review.googlesource.com/c/7495671）
7. **[riscv] Implement AssembleArchSelect**  
   [RISC-V] 实现AssembleArchSelect功能（https://chromium-review.googlesource.com/c/7502457）
8. **[riscv] Skip pop simd128 in DeoptimizationEntry**  
   [RISC-V] 在反优化入口（DeoptimizationEntry）中跳过simd128的出栈操作（https://chromium-review.googlesource.com/c/7498990）
9. **[riscv] Eliminate -Wexit-time-destructors warnings**  
   [RISC-V] 消除-Wexit-time-destructors编译警告（https://chromium-review.googlesource.com/c/7508964）
10. **[riscv] Implement FP16 in simulator**  
    [RISC-V] 在模拟器中实现FP16（半精度浮点）功能（https://chromium-review.googlesource.com/c/7266607）


## 版本测试及遗留问题
