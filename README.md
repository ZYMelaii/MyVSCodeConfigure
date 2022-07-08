# My VSCode Configure

### Target Version
> `VSCodeSetup-x64-1.68.1.exe (windows)` <br>

### Initial Setup
Download an appropriate version of VSCode and setup for yourself. <br>
PS: replace official download server `az764295.vo.msecnd.net` (or anything else appeared in your download link) to `vscode.cdn.azure.cn` to speed up your download procedure. `[optional]`

### Recommended Extensions Installation
1. `Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code` <br>
    **brief** Language pack extension for Chinese (Simplified)
2. `Error Lens` <br>
    **brief** Improve highlighting of errors, warnings and other language diagnostics.
3. `Markdown All in One` <br>
    **brief** All you need to write Markdown (keyboard shortcuts, table of contents, auto preview)
4. `clangd` <br>
    **brief** C/C++ completion, navigation and insights based on clangd (LSP project of LLVM)

### Git Configure
1. Install `Git` for yourself.
2. Add `Git` to system PATH or turn to 3.
3. Mannually set `Git: Path` to the abosulte path of your Git in VSCode.
4. Enjoy yourself.

### Language Server Protocol Configure
Take many factors into consideration, my solution to LSP server is to install and configure clangd of LLVM project for VSCode.

1. Download latest LLVM released binaries from [official site](https://releases.llvm.org/) or manually build the projects from source code, install them to a propriate folder (marked as `$LLVM_ROOT`) afterwards.
2. Install `clangd` extension for vscode.
3. Open settings of extension `clangd`, set `Clangd: Path` to `$LLVM_ROOT\bin\clangd.exe` (type absolute path of clangd.exe here).
4. Modify `settings.json` of VSCode, append content as [`clangd.cfg`](./config/clangd.cfg).
5. Create `.clangd` file at the root path of workspace or at, edit as [`.clangd`](./config/.clangd) or whatever you want, for more information, browser [official site of clangd](https://clangd.llvm.org).
6. Enjoy yourself.

### Snippet Configure
- [C](./config/c.json)
- [C++](./config/cpp.json)

### Keybinding Configure
#### `Rebinded Commands`
- ★★★★★ `editor.action.blockComment` `"ctrl+shift+/"`
- ★★★★★ `editor.action.insertCursorAtEndOfEachLineSelected` `"ctrl+shift+l"`
- ★★★★★ `editor.action.selectHighlights` `"shift+alt+d"`
- ★★★★★ `breadcrumbs.focusAndSelect` `"ctrl+shift+."`
- ★★★★★ `editor.action.moveLinesUpAction` `"ctrl+shift+up"`
- ★★★★★ `editor.action.moveLinesDownAction` `"ctrl+shift+down"`
- ★★★★☆ `workbench.action.toggleSidebarVisibility` `"ctrl+alt+b"`
- ★★★★☆ `editor.action.quickFix` `"ctrl+shift+."`
- ★★★☆☆ `selectAllSearchEditorMatches` `"shift+alt+d"`
- ★★★☆☆ `addCursorsAtSearchResults` `"shift+alt+d"`
#### `Removed Commands`
- notebook.cell.detectLanguage
- editor.action.formatSelection
- editor.detectLanguage
- editor.action.toggleTabFocusMode
- editor.toggleFold
- editor.action.removeCommentLine
- editor.action.inPlaceReplace.up
- workbench.action.files.saveWithoutFormatting
- editor.action.copyLinesUpAction
- editor.action.copyLinesDownAction
- editor.action.insertCursorAbove
- editor.action.insertCursorBelow
- editor.action.autoFix
- clangd.typeHierarchy
- breadcrumbs.toggleToOn
- cursorColumnSelectDown
- cursorColumnSelectLeft
- cursorColumnSelectPageDown
- cursorColumnSelectPageUp
- cursorColumnSelectRight
- cursorColumnSelectUp
- problems.action.showQuickFixes
- workbench.action.openSettings