## `GIT多平台推送`
```bash
平台一、coding 二、GitHub
生成SSH Key什么的就不说了自行百度 记得把pub文件里面的内容贴到平台里面
使用GitHub的时候 通过账号密码验证总是失败 这个时候SSH Key就有用武之地了，拉取项目 Use SSH 后续提交时候 避免输入账号密码
```
## [多平台配置](https://github.com/zhl6522/other/blob/master/%E6%89%93%E5%BC%80git%20bash%E7%9A%84%E6%97%B6%E5%80%99%E8%87%AA%E5%8A%A8%E5%90%AF%E5%8A%A8ssh%20agent.md)
## 多平台配置后的操作
```bash
多平台推送提交，不用命令行敲打即可完成：
代码界面直接提交'ctrl'+'k'，勾选当前的项目(新增文件需要点击'Unversioned Files')
'Before Commit'勾选的取消
'Commit Message'填写提交内容记录 下方可以比对修改的内容
代码界面直接推送'ctrl'+'shift'+'k'，推送分支到远程<"main->origin:main这里的origin点击换成github:main">（按钮冲突的话，'ctrl'+'shift'切换输入法）
```

ps:
后续可能出现的问题：如果有添加Git简写,Git命令简写识别不了，需要每次打开窗口执行 source ~/.bashrc
