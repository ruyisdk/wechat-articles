# RuyiSDK 双周进展汇报 第 056 期·2025 年 11 月 18 日

## 卷首语

## 包管理器

## IDE

**VS Code插件：**
 - 添加解压 source 功能
 - 添加下载进度
 - 添加虚拟环境管理图形化入口
 - 将配置项（Ruyi 包管理器目录、遥测信息）移动至插件设置
 - 交付测试团队准备上架 vscode marketplace

**Eclipse 插件：**
 - 引入 CI 检查 DCO 规范并在 GitHub Pages 自动发布插件
 - 重构插件目录、优化现有文档
 - 解决 Eclipse SDK IDE 中的开发、调试问题

## GCC
修复了回归测试中发现的一些BUG，对仓库说明文档添加了中文支持，对Binutils测试模块进行了更新。

## V8
提交并合入的patch：
1. **[riscv][wasm][liftoff][growable-stacks] Do not change cache state in branch**  
   [RISC-V][WebAssembly][Liftoff编译器][可增长栈] 不在分支中修改缓存状态（https://chromium-review.googlesource.com/c/7123119）
2. **[riscv][cctest] Make max_heap_size larger in cctest/SetStackLimitInThreadAndStackOverflow**  
   [RISC-V][C++测试] 增大 cctest/SetStackLimitInThreadAndStackOverflow 中的最大堆大小（https://chromium-review.googlesource.com/c/7123484）
3. **[riscv][simulator] Only use read/write mutexes if we're multithreaded**  
   [RISC-V][模拟器] 仅在多线程场景下使用读写互斥锁（https://chromium-review.googlesource.com/c/7116238）
4. **[riscv][maglev] Cache the DataView's byteLength for the bounds check**  
   [RISC-V][Maglev编译器] 缓存 DataView 的 byteLength 用于边界检查（https://chromium-review.googlesource.com/c/7129740）
5. **[riscv] Fix native build failed**  
   [RISC-V] 修复原生构建失败问题（https://chromium-review.googlesource.com/c/7090433）
6. **[riscv] Use normal fp semantics in JSEntry**  
   [RISC-V] 在 JSEntry 中使用标准浮点语义（https://chromium-review.googlesource.com/c/7130358）
7. **[riscv] Catch wasm mem trap in amoswap**  
   [RISC-V] 在 amoswap 指令中捕获 WebAssembly 内存陷阱（https://chromium-review.googlesource.com/c/7144820）
8. **[riscv] Use amo instr in codegen**  
   [RISC-V] 在代码生成中使用 amo 系列指令（https://chromium-review.googlesource.com/c/7138845）
9. **[riscv][maglev] No implicit Float64 <=> HoleyFloat64 conversion**  
   [RISC-V][Maglev编译器] 不允许 Float64 与 HoleyFloat64 的隐式转换（https://chromium-review.googlesource.com/c/7149258）
10. **[riscv] Enable v8_enable_external_code_space**  
    [RISC-V] 启用 v8_enable_external_code_space（外部代码空间）功能（https://chromium-review.googlesource.com/c/7149198）
11. **[riscv] Fix missing AccessModeField encode**  
    [RISC-V] 修复缺失的 AccessModeField 编码逻辑（https://chromium-review.googlesource.com/c/7154551）
12. **[maglev][riscv] Replace the DataViewElementOperand with StoreDataViewElement/LoadDataViewElement**  
    [Maglev编译器][RISC-V] 将 DataViewElementOperand 替换为 StoreDataViewElement/LoadDataViewElement（https://chromium-review.googlesource.com/c/7155968）

审阅并合入的patch：
1. **[riscv] Fix deoptimization failure due to register clobbering**  
   [RISC-V] 修复因寄存器被破坏导致的去优化失败问题（https://chromium-review.googlesource.com/c/7139894）
2. **[riscv] Fix kIndirectPointer issue in store node selection**  
   [RISC-V] 修复存储节点选择中 kIndirectPointer 相关问题（https://chromium-review.googlesource.com/c/7123745）
3. **[riscv] Fix loading of is_marking_flag**  
   [RISC-V] 修复 is_marking_flag 的加载逻辑（https://chromium-review.googlesource.com/c/7126739）
4. **[riscv] Fix loading of ParameterCount**  
   [RISC-V] 修复 ParameterCount 的加载逻辑（https://chromium-review.googlesource.com/c/7134140）
5. **[riscv] Add right shift to extract the true ExternalPointerTag**  
   [RISC-V] 添加右移操作以提取真实的 ExternalPointerTag（https://chromium-review.googlesource.com/c/7123565）  
6. **[riscv] Use ToSimd128Register directly.**  
   [RISC-V] 直接使用 ToSimd128Register 方法（https://chromium-review.googlesource.com/c/7137621）
7. **[riscv] Use tail-undisturbed and avoid overwriting inputs**  
   [RISC-V] 采用RVV的tail-undisturbed模式，避免覆盖输入数据（https://chromium-review.googlesource.com/c/6989490）
8. **[riscv] Fix uintptr_t format specifiers in simulator**  
[RISC-V] 修复模拟器中 uintptr_t 类型的格式说明符问题（https://chromium-review.googlesource.com/c/7117264）
