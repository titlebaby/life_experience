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
