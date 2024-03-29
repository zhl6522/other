## nohup
```bash
nohup go run main.go &
nohup 英文全称 no hang up（不挂起），用于在系统后台不挂断地运行命令，退出终端不会影响程序的运行。
nohup 命令，在默认情况下（非重定向时），会输出一个名叫 nohup.out 的文件到当前目录下，如果当前目录的 nohup.out 文件不可写，输出重定向到 $HOME/nohup.out 文件中。
```
## 文件名+内容  
```bash
grep -r "查询内容"  文件目录
等于：find 文件目录  -type f |xargs grep "查询内容"
```
## Supervisor status
```bash
cd /etc/supervisord.d/
mkdir intreface.molixcx.com
vim interface.queuesql.ini
  ;项目名 
	[program:interface.queuesql]
  ;脚本执行命令
	command=/usr/local/php7/bin/php index.php request_uri="/crontab/index"
	process_name=%(program_name)s
  ;脚本目录
	;directory=/
  ;supervisor启动的时候是否随着同时启动，默认True
	autostart=true
  ;这个选项是子进程启动多少秒之后，此时状态如果是running，则我们认为启动成功了。默认值为1
	startsecs=10
  ;当程序exit的时候，这个program不会自动重启,默认unexpected，设置子进程挂掉后自动重启的情况，有三个选项，false,unexpected和true。如果为false的时候，无论什么情况下，都不会被重新启动，如果为unexpected，只有当进程的退出码不在下面的exitcodes里面定义的
	autorestart=true
  ; 启动失败自动重试次数，默认是3
	startretries=3
  ;脚本运行的用户身份
	user=root
	priority=1
  ;把stderr重定向到stdout，默认 false
	redirect_stderr=true
  ;stdout日志文件大小，默认 50MB
	stdout_logfile_maxbytes=50MB
  ;stdout日志文件备份数
	stdout_logfile_backups=20
  ;日志输出
	stdout_logfile=/var/log/php/asynchronism.log
  ;默认为false,进程被杀死时，是否向这个进程组发送stop信号，包括子进程
	stopasgroup=false
  ;默认为false，向进程组发送kill信号，包括子进程
	killasgroup=false
  
systemctl restart supervisord.service
注意：
  crontab控制器index方法:
   try {
            while (true) {
                。。。代码部分。。。
            }
        } catch (Exception $e) {
            echo $this->ApiResult()->setError($e->getMessage(), $e->getCode());
        } catch(\Exception $e){
            Log::write(LOG_ERR, "\n\n".$e->getMessage() . "\n" . $e->getTraceAsString(), $e->getLine(), $e->getFile());
            echo $this->ApiResult()->setError(Config::module('code.2000'), 2001);
        }catch(\Throwable $e){
            Log::write(LOG_ERR, "\n\n".$e->getMessage() . "\n" . $e->getTraceAsString(), $e->getLine(), $e->getFile());
            echo $this->ApiResult()->setError(Config::module('code.2000'), 2000);
        }
```
