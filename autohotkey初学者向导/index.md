# AutoHotkey初学者向导

原文改自 https://wyagd001.github.io/v2/docs/Tutorial.htm 作者 tidbit
## 1 - 基础

在开始我们的旅程之前, 让我给你一些建议吧. 在本向导中, 你会看到大量的文字和代码. 为了更有效的学习, 建议你阅读这些文字并 尝试 这些代码. 然后, 再深入学习这些代码. 你可以复制并粘贴此页上的大多数示例. 如果你弄糊涂了, 试着再看一遍.

### a. 下载并安装 AutoHotkey

在学习使用 AutoHotkey(AHK) 之前, 你需要下载它. 下载后, 你可能会需要安装它. 但这取决于你下载的版本. 对于本指南, 我们将使用安装版, 因为对于新手来说, 它最容易安装.

文字指导:

1. 访问 AutoHotkey 主页: [https://www.autohotkey.com/](https://www.autohotkey.com/)
2. 点击下载. 你应该会看到 AutoHotkey 的每个主要版本的选项. 此文档是针对 v2 的, 因此选择 v2 选项或切换到 v1 文档.
3. 下载的文件应该命名为 AutoHotkey_*_setup.exe 或类似的名称. 运行这个程序并单击 Install.
4. 装完了? 棒极了! 我们接着往下看.

### b. 如何创建一个脚本

Autohotkey 安装完成后, 你也许会想它能做些什么. AutoHotkey 不是魔法, 虽然我们都希望它是, 但它的确不是. 所以需要我们告诉它要去干什么. 而这个过程叫做 "写脚本".

文字指导:

1. 右键点桌面空白处.
2. 点击 "新建" 菜单.
3. 点击里面的 "AutoHotkey Script" 新建一个脚本.
4. 给脚本命名. 它必须带 .ahk 后缀. 例如: MyScript.ahk
5. 找到刚刚新建的脚本并右键点击它.
6. 点击 "Edit Script".
7. 一个新窗口被弹出, 也许是记事本. 如果是这样就成功了!
    
    现在你已经创建了一个脚本, 我们需要加点内容到脚本中. 有关所有内置函数和变量的列表, 请参阅[第 5 节](https://wyagd001.github.io/v2/docs/Tutorial.htm#s5).
    
    这是一个使用 [Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) 函数创建的一个包含热键的简单脚本, 当你按下热键后, 它会向窗口发送一段文字:
    
    ^j::
    {
        Send "My First Script"
    }
    
    稍后我们将进行更深入的研究. 在此之前, 我们先解释一下上面的代码:
    
    - `^j::` 是热键. `^` 代表 Ctrl, `j` 是字母 J. 任何在 `::` 左边 的字符表示您需要按下的热键.
    - `Send "My First Script"` 表示如何 **send(发送)** 按键. `Send` 是函数, 任何在空格之后括在引号内的内容都将被键入.
    - `{` 和 `}` 标志着[热键](https://wyagd001.github.io/v2/docs/Hotkeys.htm)的开始和结束.
8. 保存文件.
9. 双击桌面上的文件来运行它, 打开记事本或者其它可以输入文字的地方然后按下 Ctrl 和 J.
10. 太好了! 你的第一个脚本完成了. 给自己一些奖励, 然后返回阅读本教程的其余部分.

视频指导, 请在 YouTube 网站观看 [Install and Hello World](https://youtu.be/HcgQlGeaPHw).

### c. 如何在你的电脑上找到帮助文件

v2.0-a076 及以后版本的下载包含一个离线帮助文件, 与主程序位于同一压缩包中. 如果手动提取了这些文件, 那么帮助文件应该在你放置它的任何位置.

v2.0-beta.4 和以后版本包含安装脚本. 如果你已经使用这个来安装 AutoHotkey, 每个版本的帮助文件应该在安装 AutoHotkey 的位置的子目录中, 如 "C:\Program Files\AutoHotkey\v2.0-beta.7". 可能还有一个名为 "v2" 的符号链接指向最后安装的版本的子目录. 如果安装了 v1.x, 则根目录中可能还存在该版本的帮助文件.

寻找 **AutoHotkey.chm** 或一个名为 AutoHotkey 的文件, 图标上带有有一个黄色问号.

如果你不需要找到文件本身, 也有很多方法来启动它:

- 通过当前运行脚本的[托盘菜单](https://wyagd001.github.io/v2/docs/Program.htm#tray-icon)中的 "Help" 菜单选项.
- 通过当前运行脚本[主窗口](https://wyagd001.github.io/v2/docs/Program.htm#main-window)的 "Help" 菜单, 或在主窗口处于活动状态时按 F1.
- 通过 [Dash](https://wyagd001.github.io/v2/docs/Program.htm#dash) 的 "Help files (F1)" 选项 , 该选项可以用鼠标激活, 也可以在 Dash 激活时按 F1. Dash 可以通过开始菜单中的 "AutoHotkey" 快捷方式打开.

## 2 - 热键 & 热字串

什么是热键? 热键是一个发热的按键, 开个玩笑. 热键是用来触发某些动作的按键或组合按键. 例如:

^j::
{
    Send "My First Script"
}

什么是热字串? 当你键入它们时, 热字串主要用于扩展缩写(自动替换). 当然, 它也可以用来启动任何脚本动作. 例如:

::ftw::Free the whales

这两个例子的区别在于, 当你按下 Ctrl+J 时, 热键将会触发, 而热字串会将你输入的 "ftw" 转换为 "Free the whales".

_"那么, 该如何创建一个热键?"_ 好问题. 热键是通过一对冒号(::) 创建的. 按键名或组合按键名必须在 `::` 的 左边. 代码则跟在后面, 括在大括号里面.

**注意:** 当然也有例外情况, 但很多时候容易引起混乱, 所以在向导页中不会涉及到它, 至少不是现在.

Esc::
{
    MsgBox "Escape!!!!"
}

热字串在要触发的文本两边各有一对冒号(::). 替换后的文本在第二对冒号(::) 的 右边.

如上所述, 热字串也可以启动脚本动作. 和热键一样 _"几乎能做任何事情"_.

::btw::
{
    MsgBox "You typed btw."
}

有一个好消息是: 你可以为每一个热键, 热字串, 标签以及许多我们尚未讨论的其他内容编写多行代码.

^j::
{
    MsgBox "Wow!"
    MsgBox "There are"
    Run "notepad.exe"
    WinActivate "Untitled - Notepad"  _; 无标题 - 记事本_
    WinWaitActive "Untitled - Notepad"
    Send "7 lines{!}{Enter}"
    SendInput "inside the CTRL{+}J hotkey."
}

### a. 键和其神秘符号

你可能会问_"我怎么知道 ^ 代表 Ctrl?!"_. 好问题! 为了帮助你学习 ^ 和其它符号的意思, 注意看这个表:

|符号|描述|
|---|---|
|#|Win(Windows 徽标键)|
|!|Alt|
|^|Ctrl|
|+|Shift|
|&|用于连接两个按键(含鼠标按键) 合并成一个自定义热键.|

**(有关完整的符号列表, 请参阅[热键](https://wyagd001.github.io/v2/docs/Hotkeys.htm)页面)**

此外, 对于所有/大多数能用于热键双冒号**左边**的热键名称, 请参阅[按键列表](https://wyagd001.github.io/v2/docs/KeyList.htm).

你可以通过在两个按键(除控制器按键) 之间, 使用  `&`  来定义一个组合热键. 在下面的例子中, 你要按下Numpad0, 再按下Numpad1 或 Numpad2, 才能触发热键:

Numpad0 & Numpad1::
{
    MsgBox "You pressed Numpad1 while holding down Numpad0."
}

Numpad0 & Numpad2::
{
    Run "notepad.exe"
}

如果你想知道热字串是否和热键一样有很酷的修饰符, 答案是有!热字串的修饰符在第一对冒号(::) 之间, 例如. 例如:

:*:ftw::Free the whales

想要查看更多关于热键和热字串修饰符的信息和实例, 请参阅: [热键](https://wyagd001.github.io/v2/docs/Hotkeys.htm)和[热字串](https://wyagd001.github.io/v2/docs/Hotstrings.htm).

### b. 窗口特定的热键/热字串

有时候你也许想要热键或热字串只在某些特定窗口上工作(或禁用). 要做到这一点, 您需要使用其中的任意一个 "高级" 命令, 在它们前面带有一个 #, 即 [#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm), 结合内置函数 [WinActive](https://wyagd001.github.io/v2/docs/lib/WinActive.htm) 或 [WinExist](https://wyagd001.github.io/v2/docs/lib/WinExist.htm):

[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinActive
[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinExist

这些特殊的命令(技术上称为 "指令") 可以创建对上下文敏感的热键和热字串. 只需为 WinTitle 指定窗口标题. 但在某些情况下, 你可能需要指定诸如 HWND, 组或类的条件. 如果想深入了解这些高级内容, 点这里: [WinTitle 参数 & 上次找到的窗口](https://wyagd001.github.io/v2/docs/misc/WinTitle.htm).

[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinActive
#Space::
{
    MsgBox "You pressed WIN+SPACE in Notepad."
}

要关闭后续热键或热字串的上下文敏感性, 请指定 #HotIf 指令, 但不带参数. 例如:

_; Untitled - Notepad_
[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinActive
!q::
{
    MsgBox "You pressed ALT+Q in Notepad."
}

_; 任何标题不是无标题 - 记事本的窗口_
[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm)
!q::
{
    MsgBox "You pressed ALT+Q in any window."
}

当 #HotIf 指令在脚本中从未使用, 所有的热键和热字串对所有窗口生效.

#HotIf 指令是与位置相关的: 它会影响脚本中实际在它下面的所有热键和热字串, 直到下一个 #HotIf 指令.

_; 记事本_
[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinActive
#Space::
{
    MsgBox "You pressed WIN+SPACE in Notepad."
}
::msg::You typed msg in Notepad

_; MSPaint_
[#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) WinActive
#Space::
{
    MsgBox "You pressed WIN+SPACE in MSPaint!"
}
::msg::You typed msg in MSPaint!

有关更深入的信息, 请查看 [#HotIf](https://wyagd001.github.io/v2/docs/lib/_HotIf.htm) 页面.

### c. 一个文件包含多个热键/热字串

这是一些人的想法. 因此, 我在这里声明一下: AutoHotkey 有能力将 任意多 的热键和热字串放在一个文件中. 不管是 1 个, 还是 3253 个(或者更多).

#i::
{
    Run "https://www.google.com/"
}

^p::
{
    Run "notepad.exe"
}

~j::
{
    Send "ack"
}

:*:acheiv::achiev
::achievment::achievement
::acquaintence::acquaintance
:*:adquir::acquir
::aquisition::acquisition
:*:agravat::aggravat
:*:allign::align
::ameria::America

上面的代码是完全可以接受的. 多个热键, 多个热字串, 都包含在一个大的脚本文件里.

### d. 示例

::btw::by the way  _; 当您按下一个[默认的结束符](https://wyagd001.github.io/v2/docs/Hotstrings.htm#EndChars)时, 用"by the way"替换掉"btw"._

:*:btw::by the way  _; 替换 "btw" 为 "By the way" 而不需要按下结束符._

^n::  _; CTRL+N 热键_
{
    Run "notepad.exe"  _; 当你按下 Ctrl+N, 将启动记事本._
}  _; 热键内容结束, 这之后的内容将不会触发._

^b::  _; CTRL+B 热键_
{
    Send "{Ctrl down}c{Ctrl up}"  _; 复制选定的文本. 也可以使用 ^c, 但这种方法更加可靠._
    SendInput "[b]{Ctrl down}v{Ctrl up}[/b]" _; 将选定的文本包装在 BBCode 标签中, 以便在论坛中以粗体显示._
}  _; 热键内容结束, 当按下热键时, 下面的代码将不会被执行._

## 3 - 发送按键

现在你决定发送(输入) 一些按键到一个程序中. 你可以使用 [Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) 函数. 该函数表示发送按键, 模拟打字或按键操作.

但是在我们准备使用 Send 之前, 还有一些常见问题要注意.

就像热键一样, Send 函数也有一些特殊的键. 这里列出 4 个最常见的特殊按键:

|符号|描述|
|---|---|
|!|发送 Alt 键. 例如, `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "This is text!a"` 将发送按键序列 "This is text" 并接着按下 Alt+A. **注意:** `!A` 在某些程序中产生的效果与 `!a` 不同. 这是因为 `!A` 表示按下 Alt+Shift+A 而 `!a` 表示按下 Alt+A. 如果不确定, 请使用小写字母.|
|+|发送 Shift 键. 例如, `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "+abC"` 会发送文本 "AbC", 而 `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "!+a"` 会按下 Alt+Shift+A.|
|^|发送 Ctrl(Ctrl) 键. 例如, `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "^!a"` 会按下 Ctrl+Alt+A, 而 `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "^{Home}"` 则发送 Ctrl+Home. **注意:** `^A` 在某些程序中产生与 `^a` 不同的效果. 这是因为 `^A` 表示按下 Ctrl+Shift+A 而 `^a` 表示按下 Ctrl+A. 如果不确定, 请使用小写字母.|
|#|发送 Win 键(带有 Windows logo 的按键), 因此 `[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "#e"` 会在按住 Win 键时按下字母 "e".|

[Send 页面中有个很大的表格](https://wyagd001.github.io/v2/docs/lib/Send.htm#keynames)展示了 AHK 内置的几乎所有特殊键. 请点击查看. 例如: `{Enter}` 和 `{Space}`.

**警告:** 这个表 不 适用于[热键](https://wyagd001.github.io/v2/docs/Hotkeys.htm). 也就是说, 当你使用 Ctrl 或 Enter(或其它按键) 作为热键时, 不要将它们括在 {} 中.

一个例子显示了不应该对热键做的情景:

_; 当你创建热键时...
; 错误的_
{LCtrl}::
{
    Send "AutoHotkey"
}

_; 正确的_
LCtrl::
{
    Send "AutoHotkey"
}

很多人都有一个共同的问题, 他们认为大括号放在文档中仅仅是为了好玩. 而实际上 大括号是需要的. 它将告诉 AutoHotkey `{!}` 表示 "感叹号", 而不是要 "按下 Alt 键". 所以要仔细查看 [Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) 页上的特殊键表格, 确保在合适的地方加上大括号. 例如:

[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "This text has been typed{!}" _;  注意大括号中的感叹号? 这是因为, 如果没有 {}, AHK 将按下 Alt 键._

_; 跟上面的例子类似, 只是这次是 Enter 键. AHK 将会输出 "Enter"
; 如果 Enter 没有加上 {} 的话._
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "Multiple Enter lines have Enter been sent." _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "Multiple{Enter}lines have{Enter}been sent." _; 正确的_

另一个常见的错误是, 人们认为当使用 Send 函数时, **所有内容**都需要加上大括号. 这是不对的. 如果不在特殊按键列表中, 没必要加大括号. 你 不 需要给普通字符, 数字加上括号, 甚至像.(句点) 这些符号加上 {}. 而且, 当你在使用 Send 函数时, 你可以一次性发送多个字符, 数字或符号. 所以没有必要为每一个字符写上一条 Send 函数. 例如::

[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{a}"       _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{b}"       _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{c}"       _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{a}{b}{c}" _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{abc}"     _; 错误的_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "abc"       _; 正确的_

想要表示按住或松开某个按键, 可以将这个键用花括号围起来, 同时加上单词 UP 或 DOWN. 例如:

_; 下面这个例子表示按下一个键的时候再按下另一个键(或多个键)..
; 如果其中一个方法不奏效, 试试另一个._
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "^s"                     _; 表示发送 CTRL+S_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{Ctrl down}s{Ctrl up}"  _; 表示发送 CTRL+S_
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{Ctrl down}c{Ctrl up}"
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{b down}{b up}"
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{Tab down}{Tab up}"
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{Up down}"  _; 按下向上键._
[Sleep](https://wyagd001.github.io/v2/docs/lib/Sleep.htm) 1000        _; 保持 1 秒._
[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "{Up up}"    _; 然后松开向上键._

现在你可能会想, _"怎样才能让我在发送超长文本时保证可读性?"_. 很简单. 使用我们所说的延续片段. 只需要在新行指定一个开括号, 然后是内容, 最后在它自己的行上加上一个闭括号. 想了解更多信息, 请阅读[延续片段](https://wyagd001.github.io/v2/docs/Scripts.htm#continuation).

[Send](https://wyagd001.github.io/v2/docs/lib/Send.htm) "
(
Line 1
Line 2
Apples are a fruit.
)"

**注意:** Send 有几种不同的形式. 每种形式有其特性. 如果一种形式的 Send 函数不能满足你的需要, 可以试试另一种形式. 只需要将函数名称 "Send" 替换成接下来的其中一个: SendText, SendInput, SendPlay, SendEvent. 想要了解每一个命令的详细内容, [请阅读这里](https://wyagd001.github.io/v2/docs/lib/Send.htm).

### a. 游戏

**非常重要:** 一些游戏, 尤其是多人游戏, 使用反作弊程序, 例如 GameGuard, Hackshield, PunkBuster 等. 且不说绕开反作弊系统是违反游戏规定的, 绕开反作弊本身也不太容易实现.

如果游戏的反作弊系统导致你的热键, 热字串和 Send 函数失效, 你是不走运的. 然而有一些方法也许能提高在某些游戏中使用热键的可能性, 但_没人能打包票一定能行_. 所以, 尽可能尝试 所有 你能想到的办法, 不要轻易放弃.

还有一个关于 DirectX 的问题要注意. 当你在 DirectX 游戏中使用 AutoHotkey 碰到问题时, 试试 [FAQ](https://wyagd001.github.io/v2/docs/FAQ.htm#games) 页面中描述的情况. 当你使用 PixelSearch, PixelGetColor 或 ImageSearch 时, 你可能会碰到更多关于 DirectX 的问题. 画面颜色可能会变成黑色(0x000000), 不管你设置的是什么颜色. 如果可能的话, 试试用窗口模式运行游戏. 这样做能够解决一些 DirectX 问题.

没有万能的办法能确保 AutoHotkey 能运行在所有程序里. 如果你试了所有的办法还是不行, 也许 AutoHotkey 暂时无法满足你的需要.

## 4 - 打开程序 & 网页

想要打开诸如_画图(mspaint.exe), 计算器(calc.exe), 脚本.ahk_ 或一个文件夹, 你可以使用 [Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) 函数. 你还可以用这个命令打开一个网址, 比如 [https://www.autohotkey.com/](https://www.autohotkey.com/). 如果你想打开一个已经安装好的程序, 也很简单, 就像这样:

_; 运行一个程序. 注意, 大部分的程序可能需要完整路径:_
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) A_ProgramFiles "\Some_Program\Program.exe"

_; 打开一个网址:_
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) "https://www.autohotkey.com"

打开一个网址. 如果您想了解更多这方面的知识, 请访问 [Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) 页面.

下面是一些示例:

_; 一些程序并不需要完整路径, 如 Windows 标准程序:_
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) "notepad.exe"
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) "mspaint.exe"

_; 使用[内置变量](https://wyagd001.github.io/v2/docs/Variables.htm#BuiltIn)_来打开 "我的文档":
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) A_MyDocuments

_; 打开一些网页:_
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) "https://www.autohotkey.com"
[Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) "https://www.google.com"

想要深入了解更多信息和示例, 请查看 [Run](https://wyagd001.github.io/v2/docs/lib/Run.htm) 页面.

## 5 - 函数调用(有或没有参数)

在 AutoHotkey 中, 函数调用可以用或不用括号来指定. 通常只有在需要函数的返回值或函数名称没有写在行首时才需要使用括号.

所有内置函数的列表可以在[这里找到](https://wyagd001.github.io/v2/docs/lib/index.htm).

典型的函数调用是这样的:

Function(Parameter1, Parameter2, Parameter3) _; 带括号_
Function Parameter1, Parameter2, Parameter3  _; 不带括号_

参数支持任何类型的表达式; 例如:

1. 你可以使用运算:
    
    SubStr
    SubStr](https://wyagd001.github.io/v2/docs/lib/SubStr.htm)([A_Hour
    
2. 你可以在函数里面调用其他函数(注意, 这些函数调用必须用括号指定, 因为它们不在行首):
    
    SubStr](https://wyagd001.github.io/v2/docs/lib/SubStr.htm)([A_AhkPath](https://wyagd001.github.io/v2/docs/Variables.htm#AhkPath), [InStr](https://wyagd001.github.io/v2/docs/lib/InStr.htm)([A_AhkPath
    
3. 文本前后需要加上双引号:
    
    SubStr
    

最常见的将函数的返回值赋值给变量的方式是这样的:

**MyVar** := SubStr

这不是赋值的唯一方法, 但这是最常用的. 您使用 `MyVar` 来存储函数的返回值, 即写在 `:=` 运算符的右边. 有关详情, 请参阅[函数](https://wyagd001.github.io/v2/docs/Functions.htm).

简而言之:

_; 这些是没有括号的函数调用:_
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "This is some text."
[StrReplace](https://wyagd001.github.io/v2/docs/lib/StrReplace.htm) Input, "AutoHotKey", "AutoHotkey"
[SendInput](https://wyagd001.github.io/v2/docs/lib/Send.htm#SendInputDetail) "This is awesome{!}{!}{!}"

_; 这些是有括号的函数调用:_
[SubStr](https://wyagd001.github.io/v2/docs/lib/SubStr.htm)("I'm scripting, awesome!", 16)
[FileExist](https://wyagd001.github.io/v2/docs/lib/FileExist.htm)(VariableContainingPath)
Output := SubStr

### a. 代码块

[代码块](https://wyagd001.github.io/v2/docs/lib/Block.htm)就是用一对大括号(`{` 和 `}`) 包围起来的代码行. 们将一段代码组合在一起, 这样 AutoHotkey 判断这些代码是一个整体. 它们通常与函数和控制流语句(如 [If](https://wyagd001.github.io/v2/docs/lib/If.htm) 和 [Loop](https://wyagd001.github.io/v2/docs/lib/Loop.htm)) 一起使用. 如果不使用大括号, 只调用块中的第一行.

在下面的代码中, 只有当 _MyVar_ 等于 5 时, 才运行这两行代码:

[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (MyVar = 5)
{
    MsgBox "MyVar equals " MyVar "!!"
    ExitApp
}

在下面的代码中, 只有当 _MyVar_ 等于 5 时, 才能显示消息框. 脚本总是会终止退出, 而不管 _MyVar_ 是否等于 5:

[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (MyVar = 5)
    MsgBox "MyVar equals " MyVar "!!"
    ExitApp

这完全没问题, 因为 if-语句只有一行代码与之关联. 它和上面的完全一样, 但是我把第二行缩进了, 所以我们知道它和 if-语句是分开的:

[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (MyVar = 5)
    MsgBox "MyVar equals " MyVar "!!"
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "我们在 if-语句的 '外部'. 我们不需要大括号, 因为 if-语句下面只有一行."

## 6 - 变量

[变量](https://wyagd001.github.io/v2/docs/Variables.htm)就像一个包含信息的便利贴. 它可以用于函数或数学表达式中, 充当存储文本, 数字, 数据的作用. 如果没有变量, 程序和脚本将会非常乏味.

给变量赋值有很多方法, 我们将会讨论最常见的几种方法. 请特别留意冒号等号(`:=`).

文本赋值

MyVar := "Text"

这是给变量赋值最简单的方法. 只需输入文本并完成. 任何文本都需要加引号.

变量赋值

MyVar := MyVar2

和上面的方法类似, 只是你将一个变量所对应的值赋给了另一个变量.

数字赋值

MyVar := 6 + 8 / 3 * 2 - Sqrt

感谢表达式, 你可以进行计算!

混合赋值

MyVar := "The value of 5 + " MyVar2 " is: " 5 + MyVar2

以上三个赋值的组合.

等号(**=**) 和它前面的符号, 如 `:=` `+=` `-=` `.=` 等等, 这些被称为**赋值运算符**, 并且总是需要一个表达式.

### a. 获取用户输入

有时候你想让用户来选择某些值. 这可以有很多种方法, 但其中最简单的办法就是使用 [InputBox](https://wyagd001.github.io/v2/docs/lib/InputBox.htm). 下面的例子展示了如何向用户提出一系列问题并根据用户的输入完成一些事情:

OutputVar := InputBox.Value
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (OutputVar = "Bill")
    MsgBox "That's an awesome name, " OutputVar "."

OutputVar2 := InputBox.Value
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (OutputVar2 = "yes")
    MsgBox "Thank you for answering " OutputVar2 ", " OutputVar "! We will become great friends."
[else](https://wyagd001.github.io/v2/docs/lib/Else.htm)
    MsgBox OutputVar ", That makes me sad."

### b. 其它示例?

Result := MsgBox
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) Result = "No"
    return  _; 如果选择 No, 则停止代码继续._
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "You pressed YES."  _; 否则, 用户选择了 YES._

Var := "text"  _; 赋值一些文本给一个变量._
Num := 6  _; 赋值一个数字给一个变量._
Var2 := Var  _; 赋值一个变量给另一个._
Var3 .= Var  _; 追加一个变量到另一个的末尾._
Var4 += Num  _; 将变量的值与另一个相加._
Var4 -= Num  _; 将变量的值减去另一个._
Var5 := SubStr  _; 变量在函数中._
Var6 := Var "Text"  _; 赋值一个变量给另一个变量并带有一些额外的文本._
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm)(Var)  _; 变量在函数中._
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) Var  _; 同上._
Var := StrSplit  _; 变量在函数中, 用作 InputVar 和 OutputVar._
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (Num = 6)  _; 检查变量是否等于一个数字._
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) Num = 6  _; 同上._
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (Var != Num)  _; 检查变量是否等于另一个._
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) Var1 < Var2  _; 检查一个变量是否小于另一个变量._

## 7 - 对象

[对象](https://wyagd001.github.io/v2/docs/Objects.htm)是一种组织数据以实现更高效使用的方法. 对象基本上是变量的集合. 属于对象的变量称为 "属性". 对象还可能包含项, 例如数组元素.

您可能想要使用对象的原因有很多, 一些例子:

- 当你需要描述一组有序列表时, 比如杂货店列表(这种情况最好使用索引数组)
- 当你需要描述一个图形方格时, 比如一个棋盘游戏(这种情况最好使用嵌套对象)
- 当你需要描述一组事物而每样事物都有自己的名称时, 比如描述水果的特性(这种情况最好使用关联数组)

### a. 创建对象

我们有很多方法可以创建对象, 下面介绍最常用的几种方法:

方括号语法(Array)

MyArray := ["one", "two", "three", 17]

这将创建一个[Array](https://wyagd001.github.io/v2/docs/lib/Array.htm), 它表示项目列表, , 索引号从 1 开始连续递增. 在本例中, 值 `"one"` 存储在对象键 `1`(又叫做索引号1), 值 `17` 存储在对象键 `4`(又叫做索引号 4).

大括号语法

Banana := {Color: "Yellow", Taste: "Delicious", Price: 3}

这将创建一个 _ad hoc_ [对象](https://wyagd001.github.io/v2/docs/lib/Object.htm). 这是一种创建具有少量已知属性的对象的快速方法. 在这个例子中, 值 `"Yellow"` 存储在对象键 `Color` 中. 同样的, 值 `3` 存储在对象键 `Price` 中.

数组构造器

MyArray := Array

这种方式跟方括号语法形式一样. 它实际上是在调用 Array 类, 而不是函数.

Map 构造器

MyMap := Map

这将创建一个 [Map](https://wyagd001.github.io/v2/docs/lib/Map.htm), 或 _关联数组_. 在本例中, 值 `"Ctrl"` 与键 `"^"` 相关联, 值 `"Alt"` 与键 `"!"` 相关联. 通常用 `[Map](https://wyagd001.github.io/v2/docs/lib/Map.htm)()` 创建空映射, 然后用项目填充.

其他构造器

Banana := Fruit()

创建给定类的对象(在本例中为 Fruit).

### b. 使用对象

使用对象有很多方式, 包括检索值, 设置值, 添加更多的值等等.

#### 设置值

方括号表示法

MyArray[2] := "TWO"
MyMap["#"] := "Win"

在映射或集合中设置数组元素或项目类似于给变量赋值. 只需在包含对象(数组, 映射或其他) 的变量后添加方括号. 括号之间的索引或键是一个表达式, 因此对于任何非数值的文字值必须使用双引号.

句点表示法

Banana.Consistency := "Mushy"

这个例子为 _Banana_ 所包含的对象的属性赋一个新值. 如果属性不存在, 则创建它.

#### 检索值

方括号表示法

Value := MyMap["^"]

此示例检索先前与键 `"^"` 相关联(映射到) 的值. 键通常包含在一个变量中, 如 `MyMap[modifierChar]`.

句点表示法

Value := Banana.Color

这个例子检索对象 `Banana` 的 `Color` 属性.

#### 增加新的键和值

方括号表示法

MyMap["NewerKey"] := 3.1415

想要直接添加一对键和值, 只需设置一个尚不存在的键即可. 但是, 请注意, 当赋值给 [Array](https://wyagd001.github.io/v2/docs/lib/Array.htm) 时, 索引必须在 1 到数组当前长度的范围内. 不同的对象可能有不同的要求.

句点表示法

MyObject.NewProperty := "Shiny"

如前所述, 向尚未定义的属性赋值将创建一个新属性.

InsertAt(在..插入) 法

MyArray.InsertAt(Index, Value1, Value2, Value3...)

[InsertAt](https://wyagd001.github.io/v2/docs/lib/Array.htm#InsertAt) 是一个用于在[数组](https://wyagd001.github.io/v2/docs/lib/Array.htm)中的特定位置插入新值的方法, 但其他类型的对象也可以用这个名称定义方法.

Push(推送) 法

MyArray.Push(Value1, Value2, Value3...)

[Push](https://wyagd001.github.io/v2/docs/lib/Array.htm#Push) "追加" 值到[数组](https://wyagd001.github.io/v2/docs/lib/Array.htm) _MyArray_. 这是向数组中添加新元素的首选方法, 因为不能使用括号表示法在当前值范围之外赋值.

#### 移除属性和项目

删除方法

RemovedValue := MyObject.Delete(AnyKey)

[Array](https://wyagd001.github.io/v2/docs/lib/Array.htm) 和 [Map](https://wyagd001.github.io/v2/docs/lib/Map.htm) 有 Delete 方法, 该方法从数组或映射中删除值. `MyObject[AnyKey]` 的前一个值将存储在 _RemovedValue_. 对于数组, 这使数组元素没有值, 并且不影响数组中的其他元素.

Pop(抛出) 法

MyArray.Pop()

此 [Array](https://wyagd001.github.io/v2/docs/lib/Array.htm) 方法从数组中删除最后一个元素并返回其值. 数组的长度减 1.

RemoveAt(在..删除) 方法

RemovedValue := MyArray.RemoveAt(Index)

NumberOfRemovedKeys := MyArray.RemoveAt(Index, Length)

[Array](https://wyagd001.github.io/v2/docs/lib/Array.htm) 有 [RemoveAt](https://wyagd001.github.io/v2/docs/lib/Array.htm#RemoveAt) 方法, 它删除一个数组元素或数组元素的范围. 移除元素右边的元素(如果有的话) 被移到左边以填充空出的空间.

## 8 - 其他有用的东西

亲爱的朋友, 当你阅读到这里, 说明快要结束我们这段旅程了. 我希望你有所收获. 最后, 我将告诉你一些我认为你可能有用的东西. 希望你过的愉快!

### a. 神秘的 [ ]

在帮助文档中, 你可能会发现有两个符号(`[` 和 `]`) 经常出现在几乎每一页开头的黄色代码框中. 方括号中的内容代表 可选的. 也就是说, 如果你不需要这些参数你完全可以不管它. 不过要强调一点, 当你在写代码时, 千万 不要 把 [ ] 也写上了.

例如, 在 [ControlGetText](https://wyagd001.github.io/v2/docs/lib/ControlGetText.htm) 页面, 你可能会看到这段代码:

Text := ControlGetText(Control , WinTitle, WinText, ExcludeTitle, ExcludeText)

如果你愿意, 你可以简单地写成这样:

Text := ControlGetText

或者再加上一些细节:

Text := ControlGetText

如果你想只使用参数 _ExcludeTitle_ 而不想使用参数 _WinText_ 或 _WinTitle_ 怎么办? 很简单!

Text := ControlGetText

请注意, 你不能忽略参数, 只是需要将它们的位置留空. 如果你像下面这样忽略 `WinTitle, WinText`, 将会产生错误:

Text := ControlGetText

### b. 查找你的 AHK 版本

你可以运行下面的代码来查看你的 AHK 版本信息:

[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) A_AhkVersion

你也可以到开始菜单或安装路径下的帮助文件(AutoHotkey.chm) 中查找.

### c. 尝试与错误

尝试和错误是非常普遍而高效的学习方法. 与动不动就问这问那相比, 有时候花点时间(也许是长年累月) 亲手尝试可能会学的更快.

如果你在尝试新东西的过程碰到错误, 不要紧, 就从解决这个错误开始. 尝试解决这个错误, 一次不行就两次. 多次尝试后还是解决不了, 可以打开帮助文件学习哪些能做哪些不能做, 然后修改你的代码再试试. 试试, 失败, 试试, 失败, 试试, 试试, 再试试, 失败, 失败, **成功!**

这也是很多大师们的学习经历. 不过也不要害怕提问, 我们不会咬人(至少不会咬的太狠). 学习总需要时间慢慢积累, 大师也不是一天练成的.

"若最初你没有成功, 努力, 努力, 不断的努力." - 威廉 · 爱德华 · 希克森.

### d. 缩进

缩进这个事非常重要! 你的代码没有它也能正常运行, 可是如果没有缩进会让阅读代码变成一件非常痛苦的事. 也许一小段代码(少于 25 行) 不用缩进也没有太大关系, 但是代码一旦增多, 缩进就非常有必要. 所以, 学习使用缩进越快越好. 缩进没有固定的风格, 但最好保持一种风格.

"**什么是缩进?**" 你可能会问? 简单的说就是在代码和页面边界保留一段距离, 这样可以区分这一段代码是属于哪一段代码. 有些人习惯使用 3, 4 个空格或 1 个 tab 来表示缩进, 每一级用一次缩进.

不用缩进:

[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (car = "old")
{
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "The car is really old."
[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (wheels = "flat")
{
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "This car is not safe to drive."
[return](https://wyagd001.github.io/v2/docs/lib/Return.htm)
}
[else](https://wyagd001.github.io/v2/docs/lib/Else.htm)
{
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "Be careful! This old car will be dangerous to drive."
}
}
[else](https://wyagd001.github.io/v2/docs/lib/Else.htm)
{
[MsgBox](https://wyagd001.github.io/v2/docs/lib/MsgBox.htm) "My, what a shiny new vehicle you have there."
}

使用缩进:

[if](https://wyagd001.github.io/v2/docs/lib/If.htm) (car = "old")
{
    MsgBox "The car is really old."
    if
    {
        MsgBox "This car is not safe to drive."
        return
    }
    else
    {
        MsgBox "Be careful! This old car will be dangerous to drive."
    }
}
[else](https://wyagd001.github.io/v2/docs/lib/Else.htm)
{
    MsgBox "My, what a shiny new vehicle you have there."
}

关于缩进, 维基百科上[缩进样式](https://en.wikipedia.org/wiki/Indentation_style)页面有很多风格示例. 建议选一种你喜欢的或你认为最容易阅读的风格来学习.

### e. 寻求帮助

在你提问之前, 最好自己先研究一下或者自己先动手试着写代码. 如果自己实在得不到满意的结果, 请往下看.

- 不要害怕提问, 即使是世界上最聪明的人也需要别人的帮助.
- 不要害怕给别人看你写的代码, 就算你觉得代码有点弱智.
- 将所有你尝试的代码都贴出来.
- 假设 其他人 都是门外汉. 把你掌握的所有信息都教给我们这些门外汉. 帮助我们就是帮助你自己.
- 耐心.
- 礼貌.
- 开放.
- 友善.
- 祝你好运!

如果你没有马上得到答案, 至少等一天再提问. 我们乐于助人, 但是我们也是在自己的空余时间里免费提供帮助. 也许我们正在工作, 睡觉, 玩游戏, 和家人在一起或太忙了, 没有时间帮忙p.

在等待帮助时, 你也可以试着自己动手解决. 独立解决问题的感觉相当不错.
