# RuyiSDK 双周进展汇报 第 081 期 · 2026 年 11 月 19 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


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
