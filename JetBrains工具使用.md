# [IDE下载安装激活](https://github.com/zhl6522/other/blob/master/IDE%E6%BF%80%E6%B4%BB.md)
-------------------------------------------------------------------------------------
## `官方汉化（2020 年开始）`
```bash
输入快捷键：Ctrl+Shift+A — 输入plugins - 选择Plugins - 搜索里面查找：Chinese（Simplified） Language Pack/中文语音包
```
## `菜单栏显示`
```bash
输入快捷键：Ctrl+Shift+A — 选择Actions — 输入menu 在Main Menu后边打开开关即可。
```

## `以 PHPstorm项目编辑器为主，其他JetBrains系列的也支持`
```bash
view
	Toobar
	Status tar
	隐藏掉
	Tool Buttons不隐藏，里面的"Terminal"可以执行artisan命令（但是不能识别简写命令）

首选项（settings）
	搜索 bread 勾掉
							
	
每打开的页面的tab -> none (Ctrl+e 就可以看到最近打开的)[开启方法：settings-->Editor-->General-->Editor Tabs-->Placement改成top]

Ctrl+e 切换之前打开的文件

Ctrl+h 查找文件里面对应的方法名

Ctrl+Shift+a -> keymap ->左边的search输入内容:live Temp...  
					Editor
						live Templates
							html/xml
								+ftext、fpass
							php
								+class、pub
								(
								/**
								 * $NAMES$
								 * @param    $data
								 * @return   array
								 */
								public function $NAME$() {
								    $END$
								}
								)
							go
								+ife
								(
								if err != nil {
								 fmt.Printf("$KEY$\n",$VAR$)
								 return
								}
								$END$
								)
						Ps:保存的时候change选择相应的文件类型
file==>settings==>live templates==>选择你要设置的语言，右边的“+”添加规
html内容快捷键：
	ftext+Tab
		Form text input

Alt+1 左侧项目目录展示

Settings==>Editor==>General
	再把“use soft wraps in editor”的勾打上，保存应用(代码自动换行)；(新版PHPstorm 同后面括号内容一样："; *.php; *.html; *.js")[Goland的Soft-wrap files加上“; *.go”]
	
(部分情况下：安装主题后)自动保存,这个功能比较重要，经常会忘记保存代码，导致麻烦,解决的办法是
Ctrl+Shift+a---setting----Apperrance&Behabvior--------systemSetings---右边下面有个Synchronization---勾选Save files automatically if application is idle for 15 sec,时间可以自己设置

一键格式化代碼： Ctrl+Alt+L
	
单元测试代码(文档是给开发者看的，更友好)，使用驼峰(PSR2规范看着不舒服，可以使用下划线)，操作步骤：
	file==>settings==>Plugins 搜索 CamelCase Browse repositories...安装 
	对方法按 option+Shift+u 进行变换(Mac);windows下的变换是让人失望的
	
	注释中 @test 声明测试
	
方法代码全部收起：'ctrl'+'shift'+'-'，全部展开：'ctrl'+'shift'+'+'
鼠标所在位置向外扩选：'ctrl'+'w'
展示左侧文件目录：'Alt'+'1'
展示当前PHP文件的方法：'Alt'+'7'(如果满屏的话，点击小菊花图案->Move to->Left Bottom，再次按'Alt'+'1')
代码界面直接提交'ctrl'+'k'，勾选当前的项目(新增文件需要点击'Unversioned Files') 'Before Commit'勾选的取消 'Commit Message'填写提交内容记录 下方可以比对修改的内容
代码界面直接推送'ctrl'+'shift'+'k'，推送分支到远程（按钮冲突的话，'ctrl'+'shift'切换输入法）
'VCS'上点击也可以实现功能，文件中右键'Git'也可以
'alt'+'f12'展示出其开发工具的命令行模式，再次执行即可隐藏
双击SHIFT        # 在当前项目中搜索（文件名、类、方法、函数等等）
CTRL+SHIFT+F    # 在当前项目/路径中查找字符串（说明：这个快捷键可能和输入法的快捷键有冲突。替换用：CTRL+SHIFT+R）
CTRL+G          # 跳转到对应行

PHPstorm查看文件之后编辑时间及编辑人员：
	Xcxscgi.php 行数位置右键->Annotate
```
