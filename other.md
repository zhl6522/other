```bash
Photoupz	图片去除水印软件
```
```bash
windows 原有基础上生成多个ssh key
https://blog.csdn.net/php_ajaxx/article/details/104187117

nginx重启前检测命令：
/usr/local/nginx/sbin/nginx -t
/usr/local/nginx/sbin/nginx -s reload
```
```bash
将redis加入到windows的服务中（service和loglevel前都是两个-）开机自启动
redis-server --service-install redis.windows-service.conf --loglevel verbose
然后在从服务中吧redis设置成自动(延迟启动)
```
```bash
composer安装laravel/laravel-admin
因为我之前电脑上有老版本的composer 在命令行更新composer的时候每次都会提醒"版本比较老，需要访问一个地址" 我忽略了这个消息，后面更新完composer之后<通过使用 Composer 安装 Laravel 安装器>或者下一步<composer create-project laravel/laravel>的时候会报错：内存溢出。修改php配置信息：memory_limit = -1 再次运行，如果还是不可以 建议控制面板->程序和功能 找到composer卸载 重新安装就可以了（安装composer的时候有一个 proxy settings不要配置）
```
```bash
PHP：7.2.31
Dolphinphp：V1.5.0（ThinkPHP5.1.41LTS）
MongoDB SERVER V4.4.4
MongoDB（win.dll插件）：1.8.1
出现的问题：BSON field 'count.query' is the wrong type 'array', expected type 'object'
故障原因在think-mongo版本，vendor/topthink/think-mongo/src/Builder.php文件中，parseWhere方法在做过滤条件初始化的时候，没有考虑周全，将数据类型定义为了数组。这里在返回的时候做一个判断，如果$filter为空，就重新定义为stdClass对象。可以参考以下代码:
	public function parseWhere(Query $query, $where)
    {
        if (empty($where)) {
            $where = [];
        }

        $filter = [];
        foreach ($where as $logic => $val) {
            foreach ($val as $field => $value) {
                if (is_array($value)) {
                    if (key($value) !== 0) {
                        throw new Exception('where express error:' . var_export($value, true));
                    }
                    $field = array_shift($value);
                } elseif (!($value instanceof \Closure)) {
                    throw new Exception('where express error:' . var_export($value, true));
                }

                if ($value instanceof \Closure) {
                    // 使用闭包查询
                    $query = new Query($this->connection);
                    call_user_func_array($value, [ & $query]);
                    $filter[$logic][] = $this->parseWhere($query, $query->getOptions('where'));
                } else {
                    if (strpos($field, '|')) {
                        // 不同字段使用相同查询条件（OR）
                        $array = explode('|', $field);
                        foreach ($array as $k) {
                            $filter['$or'][] = $this->parseWhereItem($query, $k, $value);
                        }
                    } elseif (strpos($field, '&')) {
                        // 不同字段使用相同查询条件（AND）
                        $array = explode('&', $field);
                        foreach ($array as $k) {
                            $filter['$and'][] = $this->parseWhereItem($query, $k, $value);
                        }
                    } else {
                        // 对字段使用表达式查询
                        $field            = is_string($field) ? $field : '';
                        $filter[$logic][] = $this->parseWhereItem($query, $field, $value);
                    }
                }
            }
        }

        $options = $query->getOptions();
        if (!empty($options['soft_delete'])) {
            // 附加软删除条件
            list($field, $condition) = $options['soft_delete'];
            $filter['$and'][]        = $this->parseWhereItem($query, $field, $condition);
        }
        if (empty($filter)){ // 返回空对象
            return new \stdClass;
        }

        return $filter;
    }
-----
海豚+mongo 模糊查询
$regex = new \MongoDB\BSON\Regex($content,'i');
```
```bash
Win Google浏览器快捷键
Ctrl+W		关闭当前标签页
Ctrl+Shift+T	重新打开上次关闭的标签页。 谷歌浏览器可记住您关闭的最后 10 个标签页。
```
```bash
蓝灯翻墙软件：http://lanter.clbug.com/ 下载地址：http://pan.clbug.com/?dir=lan
蓝灯有时候也会别墙，经测试如果打不开蓝灯就退出，不然可能影响上网
```
