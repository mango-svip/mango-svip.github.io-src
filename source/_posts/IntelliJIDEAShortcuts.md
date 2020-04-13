---
title: IntelliJ IDEA Shortcuts
date: 2020-04-07 14:02:08
comments: false
reward: false
---

### IntelliJ IDEA 快捷键整理
<!--more-->

##### 0、代码补全更多提示

```
win：Ctrl + j；mac：command＋j
输入：
iter    Iterate (for each..in)
itco  for (Iterator<String> iterator = locationUrl.iterator(); iterator.hasNext(); )
itin    Iterate (for..in)
itli    Iterate over a List
itit  while (iterator.hasNext())   // js中 for (var obj in _this)
itar    Iterate elements of array
ritar   Iterate elements of array in reverse order
iten  while (enumeration.hasMoreElements())
itve  for (int i = 0; i < vector.size(); i++)
怎么生成小于某个数字的循环？
   比如生成10次循环：
      1.正：10.fori
      2.反：10.forr
      就自动生成了
```

#### 1、查看注释：Win: Ctrl+Q, Mac: Control+J

```

补齐方法调用: tab，如果方法有参数，光标会自动定位在小括号内，
这个时候，使用commond+P或者Alt+P可以查看参数信息；
如果没有参数，直接定位在()后；
调用完毕，不需要再定位光标，直接 shift+command+Enter (win: Shift+Ctrl+Enter) 会自动补齐分号“;”，并自动定位到下一行。
 
1.2、新加文件自动加入版本控制设置
intellij同eclipse一样，可以设置新建文件就直接add进入版本控制中；
在settings –> Version control –> confirmation中选择add sliently即可

```

#### 2、进入调用的接口实现

```
Ctrl+B / Ctrl+Alt+B        在继承层次上跳转，分别对应父类或父方法定义和子类或子方法实现
Ctrl + Alt + mouse left key

```

#### 3、收起、展开 所有方法的快捷键是什么 ?

```
Ctrl+”+/-”，当前方法展开、折叠
Ctrl+Shift+”+/-”，全部展开、折叠
选择一部分代码,则收起或者展开选择部分的代码,不会影响其他地方的代码

```

#### 4、调用方法显示方法形参列表（列出变量，能根据形参名和变量名排序）

```
ctrl+shift+space

```

#### 5、idea 代码补全

```
alt + enter

```

#### 6、idea 字符大小写切换

```
ctrl + shift + u

```

#### 7、快速定位到语法错误的地方：

```
shift + f2
shift + f6 重命名

```

#### 8、引入try catch

```
Ctrl+Alt+T

```

#### 9、IntelliJ IDEA的自动提示貌似是区分大小写的，首字母小写的话，怎么都提示不出来


```
editor >general >code completion >case sensitive completion >none
这样就可以了

```

#### 9.1、修改文件后，目录变色、tab标签用星号 ＊标记修改过的文件

```
setting>version contro 勾上 show directorles with changed descendants
setting>Editor> general>editor tabs 勾上 Mark modifyied tabs with asterisk

```

#### 9.2、开启自动编译

```
File->setting->compiler 勾选Make project automatically

```
#### 10、代码提示 keymap-completion

```
问题：Idea代码自动补全默认快捷键是 Ctrl + 空格。与输入法快捷键冲突
修改：
点击 文件菜单(File) –> 点击 设置(Settings… Ctrl+Alt+S), –> 打开设置对话框，
在左侧的导航框中点击 KeyMap -> 选择 Main menu –> Code –> Completion
接着需要做两件事：
1. 在Cycle Expand Word 上右击，移除原来的 Alt+/(斜杠) 快捷键绑定。
2. 在 Basic 上点击右键，移除原来的 Ctrl+空格 绑定，然后添加 Alt + 斜杠 快捷键。
然后应用(Apply), OK.

```

#### 11、快速生成代码，如：getter setter

```
alt + insert

```
 
#### 12、优化导入的类和包

```
Ctrl+Alt+O
更好的方法：在settings中搜索Auto Import，即setting—>Editor—>Auto Import（勾选下面两项自动导入class并优化导入的class），
勾选：Add unambiguous imports on the fly 和 Optimize imports on the fly（连Ctrl+Shift+O都省了，是不是很爽）

```
#### 13、方法调用链

```
alt + f7          查找那些类调用该资源（资源可能是字段、方法、类）
Ctrl + alt + f7    快速显示查找内容

```
#### 14、回车能自动跳到行尾

```
Ctrl+Shift+Enter(跳到行尾并且自动补全行末尾内容，如分好，if等后的大括号）

```

#### 15、在editor间来回切换多个打开的tab页

```
Ctrl+ Tab

```
#### 16、 复制当前行到粘贴板， Ctrl+C（不要选中任何内容）
 
#### 17、Ctrl+Shift+V 高级粘贴。。
 
#### 18、查找文件

```
Ctrl+shift + n       通过文件名查找文件
Ctrl+Alt+Shift+N    前往指定的变量 / 方法
Ctrl+n          通过class名查找
Double Shift    双击Shift搜索文件或内容
Ctrl + shift +a     查找动作或设置

```
#### 19、Alt +Q      快捷显示当前行在哪个方法里(如果方法体太长，一屏显示不下这个很有用）
 
#### 20、查看/补全 调用方法的参数列表

```
Ctrl+P        查看方法参数（或叫方法签名) ，这个功能叫parameter info
Ctrl+Shift+Space    光标在调用的方法名上按，显示方法参数信息；光标在调用的方法的括号中按，显示选择补全参数

```

#### 21、Ctrl+Q    查看方法文档注释

```
doc文档快速显示，光标悬停到方法上时，显示文档注释设置：
setting -> Editor -> General -> 勾选Show quick documentation on mouse move

```
 
#### 22、IDEA默认支持zen coding，写html再也不用敲尖括号了.，补全的快捷键是tab，不是Alt+/
 
#### 23、Ctrl + Mouse Wheel    编辑器字体随鼠标滚动变更字体

```
设置：setting -> Editor -> General -> 勾选Change font size(Zoom) with Ctrl+Mouse Wheel

```
#### 24、idea列编辑模式

```
alt + capslk(大小写切换) + 鼠标左键    Eclipse：alt+shit+a

```
#### 25、定位到上次编辑的位置

```
Ctrl + Alt + left（right）

```
#### 26、切换窗口：

```
Alt+Num        常用的有1-项目结构，3-搜索结果，4/5-运行调试。
Ctrl+Tab        切换标签页，Ctrl+E/Ctrl+Shift+E打开最近打开过的或编辑过的文件

```
#### 27、运行：Alt+Shift+F10运行程序，Shift+F9启动调试，Ctrl+F2停止
 
#### 28、新建：Alt+Insert可以新建类、方法等任何东西
 
#### 29、Ctrl + shift (+ 或 -)     折叠、收起代码
 
#### 30、Ctrl+F12    查看当前类的所有方法用
 
#### 31、要查找文本的出现位置就用Ctrl+F/Ctrl+Shift+F在当前窗口或全工程中查找，再配合F3/Shift+F3前后移动到下一匹配处
 
#### 32、格式化代码Ctrl+Alt+L
 
#### 33、Ctrl + R 替换
 
#### 34、Ctrl + alt + v 选中未声明变量的代码，为代码抽取变量
 
#### 35、IDEA 编辑窗口开多后自动关闭问题


```
Settings >> Editor >> General >> Editor Tabs中修改“Tab limit”值即可

```
