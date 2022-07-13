## 常用命令
1. mvn -version 
2. mvn clean 清理项目生产的临时文件，一般是模块下的target目录
3. mvn compile  编译源代码，一般编译模块下的src/main/java目录
4. mvn package 项目打包工具，会在模块下的target目录生成jar或者war等文件
5. mvn test 测试命令，或执行src/test/java下junit的测试用例
6. mvn install 将打包的jar、war文件复制到你的本地仓库中，供其他模块使用
7. mvn deploy 将打包的文件发布到远程仓库，提供其他人人员进行下载一来
8. mvn site 生成项目相关信息网站
9. mvn dependency:tree 打印出醒目的整个依赖树
10. mvn archetype:generate 创建maven的普通git pushjava项目
11. mvn tomcat:run 在tomcat容器中运行web应用
12. mvn jetty:run 调用jetty插件的run目标在jetty serlet容器中启动web应用
13. mvn jetty:run -Djetty.port=9090