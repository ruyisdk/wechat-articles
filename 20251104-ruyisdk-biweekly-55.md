# RuyiSDK 双周进展汇报 第 055 期·2025 年 11 月 04 日

## 卷首语

## 包管理器

## IDE

**VSCode 插件：** ：
- 新闻:
  - 将新闻缓存到本地供离线查看
  - 新闻列表可手动刷新
  - 新闻列表由树状改为卡片式
- 虚拟环境:
  - 创建新的虚拟环境
  - 管理当前激活的虚拟环境
  - 删除虚拟环境
  - 发现已存在的虚拟环境
- 遥测: 提供配置选项
- 管理 Ruyi:
  - 检查 Ruyi 版本更新
  - 提供多种安装 Ruyi 的方式
- 优化代码结构，更新依赖，更新 linter

**Eclipse 插件：**
- 支持构建包含 RuyiSDK 插件的 RuyiSDK IDE

## GCC

## LLVM

Upstream:
- [LLDB][Editline] empty current line before el_wgets 
 lldb (https://github.com/llvm/llvm-project/pull/165830)
- [LLDB][DWARF] Use the same qualified name computation for Rust 
 lldb (https://github.com/llvm/llvm-project/pull/165840)

## V8
**提交的patch：**
1. **[riscv] Fix incorrect check supports_wasm_simd_128**  
   [RISC-V] 修复 supports_wasm_simd_128 的错误检查逻辑（https://chromium-review.googlesource.com/c/v8/v8/+/7087478）
2. **[riscv][simulator] Only use read/write mutexes if we're multithreaded**  
   [RISC-V][模拟器] 仅在多线程场景下使用读写互斥锁（https://chromium-review.googlesource.com/c/v8/v8/+/7116238）
3. **[riscv] Fix native build failed**   
   [RISC-V] 修复原生构建失败问题（https://chromium-review.googlesource.com/c/v8/v8/+/7090433）
