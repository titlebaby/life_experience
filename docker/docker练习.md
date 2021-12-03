### 作业一
```
docker pull nginx #下载
docker images #查看
## 运行
# -d 后台运行
# -name 命名
# -p 宿主机端口：容器内部端口
docker run -d --name nginx_01 -p:3344(公网-外部):80（容器内部） nginx  

## 测试

curl localhost:3344

## 进入容器
docker exec -it nginx_01 /bin/bash # 进入交互模式
```
### 思考问题
1. 每次改动nginx 配置都要进入内部，十分麻烦，可以在外部提供一个映射，即数据卷的技术

### 作业二
```
docker run -it --rm tomcat:9.0

## run是存在即用，不存在即先pull 在用run
## --rm 用完即删除（容器？）（不推荐，用于测试）

## 下载在启动 ？？
docker pull 镜像名

## 启动运行
docker run -d -p 3355:8080 --name tomcat01 tomcat

测试 localhost:3355
## 进入容器
docker exec -ittomcat /bin/bash
# 没有webapps， 进入发现tomcat是简版，很多命令都没有
# 可以把webapps copy进入（15课-狂说）
```

### 作业三
#### 部署es+kibana


#### es 暴露得端口多；十分耗内存；es得数据一般放置比较安全！挂载
#### 查看内存 
```
docker status
```

#### 环境 1核2G是什么概念 ？？？

```
Run Elasticsearch:
docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag

```
#### 测试
``
curl localhost:9200
``

#### 限制内存（es太耗内存了）修改配置文件(-e ES_JAVA_OPTS="-Xms64m -Xmx512m")
```
docker run -d --name elasticsearch02 --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx512m" elasticsearch:7.6.3

```
#### 作业把 kibana链接es
```
### 容器与容器之间是互相隔离得。linux中有一个内网地址，因此容器之间是通过这个linux内网ip，链接
```


### 可视化（管理镜像得工具）（平时不会使用---测试玩玩）
- portainer
- rancher（ci/cd再用）

#### docker图像化界面管理工具，提供一个后台面板，供我们操作

```
docker pull portainer/portainer
# -v挂载数据卷
# --privileged 给权限
docker run -d -p 8088:9000 \ --restart=always -v /var/run/docker.sock:/var/run/docker.sock  --privileged=true  portainer/portainer

#测试
curl localhost:8088
#访问界面，选择本地（local）就可以了
http://ip:8088

```