# 我的VSCode配置历程

### 配置的VSCode目标版本
> `VSCodeSetup-x64-1.68.1.exe (windows)` <br>

### 安装VSCode
从VSCode官网下载一个合适的版本并按步骤安装。 <br>
PS: 国内用户如果下载速度太慢，可以将下载链接中的域名段（如`az764295.vo.msecnd.net`）替换为`vscode.cdn.azure.cn`（国内云服务器）来加速下载。

### 推荐安装的插件
1. `Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code` <br>
    **简介** VSCode简体中文语言拓展包
2. `Error Lens` <br>
    **简介** 更好的程序诊断高亮
3. `Markdown All in One` <br>
    **简介** Markdown集成拓展包（支持热键、表格、自动预览等）
4. `clangd` <br>
    **简介** LLVM用于C/C++的LSP服务器——clangd的VSCode支持插件

### Git配置
1. 安装Git。
2. 将Git添加到系统环境变量，或者按照步骤3操作。
3. 手动将已经安装的Git的绝对路径写入VSCode的`Git: Path`（可以直接在settings.json中添加或修改`git.path`属性）。

### C/C++的LSP配置
考虑多方面因素，我采用了LLVM的clangd来配置VSCode的LSP层。

1. 从LLVM的[官网](https://releases.llvm.org/)下载最新版的二进制发行文件或手动从项目源码编译，完成后将其安装到一个合适的目录中(此处记为 `$LLVM_ROOT`) 。
2. 为VSCode安装`clangd`拓展插件。
3. 在拓展插件`clangd`的配置中设置`Clangd: Path`为`$LLVM_ROOT\bin\clangd.exe`（即安装的clangd可执行文件的绝对路径）。
4. 编辑VSCode的`settings.json`文件，加入以下内容（必要时可去除所给内容中的注释）。
``` js
"clangd.arguments": [
    //! 在后台执行索引工作
    "--background-index",
    //! 指定依赖的clangd依赖的compile_commands.json所在的目录（可选）
    "--compile-commands-dir=build",
    //! 并行运行数目
    "-j=8",
    //! 启用clang-tidy
    "--clang-tidy",
    //! 指定clang-tidy检查目标文件与性能相关的条目及有错误编码倾向的编码块（访问官网`https://clang.llvm.org/extra/clang-tidy/`以获取更多信息）
    "--clang-tidy-checks=performance-*,bugprone-*",
    //! 若目标不存在的话，允许从代码补全中自动插入符号所属的索引域（如头文件）
    "--all-scopes-completion",
    //! 指定补全提示风格
    "--completion-style=detailed",
    //! 当应用代码补全的时候，允许插入#include引导
    "--header-insertion=iwyu",
    //! 允许缓存预编译头文件
    "--pch-storage=disk",
]
```
1. 在工作环境根目录创建`.clangd`并如下编辑（或自行调整）以细化`clangd`的配置（访问[官网](https://clangd.llvm.org)以获取更多信息）。
```yaml
###
# @file .clangd
# @brief configuration details for clangd
###
CompileFlags:
    Add: -std=c++20         # 启用C++20标准
Diagnostics:
    UnusedIncludes: Strict  # 标记未被使用的头文件
```