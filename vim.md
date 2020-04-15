# vi 常用命令

## 01. 一般模式

> 光标移动、复制粘贴删除、搜索替换等

### 1.1 移动光标

- <kbd>h</kbd>，<kbd>j</kbd>，<kbd>k</kbd>，<kbd>l</kbd>：上下左右移动一个字符
- <kbd>Ctrl</kbd>+<kbd>f</kbd> ，<kbd>Ctrl</kbd>+<kbd>b</kbd> ，<kbd>Ctrl</kbd>+<kbd>d</kbd> ，<kbd>Ctrl</kbd>+<kbd>u</kbd>： 上下移动一页/半页
- <kbd>+</kbd>，<kbd>-</kbd>：上下移动非空格符的一行
- <kbd>n<space></kbd>：例如 <kbd>20<space></kbd> 则光标会向后面移动 20 个字符
- <kbd>0</kbd>：移动到一行的最前面字符
- <kbd>$</kbd>：移动到一行的最后面字符
- <kbd>H</kbd>，<kbd>M</kbd>，<kbd>L</kbd>：移动到屏幕的最上/中/下方一行的第一个字符
- <kbd>G</kbd>：移动到文件的最后一行
- <kbd>nG</kbd>：例如<kbd>20G</kbd>则会移动到文件的第 20 行
- <kbd>gg</kbd>：移动到文件的第一行
- <kbd>n<Enter></kbd>：向下移动 n 行

### 1.2 复制粘贴删除

- <kbd>X,x</kbd>：向前/后删除一个字符
- <kbd>nx</kbd>：连续向后删除 n 个字符
- <kbd>dd</kbd>：删除一行
- <kbd>ndd</kbd>：例如<kbd>20dd</kbd>是删除 20 行
- <kbd>d1G</kbd>：删除到第一行的所有数据
- <kbd>dG</kbd>：删除到最后一行的所有数据
- <kbd>d$</kbd>，<kbd>d0</kbd>：~
- <kbd>yy</kbd>：复制该行
- <kbd>nyy</kbd>：复制 n 行
- <kbd>y1G</kbd>，<kbd>yG</kbd>：~
- <kbd>y0</kbd>，<kbd>y$</kbd>：~
- <kbd>p,P</kbd>：粘贴在下/上方
- *<kbd>J</kbd>：不常用*
- *<kbd>c</kbd>：不常用*
- <kbd>u</kbd>：复原前一个动作【撤销】
- <kbd>Ctrl</kbd>+<kbd>r</kbd>：重做前一个动作
- <kbd>.</kbd>：重复前一个动作

### 1.3 搜索替换

- <kbd>/word</kbd>，<kbd>?word</kbd>：向光标之下/上寻找一个名称为 word 的字符串
- <kbd>n,N</kbd>：如果刚刚执行 /vbird 去向下搜寻 vbird ，则按下 n 后，会向下继续搜寻下一个 vbird ；N 反向
- <kbd>:n1,n2s/word1/word2/g</kbd>：在 100 到 200 行之间搜寻 vbird 并取代为 VBIRD 则<kbd>:100,200s/vbird/VBIRD/g</kbd>
- <kbd>:%s/word1/word2/g</kbd>：从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 
- ***<kbd>:%s/word1/word2/gc</kbd>：且在取代前显示提示字符给用户确认 (confirm) 是否需要取代！***

## 02. 编辑模式

### 2.1 插入模式

- <kbd>i</kbd>：在目前光标所在处输入
- <kbd>I</kbd>：在目前所在行的第一个非空格符处开始输入
- <kbd>a</kbd>：从目前光标所在的下一个字符处开始输入
- <kbd>A</kbd>：从光标所在行的最后一个字符处开始输入
- <kbd>o,O</kbd>：在目前光标所在的下/上一行处输入新的一行

### 2.2  取代模式

- <kbd>r</kbd>：取代光标所在的那一个字符一次
- <kbd>R</kbd>：一直取代光标所在的文字，直到按下<kbd>ESC</kbd>为止

## 03. 指令行模式

### 3.1 储存离开等指令

- <kbd>:w</kbd>：保存
- <kbd>:w!</kbd>：强制写入
- <kbd>:q</kbd>：离开
- <kbd>:q!</kbd>：强制离开不保存
- <kbd>:wq</kbd>：~
- <kbd>ZZ</kbd>：若文件没有更动，则不储存离开，若已经被更动过，则储存后离开
- <kbd>:w [filename]</kbd>：另存为
- <kbd>:r [filename]</kbd>：将 [filename] 这个文件内容加到游标所在行后面
- <kbd>:n1,n2 w [filename]</kbd>：将 n1 到 n2 行的内容保存为 [filename] 文件
- <kbd>:! command</kbd>：暂时离开 vi 到指令行模式下执行 command 的显示结果！例如 [:! ls /home] 即可在 vi 当中察看 /home 底下以 ls 输出的档案信息！

### 3.2 显示行号

- <kbd>:set nu</kbd>：显示行号
- <kbd>:set nonu</kbd>：取消行号

## 04 可视块模式

- <kbd>Ctrl</kbd>+<kbd>v</kbd>：进入块选择模式
- 批量注释：进入块选择模式，移动光标选中要注释的行，按<kbd>I</kbd>进入行首插入模式输入注释符号，按两下 <kbd>ESC</kbd>即可