```bash
在C:/Users/userName/ 目录下，新建一个.profile文件，粘贴以下内容：
------------.profile--------------
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add ~/.ssh/id_rsa
    ssh-add ~/.ssh/id_rsa_gitlab
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add ~/.ssh/id_rsa
    ssh-add ~/.ssh/id_rsa_gitlab
fi

unset env
------------.profile--------------
git bash窗口关闭重新打开
$ ssh-add -l
2048 SHA256:qH5KQe3UD/3ovY+2aETMcsdvrLR5Or3A /c/Users/Administrator/.ssh/id_rsa (RSA)
2048 SHA256:07ism/CJCHjP0em922YLtJe0/Ejgno /c/Users/Administrator/.ssh/id_rsa_gitlab (RSA)
出现这些则表示ssh key全局添加完成。
```
## [多平台配置后的操作](https://github.com/zhl6522/other/blob/master/GIT%E5%A4%9A%E5%B9%B3%E5%8F%B0%E6%8E%A8%E9%80%81.md)
## 同步平台[CSDN](https://blog.csdn.net/php_ajaxx/article/details/104187117)
