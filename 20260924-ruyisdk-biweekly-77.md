# RuyiSDK 双周进展汇报 第 077 期 · 2026 年 09 月 24 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 新功能

- 侧边栏图标改为透明样式。
- 支持基于语义化版本号的比较对软件包、工具链进行排序。
- 软件包树视图的搜索提示更加醒目。
- 安装软件包时显示详细的进度信息。
- 支持检测虚拟工作区。
- 软件包详情中新增 slug 信息，同时从软件包标签中移除 slug。
- 运行本地化同步工具（sync-l10n）时自动重新生成 bundles。
- 修复工具链选择与 sysroot 选择行为不一致的问题。
- 修复仓库管理操作后软件包树未重新加载的问题。
- 修复软件包树视图的本地化问题。
- 清理资源后软件包树视图会自动刷新。
- 采用 esbuild 打包，消除打包警告。
- 在不受信任的工作区中禁止执行构建操作，提升工作区安全性。
- 删除虚拟环境时校验删除目标，并停用对应环境别名。
- 安装、更新 ruyi 前提示用户需要安装 "python3"、"python3-pip" 等软件包以使用 pip 或 pipx。
- 测试由 CI 构建的跨平台的 IDE。

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵

- 新增 HiFive Premier P550 的 Fedora 44 Server 中英文测试报告。[PR #400](https://github.com/ruyisdk/support-matrix/pull/400)
- 新增 SpacemiT K3 CoM260 Kit 的 Bianbu 4.0.6、OpenHarmony 6.1 中英文测试报告，并补充 openEuler 24.03-LTS-SP4 中英文待测文档。[PR #401](https://github.com/ruyisdk/support-matrix/pull/401)、[PR #402](https://github.com/ruyisdk/support-matrix/pull/402)、[PR #403](https://github.com/ruyisdk/support-matrix/pull/403)
- 更新 CH32V307 的 RT-Thread 5.3.1 中英文测试报告。[PR #404](https://github.com/ruyisdk/support-matrix/pull/404)
- 更新 Milk-V Duo S 的 Zephyr 4.1.99 中英文测试报告。[PR #405](https://github.com/ruyisdk/support-matrix/pull/405)

### 开发板示例仓库

- 新增 HiFive Premier P550 中英文板卡文档及 HelloWorld、CoreMark 示例。[PR #46](https://github.com/ruyisdk/board-docs/pull/46)
- 新增 SpacemiT K3 CoM260 Kit 中英文板卡文档和 HelloWorld 示例，补充中文 CoreMark 示例及 ROS 2 前两章课程入口。[PR #47](https://github.com/ruyisdk/board-docs/pull/47)
- 开发板文档前端新增课程前后章节导航，并在首页展示最新课程章节预览。[PR #11](https://github.com/DuoQilai/board-docs-frontend/pull/11)

### 官网&文档


## 基础组件


### 基础C库

### GCC

### LLVM

### V8
本期亮点：对Word32Equal，Word32NotEqual IR的代码生成进行了优化，优化后，提前编译（AOT）的内置库静态代码尺寸降低了2.7%。

本期提交并合入的patch：
1. **[riscv][sandbox] Remove kDefaultCodeEntrypointTag, pt.1**
   [RISC-V][沙箱] 移除 kDefaultCodeEntrypointTag（第一部分）[CL8400460](https://chromium-review.googlesource.com/c/8400460)
2. **[riscv][wasm-wide-arith] optimize nested 128 bit additions**
   [RISC-V][Wasm 宽位算术] 优化嵌套128位加法 [CL8404059](https://chromium-review.googlesource.com/c/8404059)
3. **[riscv] Fix 32-bit add/sub overflow check with dirty upper bits**
   [RISC-V] 修复高位脏数据场景下32位加减溢出检查 [CL8411269](https://chromium-review.googlesource.com/c/8411269)
4. **[riscv] Handle kProjection in ZeroExtendsWord32ToWord64NoPhis**
   [RISC-V] 在 ZeroExtendsWord32ToWord64NoPhis 中处理 kProjection [CL8413986](https://chromium-review.googlesource.com/c/8413986)
5. **[riscv][wasm] Fix safepoints in huge-frame stack check**
   [RISC-V][Wasm] 修复超大栈帧栈检查中的安全点 [CL8424461](https://chromium-review.googlesource.com/c/8424461)
6. **[riscv][wasm] Remove the trap_on_null bit/NullDereference memory access mode**
   [RISC-V][Wasm] 移除 trap_on_null 标记与空解引用内存访问模式 [CL8417701](https://chromium-review.googlesource.com/c/8417701)
7. **[riscv][wasm-wide-arith] optimize nested 128 bit additions**
   [RISC-V][Wasm 宽位算术] 优化嵌套128位加法 [CL8411268](https://chromium-review.googlesource.com/c/8411268)
8. **[riscv][wasm-wide-arith] Fix incorrect carry in Add128**
   [RISC-V][Wasm 宽位算术] 修复 Add128 进位错误 [CL8411517](https://chromium-review.googlesource.com/c/8411517)
9. **[riscv][compiler] Optimize Word32 equality/inequality comparisons**
   [RISC-V][编译器] 优化 Word32 相等/不等比较 [CL8414493](https://chromium-review.googlesource.com/c/8414493)
10. **[riscv] Fix ZeroExtendsWord32ToWord64NoPhis for atomic loads**
    [RISC-V] 修复原子加载场景下 ZeroExtendsWord32ToWord64NoPhis 逻辑 [CL8414976](https://chromium-review.googlesource.com/c/8414976)
11. **[riscv] Optimize tagged comparison branches with subw**
    [RISC-V] 使用 subw 优化带标记值的比较分支 [CL8411262](https://chromium-review.googlesource.com/c/8411262)
12. **[riscv] Fix Word32And zero test with dirty upper bits**
    [RISC-V] 修复高位脏数据下 Word32And 判零逻辑 [CL8403122](https://chromium-review.googlesource.com/c/8403122)
13. **[riscv] Fix register constraint field layout after AccessMode shrink**
    [RISC-V] 修复 AccessMode 缩减后的寄存器约束字段布局 [CL8431981](https://chromium-review.googlesource.com/c/8431981)

本期审阅并合入的patch：
1. **[riscv] Fix register clobbering for atomic compare-exchange**
   [RISC-V] 修复原子比较交换的寄存器覆盖问题 [CL8411976](https://chromium-review.googlesource.com/c/8411976)
2. **[riscv] Avoid clobbering expect value in atomic compare-exchange**
   [RISC-V] 避免原子比较交换中覆盖预期值 [CL8319928](https://chromium-review.googlesource.com/c/8319928)
3. **[riscv][maglev] Use public Float64Min/Max helpers**
   [RISC-V][Maglev] 使用公开的 Float64Min/Max 辅助函数 [CL8397048](https://chromium-review.googlesource.com/c/8397048)

### OpenJDK

### Go

### QEMU

## 社区动态
  [RuyiSDK 亮相 2026 云栖大会如意社区展台，展示 RISC-V 开发生态能力](https://ruyisdk.cn/t/topic/2849)：RuyiSDK 携多款 RISC-V 开发相关成果亮相云栖大会如意社区展台，现场展示一体化集成开发环境与软硬件资源共建成果，和参会开发者交流 RISC-V 生态进展。

---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
