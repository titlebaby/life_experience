## composer
### 1. composer install合composer update的区别
1. composer install 是composer.lock存在即读此文件，不存在则，将在处理完依赖关系后创建它。
2. 为了获取依赖的最新版本，并且更新 composer.lock 文件
3. 更新某个包 composer update XXXX

#### 区别：
 **composer install命令(主要)用于生产环境**，composer.lock文件记录项目当前版本信息，当执行install命令时，会检测lock文件的各扩展版本与最新版本差别，如果有则更新到最新版。
 **而composer update命令也会执行上述所讲**，但是如果在composer.json文件添加库到require字段时，就必须用composer update命令了。但这时会更新其他库的内容，此时如果只是添加某个库而不更新其他库(例如生产环境)，就要使用composer require "包名:版本号" 命令了。composer init --require=包名:版本号 -n 还可以自动更新composer.json文件。
 [博主原文](https://blog.csdn.net/sanbingyutuoniao123/article/details/52025565)

