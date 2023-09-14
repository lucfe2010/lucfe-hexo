# vs code shortcut

## 1

查找替换
Ctrl+F | 查找
Ctrl+H | 查找替换

F3 / Shift+F3 | Find next/previous
Alt+Enter | Select all occurences of Find match

Ctrl+D | Add selection to next Find match下一个匹配的也被选中

Ctrl+Shift+L | Select all occurrences of current selection同时选中所有匹配的
Ctrl+F2 | Select all occurrences of current word

Ctrl+K Ctrl+D | Move last selection to next Find match将光标移动到，搜索结果中的下一个

Ctrl+Shift+F | 整个文件夹中查找

file to include or exclude
path segment匹配符：
 `*` to match one or more characters in a path segment
? to match on one character in a path segment
 ** to match any number of path segments ,including none {} to group conditions
 e.g. `{**/*.html,**/*.txt}` matches all html and txt files
 [] to declare a range of characters to match
 e.g., example.[0-9] to match on example.0,example.1, …

## 2

显示相关
 全屏：F11
 zoomIn/zoomOut：Ctrl + =/Ctrl + -
 侧边栏显/隐：Ctrl+B

侧边栏4大功能显示：
  Show Explorer Ctrl+Shift+E
  Show Search Ctrl+Shift+F
  Show Git Ctrl+Shift+G
  Show Debug Ctrl+Shift+D

Ctrl+Shift+M Show Problems panel

Ctrl+` Show integrated terminal

  输出Show Output Ctrl+Shift+U
  预览markdown Ctrl+Shift+V

  Alt+Z Toggle word wrap

  Shift+Alt+0 Toggle editor layout (horizontal/vertical)

ctrl k + ctrl s = 打开快捷键一览表。

ctrl + , user settting

Ctrl+M Toggle Tab moves focus

## 6

编辑器与窗口管理

新建文件 Ctrl+N
Ctrl+F4, Ctrl+W Close editor
Ctrl+Shift+T Reopen closed editor
历史打开文件之间切换 Ctrl+Tab，Alt+Left，Alt+Right

Ctrl+Shift+PgUp / PgDn Move editor left/right

Ctrl+K P Copy path of active file

### show command palette

主命令框 Ctrl+Shift+P模式。或 F1

在Ctrl+P下输入>又可以回到主命令框 Ctrl+Shift+P模式。

#### quick open, go to file

直接输入文件名，快速打开文件
? 列出当前可执行的动作
! 显示Errors或Warnings，也可以Ctrl+Shift+M
: 跳转到行数，也可以Ctrl+G直接进入

 @ 跳转到symbol（搜索变量或者函数），也可以Ctrl+Shift+O直接进入
  `#` Show all Symbols，也可以Ctrl+T

## Rich languages editing

重命名：比如要修改一个方法名，可以选中后按F2，输入新的名字，回车，会发现所有的文件都修改过了。

跳转到下一个Error或Warning：当有多个错误时可以按F8逐个跳转

查看diff 在explorer里选择文件右键 Set file to compare，然后需要对比的文件上右键选择Compare with 'file_name_you_chose'.

Ctrl+Space 或 Ctrl+I Trigger suggestion

Ctrl+. Quick Fix

代码格式化：Shift+Alt+F，或Ctrl+Shift+P后输入format code

Ctrl+K Ctrl+F Format selection

### 重构代码

跳转到定义处：F12
定义处缩略图：只看一眼而不跳转过去Alt+F12

列出所有的引用：Shift+F12
同时修改本文件中所有匹配的：Ctrl+F12

## editing

| KEYS | ACTION |
| --- | --- |
| Ctrl + [ / ] | 代码行缩进 |
| Ctrl + Shift + [ / ] | 折叠打开代码块  |
| Ctrl+K Ctrl+0 | Fold (collapse) all regions |
| Ctrl+K Ctrl+J | Unfold (uncollapse) all regions |
| Ctrl + X | 如果不选中，默认复制或剪切一整行 |
| Ctrl + C | 如果不选中，默认复制或剪切一整行 |
| Alt + Up / Down | 上下移动一行 |
| Shift+Alt+Up 或 Shift+Alt+Down | 向上向下复制一行 |
| Ctrl+Enter | 在当前行下边插入一行 |
| Ctrl+Shift+Enter | 在当前行上方插入一行 |

## 光标相关

| KEYS | ACTION |
| --- | --- |
| Home | 移动到行首： |
| End | 移动到行尾： |
| Ctrl+End | 移动到文件结尾： |
| Ctrl+Home | 移动到文件开头： |
| Ctrl+Shift+\ | 移动到后半个括号 |
| Ctrl+L | Select current line 选中当前行 |
| Shift+End | 选择从光标到行尾 |
| Shift+Home | 选择从行首到光标处 |
| Ctrl + Shift + K | 删除光标所在行 |
| Ctrl + Left / Right | 一个单词一个单词的移动光标 |
| Shift + Left / Right | 一个字母一个字母的加入选择 |
| Ctrl + Shift + Left / Right | 一个单词一个单词的加入选择 |
| Shift + Alt + Left / Right | Shrink/expand selection（光标所在单词，文档高亮显示相同的） |

### multi cursor

| KEYS | ACTION |
| --- | --- |
| Alt+Click | Multi-Cursor：可以连续选择多处，然后一起修改，添加cursor |
| Ctrl+Alt+Down 或 Ctrl+Alt+Up | Insert cursor above / below  |
| Ctrl + Shift + Alt + (arrow key) | Column (box) selection |
| Shift+Alt+I | Insert cursor at end of each line selected |
| Ctrl+U | 回退上一个光标操作 |
| Ctrl+↑ / ↓ | Scroll line up/down |
| Alt+PgUp / PgDn | Scroll page up/down, not change the cusor location |

## comment

Ctrl+K Ctrl+C Add line comment
Ctrl+K Ctrl+U Remove line comment
Ctrl+/ Toggle line comment
Shift+Alt+A Toggle block comment

## 8
