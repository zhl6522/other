```bash
拉取远程分支到本地：git fetch <远程主机名> <远程分支名>:<本地分支名>
                  git fetch origin zhl-test:zhl-test
构建出带tag的版本：go build -tags=v1.6.3 .
加速下载：export GOPROXY=https://goproxy.io

gco - //切到上一个分支
gm -  //合并上一个分支
glo   //拉取远程内容（远程有这个分支）
gpo   //推送内容到远程（远程有这个分支）
```
```bash
Git查找：
在git上快捷查找对应项目下的文件：
举例：https://github.com/zhl6522/other
在Code下面按"t"就会开启搜索模式

如果要快捷键接环到"Issues"下(https://github.com/zhl6522/other/issues)，按"gi"
如果要快捷键接环到"Pull requests"下(https://github.com/zhl6522/other/pull)，按"gp"
如果要快捷键接环到"Wiki"下(https://github.com/zhl6522/other/wiki)，按"gw"
如果想在当前控制面板中搜索内容，直接按"s"即可
按住shift+? 就可以把所有可以操作的快捷键都罗列出来

在对应文件中标注高亮给别人看：打开对应文件 选择查看的那一行，点击行号前面，然后在找到你要的最后一行，按住shift键点行号前面(就相当于建立了锚点)，这样把对应的url再分享给别人，别人就可以看到你标注的高亮内容了。
```
```bash
git问题记录：
  git克隆代码：warning: Negative patterns are ignored in git attributes Use '\!' for literal leading exclamation.
  克隆成功进入项目查看状态：git status (报错了)：segmentation fault
  $ git --version --build-options
  原来版本：git version 2.12.2.windows.1 更新版本：git version 2.32.0.windows.2
  如果上面这种方法解决不了问题，看下这种方法：https://github.com/RobinHerbots/Inputmask/issues/1646 + https://stackoverflow.com/questions/46169996/git-what-is-causing-warning-negative-patterns-are-ignored-in-git-attributes
```
```bash
Git合并时遇到冲突或错误后取消合并
	git merge --abort
```
