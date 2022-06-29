```
Yaf_Loader::import 导入一个PHP文件, 因为Yaf_Loader::import只是专注于一次包含, 所以要比传统的require_once性能好一些
<?php
//绝对路径
Yaf_Loader::import("/usr/local/foo.php);

//相对路径, 会在APPLICATION_PATH."/library"下加载
Yaf_loader::import("plugins/User.php");
?>
```
```
鸟哥，今天是2018-07-31 执行代码:
date("Y-m-d",strtotime("-1 month"))
怎么输出是2018-07-01?
我们来模拟下date内部的对于这种事情的处理逻辑:
1. 先做-1 month, 那么当前是07-31, 减去一以后就是06-31.
2. 再做日期规范化, 因为6月没有31号, 所以就好像2点60等于3点一样, 6月31就等于了7月1
ar_dump(date("Y-m-d", strtotime("2017-06-31")));
//输出2017-07-01
var_dump(date("Y-m-d", strtotime("-1 month", strtotime("2017-03-31"))));
//输出2017-03-03
var_dump(date("Y-m-d", strtotime("+1 month", strtotime("2017-08-31"))));
//输出2017-10-01
var_dump(date("Y-m-d", strtotime("next month", strtotime("2017-01-31"))));
//输出2017-03-03
var_dump(date("Y-m-d", strtotime("last month", strtotime("2017-03-31"))));
//输出2017-03-03
PHP5.3
从PHP5.3开始呢, date新增了一系列修正短语, 来明确这个问题, 那就是”first day of” 和 “last day of”, 也就是你可以限定好不要让date自动”规范化”:
ar_dump(date("Y-m-d", strtotime("last day of -1 month", strtotime("2017-03-31"))));
//输出2017-02-28
var_dump(date("Y-m-d", strtotime("first day of +1 month", strtotime("2017-08-31"))));
////输出2017-09-01
var_dump(date("Y-m-d", strtotime("first day of next month", strtotime("2017-01-31"))));
////输出2017-02-01
var_dump(date("Y-m-d", strtotime("last day of last month", strtotime("2017-03-31"))));
////输出2017-02-28
```
```
utf8一个字符最多3字节，只支持BMP这部分的unicode编码区;而utf8mb4则扩展到一个字符最多能有4字节，所以能支持更多的字符集。
```
```
offsetSet — 为指定索引设定新的值（$res为对象数组）
foreach ($res as $k => $v) {
	$v['my_status'] = in_array($v['uniacid'], $uniacidStatusList)?'1':'0';
	$res->offsetSet($k, $v);
}
```
[TP队列](https://github.com/coolseven/notes/blob/master/thinkphp-queue/README.md)

$a = [['id'=> 1, 'name' => 'php', 'type' => 'textatea'],[...][...]];
$b = [['id'=> 1, 'name' => 'golang'],[...][...]];
foreach($a as &item) {
	...
}
foreach($b as $item) {
	...
}
return ['a' => $a, 'b' => $b];	//$a的数据会出问题
[php的传址调用](https://blog.csdn.net/weixin_33711795/article/details/115173586)

```
//todo
```
