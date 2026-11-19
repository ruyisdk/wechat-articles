# RuyiSDK 双周进展汇报 第 081 期 · 2026 年 11 月 19 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

- 去除新闻页面无用的按钮
- 更新 l10n tools 文档

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
