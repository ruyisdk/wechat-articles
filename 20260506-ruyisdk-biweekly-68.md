# RuyiSDK 双周进展汇报 第 068 期·2026 年 05 月 06 日

## 卷首语


## 包管理器


## IDE

### VSCode 插件

- 新增一键编译系统
- 优化ruyi包管理器安装/升级逻辑
- 升级新欢迎页（初次安装或使用ruyi.home.show触发）
- 修复当用户安装新旧两个ruyi包管理器时，使用旧版本会出现“升级提示”
- 修复虚拟环境的sysroot为空

### Eclipse 插件

- 工程：维护各插件 OSGi 配置文件中信息的一致性。
- 兼容性：支持 Ruyi 0.47。
- 包管理器模块：设备列表支持手动刷新。
- 项目：发布 v0.1.3。

## GCC
更新GCC到16.1.0发布版，添加了Zalasr扩展支持。

## LLVM

- [RISCV][MC] Support experimental Zvdota Family instructions 
https://github.com/llvm/llvm-project/pull/195069
为 RISC-V 中的 Zvdota 扩展添加 MC 支持
正在 review

- [RISCV][MC] Add experimental Zvvmm MC support
https://github.com/llvm/llvm-project/pull/193956
为 RISC-V 的 Zvvmm 拓展增加初步的 MC 汇编支持
已经合并

- [InstCombine] Fold select of ordered fcmps of fabs over NaN-scrubber selects to a single select
https://github.com/llvm/llvm-project/pull/192182
将不可能是NaN的嵌套select ordered fcmp fabs 化简为单层select
已经合并

- [IRBuilder][NFC] Add CreateFAbs helper
https://github.com/llvm/llvm-project/pull/193421
在 IRBuilder 中创建并重构代码库中通用的 CreateFAbs 辅助函数
已经合并

## V8
本期提交的patch：
1. **[riscv][codegen] Fix signed integer overflow in Assembler::GrowBuffer**
   [RISC-V][代码生成] 修复 Assembler::GrowBuffer 中的有符号整数溢出问题（https://chromium-review.googlesource.com/c/7800114）
2. **[riscv] Reland [wasm][shared] Fix write barrier DCHECK for unshared cmpxchg of tagged**
   [RISC-V] 重提「[WASM][共享] 修复非共享标记比较交换的写屏障 DCHECK 问题」（https://chromium-review.googlesource.com/c/7804857）
3. **[riscv][wasm-wide-arith] Turboshaft x64 implementation of wide add op.**
   [RISC-V][WASM 大位宽计算] Turboshaft x64 宽加法指令实现（https://chromium-review.googlesource.com/c/7784730）
4. **[riscv][compiler] 10-bit ArchOpcodes**
   [RISC-V][编译器] 支持 10 位架构操作码（ArchOpcodes）（https://chromium-review.googlesource.com/c/7781567）
5. **[Reland "[riscv] Optimize code gen by zfa"]**
   [重提] [RISC-V] 基于 ZFA 扩展优化代码生成（https://chromium-review.googlesource.com/c/7785250）
6. **[riscv] Optimize float min/max codegen with ZFA extension**
   [RISC-V] 使用 ZFA 扩展优化浮点取最小/最大值代码生成（https://chromium-review.googlesource.com/c/7787832）
7. **[riscv][wasm-wide-arith] Implement Wide Multiplication in Liftoff**
   [RISC-V][WASM 大位宽计算] 在 Liftoff 中实现宽乘法指令（https://chromium-review.googlesource.com/c/7790661）
8. **[riscv][wasm-wide-arith] Implement Wide Multiplication in turboshaft**
   [RISC-V][WASM 大位宽计算] 在 Turboshaft 中实现宽乘法指令（https://chromium-review.googlesource.com/c/7790660）

本期审阅并合入的patch：
1. **[riscv] Fix typo in RVV SEW handling**
   [RISC-V] 修复 RVV SEW 处理中的拼写错误（https://chromium-review.googlesource.com/c/7763223）
2. **[highway: add riscv RVV to BROKEN_TARGETS]**
   [Highway] 将 RISC-V RVV 添加到 BROKEN_TARGETS 禁用列表（https://chromium-review.googlesource.com/c/7781707）
3. **[Download riscv64 sysroot when checkout_riscv64]**
   [构建工具] 执行 checkout_riscv64 时自动下载 riscv64 系统根文件系统（https://chromium-review.googlesource.com/c/7781706）

## 版本测试及遗留问题

### Ruyi 测试

报告 https://gitee.com/yunxiangluo/ruyisdk-test/tree/master/20260421

新增缺陷

| 缺陷 | 问题等级 | 判定依据 |
| --- | ---- | ----- |
| [bash-completion: not work properly when running ruyi for the first time #452](https://github.com/ruyisdk/ruyi/issues/452) | 一般 | 在边缘情况才会遇到 |
| [ruyi version: show welcome message before print ruyi version #453](https://github.com/ruyisdk/ruyi/issues/453) | 一般 | 在边缘情况才会遇到 |
| [ruyi extract --extract-without-subdir: does not print destination directory properly #454](https://github.com/ruyisdk/ruyi/issues/454) | 一般 | 在边缘情况才会遇到 |

### RuyiSDK Eclipse IDE 测试

本版本同步发版的 Eclipse 插件测试[报告](https://github.com/ruyisdk-test/ruyisdk-eclipse-plugins-test/tree/v0.1.3)。

新增缺陷

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [ruyi venv 没有显示虚拟环境名称，具体名称只会在sysroot路径列表出现 #151](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/151)   | 建议 |   |
| [ruyi-venv中的vnev path需要手动点击右侧列表，显示项目路径 #152](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/152) | 建议 |  |
| [ruyi-venv名称可以默认设置为ruyi-venv-profile属性 #153](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/153) | 建议 |  |
| [eclipse中版本检测中升级ruyi包管理器，显示由于不支持utf8报错 #154](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/issues/154) | 建议 |  |

### RuyiSDK VSCode IDE 测试

本版本同步发布的 VSCode 插件测试[报告](https://github.com/ruyisdk-test/ruyisdk-vscode-extension-test/tree/v0.1.3)。

新增缺陷

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [vscode插件更新后通过.vsix重新安装插件后存在缓存问题，仍是上个版本内容，建议加个重启vscode弹窗 #136](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/136) | 建议 |  |
| [ruyi-venv创建过程中配置sysroot选项中输入非法字符仍可正常配置sysroot #144](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/144) | 建议 |  |

## 测试结论

- 本版本包含遗留的严重缺陷，均按照修复时间表修复中；
- 本版本包含新增的一般缺陷，下一个版本修复；

