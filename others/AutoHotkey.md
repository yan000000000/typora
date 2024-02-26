# AutoHotkey

### intro

通过AutoHotkey， 可以自定义快捷键，用字母缩写打出一连串句子

* 通过发送键盘键击和鼠标点击自动化几乎所有的操作
* 为键盘，游戏杆和鼠标创建热键（自定义快捷键）
* 在键入缩写时拓展缩写（ily -> i love you
* 创建自定义数据输入表格，用户界面和菜单栏。重新映射键盘，游戏杆和鼠标上的按键
* 将任何脚本转化为exe文件。在没有安装AutoHotkey的计算机上也可以运行

### 官方文档

[official_En](https://www.autohotkey.com/docs/v2/)

[official_CN](https://wyagd001.github.io/v2/docs/misc/Remap.htm)



### 基本用法

```
#space::Run https://www.pptsupermarket.com/`
```

`#` -> [win 键]

`space` -> [空格]

`::` -> [代表每次按下此热键之后，随后的命令就会被执行]

`Run` -> [Run命令表示启动程序，文档，URL或者快捷方式]

### 基本符号对应键位

`#` -> [win 键]

`space` -> [空格]

`^` -> [CTRL]

`!` -> [ALT]

`+` -> [Shift]

`&` -> [用于连接两个按键合并成一个自定义热键]



### window默认快捷键

`Win + E` 打开资源管理器

`Win + D` 显示桌面

`Win + F` 打开查找对话框

`Win + R` 打开运行对话框

`Win + L` 锁定电脑

`Win + Q` 本地文件/网页等搜索

`Win + U` 打开设置-轻松使用设置中心



### 命令

#### 信息栏

```
MsgBox "Hello, world!"
```

弹出信息窗口

#### 运行程序， 打开文档，文件和URL

```
Run "C:\Windows\notepad.exe"
```

有些已经在系统中注册了路径的程序可以只传递文件名

```
Run "notepad"
```

### tips

`;` 表示注释



### 案例分析

```
#IfWinActive ahk_exe Typora.exe
{

	; Ctrl+Alt+o
	^!o::addFontColor("OrangeRed")
	
	; Ctrl+Alt+g
	^!g::addFontColor("#12b312")

	
}


addFontColor(color)
{
	Send {ctrl down}c{ctrl up} 
	SendInput {Text}<font color='%color%'>
	SendInput {ctrl down}v{ctrl up} 
	If(clipboard = "")
	{
		SendInput {TEXT}</font>{Left 7}
	}else{
		SendInput {TEXT}</
	}
}
```

* auto hot key is case insensitive so {text} or {TEXT} is fine
* the words behind {text} is string and # or ^ is inavailable
* := is equivalent to assignment in coding
* when = appear in if statement or while loop it mean comparison
* when you send </ as closing, typora will automatically complement the rest for you
* you can use {left} or {left n} order to move the cursor, similarly we have right Home

