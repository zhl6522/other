## `mongo整库导入导出命令`
```bash
[root@10-9-29-5 public]# mongodump -h 127.0.0.1 -d relations -o /data/wwwroot/dingzhier/guanxiwang/public
[root@10-9-29-5 public]# mongorestore -h 127.0.0.1:27017 -d relations2 /data/wwwroot/dingzhier/guanxiwang/public/relations
```

win10上MongoDB，[mongoimport失效的解决办法](https://blog.csdn.net/php_ajaxx/article/details/116297238)
```bash
数据集合导出：mongoexport -d relations -c relations -o /tmp/relations.log
数据集合导入：mongoimport -d relations -c relations --file relations.log
```
