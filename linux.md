### 查看日志中关键字
```
查看关键字及其下文200行

grep '关键字' -A 200 文件名 | tail -n 201

 

查看关键字及其上下文200行

grep '关键字' -C 200 文件名 | tail -n 401

eg:
grep -i '/apple-touch-icon-120x120.png' -C 10 app.log  | tail -21

cat app.log | grep "test"
grep -i "test" app.log



```

### 查看日志
```
less /var/log/nginx/laravel-shop-error.log
```

### 直接跳转底部
```shell

shift + g 跳转到日志底部

按 shift + g 跳转到日志底部，再按 ?#0 回车，这个是代表从底部往上搜索 #0 字符串，再按几次 ↑ 按键可以看到真正的报错原因：

```

### 


## nginx

```
## 重启
service php7.4-fpm restart

## 1. 看到是 Nginx 在连接 PHP-FPM 的 sock 文件时出现了 Resource temporarily unavailable 错误，这是因为 PHP-FPM 进程数不足，来不及处理 Nginx 传来的请求导致的。

编辑： /etc/php/7.4/fpm/pool.d/www.conf

pm = static
pm.max_children = 500
pm.max_requests = 1000

备注： pm.max_requests，这个配置代表当一个 PHP-FPM 进程处理了 1000 个请求之后就会主动退出进程，然后再由 FPM 管理进程启动一个新的 PHP-FPM 进程，这样即使有内存泄露发生，这种类似于重启的操作也会将泄露的内存释放掉。


# 检查一下 PHP-FPM 进程数量
ps aux|grep php-fpm|wc -l


##
经查看还是 502，但启动 500 个 PHP-FPM 已经是 4 核 8 G 服务器的极限了，所以我们不再调整。

可以看到我们目前的代码在两台 4 核 8 G 的 Web 服务器极限吞吐量在 580 qps 左右

```


## mysql

```sql

MySQL 报 Too many connections，这是 MySQL 服务器的连接数不足导致的。

mysql -uroot -p

mysql> set global max_connections=1000;
mysql> show variables like 'max_connections';


备注：但是上面的修改只是临时的，只要 MySQL 重启就会变回原来的值，所以我们需要通过修改配置文件来永久性调高最大连接数，编辑 /etc/mysql/mysql.conf.d/mysqld.cnf 文件并找到 max_connections

删除前面的 # 号，然后将值改为 1000。为了让这个值生效，还有另外一个文件需要修改 /lib/systemd/system/mysql.service，在这个文件底部加上两行：
LimitNOFILE=65535
LimitNPROC=65535


然后重启 MySQL：
systemctl daemon-reload
systemctl restart mysql.service
```


