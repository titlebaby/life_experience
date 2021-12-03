### commit 镜像
```
docker commit -a='作者' -m '提交描述' 容器id 目标镜像名:[tag]
## 实战
1.启用一个默认得tomcat

2.发现默认得tomcat是没有webapps目录，制作一个有de

3. copy目录

4. 将操作过的的容器通过commit提交为一个镜像

## 执行过程
docker pull tomcat
docker run -it -p 8080:8080 tomcat( 启动是一个前台应用)
docker exec -it 容器id /bin/bash （进入容器）
cd webapps 
ll # 没有数据
cd ..
cp -r webapps.dist/* webapps

docker commit -a='lyl' -m '有webapps的tomcat' 容器id tomcat02:1.0

docker images （可见新镜像）

##发布之后，别人可用

## -i -t ==》-it 
加-it 后docker命令会为容器分配一个伪终端，并接管其stdin/stdout支持交互操作，这时候bash命令不会自动退出。

```