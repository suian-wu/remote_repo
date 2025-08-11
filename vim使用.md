#### 在normal模式

`kjhl`:上下左右

`gg`:跳转第一行

`G`:跳转最后一行

`Ctrl+u`:往上翻半页

`Ctrl+d`:往下翻半页

`Ctrl+b`:往上翻一页

`Ctrl+f`:往下翻一页

`linenumber+gg`:跳转指定行数

`zz/zt/zb`:光标行设置为居中，第一行，最后一行

`w`:下一处单词开头

`b`:上一个单词开头

`e`:下一个单词结尾

`ge`:上一个单词结尾

`WBE`：大写表示非空字符，而小写表示最小单词

#### Insert模式

`i` :当前光标之前输入，大写是本行开头输入

`a`:当前光标之后输入，大写是本行结束输入

`o`:下方插入新的一行开始输入，上方插入新的一行

`s`:删除当前光标并开始输入，删除当前行开始输入

按 `Esc`进入 `normal`模式

#### command模式

在 `normal`模式输入：进入

`w`:保存

`q`:退出

`q!`:放弃更改退出

`wq`:保存更改退出

``Esc`:回到normal模式

#### visual模式

在 `normal`模式按v可进入

`x/y`:剪切、复制，回到normal后p粘贴

V进入行可视模式，一次选中一行

Esc回到

#### 基于搜索的移动

`f/t+char`:jump to the next char(before)in this line

`;/,`:quickly repeat the operation of f/t

`F/T+char`:the last char

`/+pattern`:jump to the pattern in this file

`?+pattern`:to the last pattern

`*`:(only)the same to /+pattern ,pattern is the present one

`n/N`:quickly repeat / operation

#### move based on the mark

 `m+mark`:mark the present place as "mark"

``+mark`:jump to the place marked as "mark"

` `` `:the last place before jump

##### `.  :the last place changed

##### `^  :the last place of word insertion

`^/$` :jump to the start/end in this line

`%`:jump to the suited opereation ()找一对操作符中另外的一个

#### operation+motion =action

`c`:change

`d`:delete

`y`:yank(copy)

`v`:choose the words and enter visual model

##### example:

`dgg`:delete until first line

`ye`:复制到单词结尾

`d$`:删除到行尾

`dt`:删除直到分号为止

##### 大部分操作符按两次作用在本行 `cc/dd/yy`

#### 重复操作

`.`:重复上一次修改

`u`:撤销上一次修改

`Ctrl+r`:重做上次修改（撤销之后

##### 文本操作对象

格式：`i/a+对象`（a表示加上后面一个空格，i表示只有字符）

example: iw is ip:单词、句子以及段落，还可以用各种括号将文本选择

##### 寄存器

一个字符对应一个：a-z,0-9

特别寄存器：

'':默认寄存器，复制删除放里面

%:当前文件名

. :上一次插入的内容

: :上一次执行的命令

通过 :reg{register}查看对应寄存器内容

##### 指定寄存器

在复制，删除，粘贴等操作前加上 ''{register} 可以指定本次操作所用的寄存器

example:

 `''ayy`:copy this line ,into register `a`

`''bdiw`:delete the word,save it into register `b`

`''cp`:将C寄存器中的内容粘贴出来

#### 宏

`q+register`:开始录制宏 存在寄存器中，再按退出操作

`@+register`:重放寄存器中的操作

   可以count + @+register来

### shell

##### 建立脚本： vi  [name].sh (用vim 这个编辑器写脚本)

##### 脚本内 ：

第一行：` #!/bin/bash （使用的路径解释脚本文件）`

##### 命令：

`echo` : print

`date`:show present date and time

`whoami`:show the user

##### 执行命令：

先要 `chmod a+x [name].sh`(增加权限)

then  `./[name].sh`

###### 语法相关

变量前加local才是局部变量

`lt`:less than

`gt`:greater than

`le`:less / equal

`ge`:greater/equal

`ne`:not equal


##### 输入输出重定向

 **`cat < hello.txt`**

* **作用** ：使用 **输入重定向** 将 `hello.txt` 的内容传递给 `cat`。
* **细节** ：
* `<` 表示将文件内容作为命令的  **标准输入（stdin）** 。
* 效果和 `cat hello.txt` 相同，但实现方式不同：
  * `cat hello.txt`：`cat` 直接打开文件。
  * `cat < hello.txt`：Shell 先打开文件，再将内容传给 `cat`。



#### git

#### `git reset`:

<img src="C:\Users\WU\Pictures\屏幕截图\屏幕截图 2025-08-10 222250.png" alt="屏幕截图 2025-08-10 222250" style="zoom:30%;" />

#### `git diff`:

1.git diff :比较工作区和暂存区的内容差别



2.git diff HEAD:比较工作区和版本库之间的差异



3.git diff --cached:比较暂存区和版本库之间的差异   



4.git diff  [version1 ID] [version2 ID]:比较两个版本的差异

`HEAD`：指向分支的最新提交节点，上面version ID 可以替换成HEAD

`HEAD~`:the last version的** 同上

`HEAD~[number]`:表示之前的几个版本



 5.在上述指令后加上文件名 就会只查看该文件的差异



#### `git rm`

|                          |                |                                       |
| ------------------------ | -------------- | ------------------------------------- |
| `git rm <file>`          | 删除文件       | 从暂存区和工作区中删除文件            |
| `git rm -f <file>`       | 强制删除       | 如果文件已修改或已暂存，必须加 `-f`   |
| `git rm --cached <file>` | 仅从暂存区删除 | 文件仍保留在工作区，但不再被 Git 跟踪 |
| `git rm -r <dir>`        | 递归删除目录   | 删除整个目录及其内容                  |



#### `.gitignore`:忽略文件

写入其中的文件会被忽略，不再被跟踪，内容更改也不会被检测

`dir/`:忽略文件夹

`/todo`:忽略当前文件夹下的todo文件

`*.a`:忽略所有.a文件

`doc/*.txt`:忽略一级目录下的文件

`doc/**/*.txt`:忽略所有子目录下的文件



<img src="C:\Users\WU\Desktop\Screenshot_20250811-140532-display-0.png.png" alt="Screenshot_20250811-140532-display-0.png" style="zoom:20%;" />
