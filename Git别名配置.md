## `Windows下使用Git简写`
```bash
~/.gitconfig下不能配置带有git简写的（比如：gst=git status）
操作：
	1.新建 ~/.bashrc文件
	2.编辑文档
		alias ga='git add .'
		alias gb='git branch'
		alias gt='git tag'
		alias gba='git branch -a'
		alias gd='git diff'
		alias gst='git status'
		alias gcm='git commit -m'
		alias gco='git checkout'
		alias gf='git fetch'
		alias gm='git merge'
		alias glo='git pull origin'
		alias gpo='git push origin'
		alias gst='git status'
		alias ll='ls -l'
		alias ls='ls -F --color=auto --show-control-chars'			#自定义不同文件显示不同颜色
		alias php='winpty php.exe'						#Git for Windows下使用 winpty 进行字符流转换（ Git Bash 已自带）

	3.保存并source ~/.bashrc即可

alias可以查看Git别名配置
	
PS:Git多平台配置后，每次重新启动电脑后 别名配置很可能是打不开的，需要$ source ~/.bashrc
```
