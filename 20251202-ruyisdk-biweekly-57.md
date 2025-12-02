# RuyiSDK 双周进展汇报 第 057 期·2025 年 12 月 02 日

## 卷首语

## 包管理器

RuyiSDK 0.43 已于 11 月 26 日发布，对应的包管理器版本也为 0.43.0。您可前往以下位置之一下载 RuyiSDK 包管理器：

* [PyPI](https://pypi.org/project/ruyi/0.43.0/): `pip install ruyi`
* <https://github.com/ruyisdk/ruyi/releases/tag/0.43.0>
* <https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.43.0/>

> [!NOTE]
> RISC-V 用户可以使用 `pip` 安装 `ruyi`，但由于 `ruyi` 依赖的部分 Python
> 库暂未在 PyPI 上提供 RISC-V 架构的预编译包，安装 `ruyi` 时 Python
> 包管理器会尝试从源代码编译安装这些依赖，可能非常耗时或编译失败。
>
> 如果您在 RISC-V 设备上安装 `ruyi` 时遇到问题，建议使用其他安装方法。

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 允许在容器环境下以 `root` 身份运行 `ruyi` 了，以方便 CI 等受控场景。
* 会在新创建的 Ruyi 虚拟环境中记录所用 RuyiSDK 软件包的包名、版本号等元数据了，以便 RuyiSDK
  IDE 等 RuyiSDK 生态组件取用。
* 工程化迭代：
    * 支持了 Python 3.14 运行环境。
    * 移除了 `ruyi` 对 `packaging` 的依赖。请打包人员更新依赖声明。
    * 新增了集成测试框架，作为 `ruyi-litester` 的补充，有助于持续保证 `ruyi` 在小众场景下的功能不受破坏。

本次 RuyiSDK 软件源的更新主要包含了以下内容：

* 新增软件包：
    * `source/riscv-gnu-toolchain-plct`: `toolchain/gnu-plct` 的源码仓库集合。
* 新增设备支持：
    * Milk-V Jupiter: 兼容各类 Bianbu 镜像。
    * Sipeed LicheePi 3A: 兼容各类 Bianbu 镜像。
    * SpacemiT MUSE Book: 兼容各类 Bianbu 镜像。
    * SpacemiT MUSE Box: 兼容各类 Bianbu 镜像。
    * 香山南湖笔记本: 兼容 RedleafOS。
* 完善了设备支持：
    * 移除 Pine64 Star64 的 Armbian 支持: 上游已停止维护并不再提供系统镜像下载。
    * 适用各类 SpacemiT K1 设备的 Bianbu Desktop 与 Bianbu Minimal: 新增适用于 eMMC 存储设备的镜像。
    * 新增适用各类 SpacemiT K1 设备的 Bianbu Desktop Lite。

感谢 [@weilinfox] 的贡献！

[@weilinfox]: https://github.com/weilinfox

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。您也可以亲自参与
RuyiSDK 软件的打包与分发工作：目前您可以直接在 GitHub 上查看、修改我们的[部分打包脚本](https://github.com/ruyisdk/ruyici)与[软件源仓库](https://github.com/ruyisdk/packages-index)。今后，按照本年度的开发计划，我们也将支持有权的第三方贡献者通过程序化的方式上传软件包、系统镜像等分发文件，以便利打包工作。

## IDE

**VSCode 插件：**

**Eclipse 插件：**
 - 制定代码风格约束，审查所有代码。
 - 添加“新闻”模块。

## GCC

## LLVM

## V8
本期亮点：Zba扩展的shxadd指令可融合移位与加法，加速RISC-V的地址计算。V8实现了这项优化，结合偏移调整，加载指令数可减半（从4条指令降低为2条）。

本期提交的patch：
1. **[riscv] Encode AccessMode with kMemoryAccessProtectedNullDereference in visitAtomicLoad**  
   [RISC-V] 在visitAtomicLoad中使用kMemoryAccessProtectedNullDereference对AccessMode进行编码（https://chromium-review.googlesource.com/c/7165988）
2. **[riscv] Optimize Word64Add with shxadd instruction on RISC-V**  
   [RISC-V] 在RISC-V架构上通过shxadd指令优化Word64Add操作（https://chromium-review.googlesource.com/c/7155850）
3. **[riscv] Make the index as a immediate whenever possible**  
   [RISC-V] 尽可能将索引处理为立即数（https://chromium-review.googlesource.com/c/7155768）
4. **[riscv][wasmfx] Implement tag parameters and returns**  
   [RISC-V][wasmfx] 实现标签参数与返回值功能（https://chromium-review.googlesource.com/c/7202304）
5. **[riscv][maglev] Fix an issue where SMI values do not overflow correctly**  
   [RISC-V][Maglev] 修复SMI值溢出处理不正确的问题（https://chromium-review.googlesource.com/c/7202584）
6. **[riscv][codegen] Remove IsolateAddressId in favour of IsolateFieldId**  
   [RISC-V][代码生成] 移除IsolateAddressId，改用IsolateFieldId（https://chromium-review.googlesource.com/c/7214846）

审阅的patch：
1. **[riscv] Reset the rounding mode when returning from API**  
   [RISC-V] 从API返回时重置舍入模式（https://chromium-review.googlesource.com/c/6994659）
2. **[riscv] Fix loading of InstanceType in BaselineAssembler**  
   [RISC-V] 修复 BaselineAssembler 中 InstanceType 的加载逻辑问题（https://chromium-review.googlesource.com/c/7190169）
