### docker 容器和镜像的区别（images）
1. 使用docker run 镜像名==》运行之后的镜像变成了一个容器？
### 什么事卷，怎么理解卷？
### 列出所有运行得容器
```
docker ps     #当前正在运行得容器

-a            # 当前正在运行的容器 + 带出历史运行过的容器
-n=？         # 显示最近创建的容器

-9            # 只显示容器的编号
```


### 退出容器
```
exit         #直接退出容器并退出
ctrl + P + Q #容器不停止退出
```

### 删除容器
```
docker rm 容器id

docker rm f $(docker ps -aq)  ## 删除所有容器

docker ps -a -q|xargs docker rm   ## 删除所有容器

```

### 启动和停止容器操作

```
docker start 容器id
restart
stop
kill #强制停止容器

```

### docker日志
```
docker log --help
docker log -f -t --tail 容器 
docker log -天府--tail 10 容器id
-tf   #显示日志
--tail number #显示日志是条数 

-是缩写 -- 是全称
-f 跟随日志
```

## 查看docjer中的进程信息
```
docker top 容器id

```

## 查看镜像（容器）的元数据
```
docker inspect -- help
docker inspect  容器的id
```

### 进入当前正在运行的容器

```
docker exec -it 容器id bashShell（=/bin/bash 固定的） #进入容器后，开启一个新的终端

docker attach -- help
docker attach 容器id  #进入容器正在执行的终端，不会启动新的进程

```

### 从容器拷贝文件到主机
```
docker cp 容器id:容器内路径 目的主机路径

docker cp XXXXXXX:/home/test.java /home
```


### 常用命令的小结



