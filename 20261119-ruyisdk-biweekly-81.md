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


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 tanh, tanhf, tanpi, tanpif 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 hypotf, lgammaf, log10f, log1pf, powf, sincosf, sincospif, sinf, sinhf, sinpif, sqrtf, tanf, tanhf, tanpif 至现有的 newlib 向量数学框架。

### GCC

### LLVM

### V8

### OpenJDK

### Go

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
