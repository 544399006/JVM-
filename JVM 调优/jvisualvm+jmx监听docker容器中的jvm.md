# jvisualvm+jmx监听docker容器中的jvm

## 1. dockerfile  文件
```shell
FROM xxx.xxx.xxx.xxx:5000/oracle_jdk8_alpine

MAINTAINER xxx xxxxxx@foxmail.com
 
ADD *.jar app.jar
 
ENTRYPOINT java ${JVM_OPTS} -jar /app.jar
```



## 2. 添加 JVM 参数  及  映射端口

```shell
-Dcom.sun.management.jmxremote 
-Dcom.sun.management.jmxremote.local.only=false 
-Dcom.sun.management.jmxremote.authenticate=false 
//端口可自己定义
-Dcom.sun.management.jmxremote.port=19999 
-Dcom.sun.management.jmxremote.rmi.port=19999 
//此IP为宿主机的IP
-Djava.rmi.server.hostname=xxx.xxx.2.140 
-Dcom.sun.management.jmxremote.ssl=false
```

* rancher 环境变量配置

![](.\imgs\环境变量.png)



* rancher 端口映射配置

![](.\imgs\端口映射.png)



## 3. 启动jvisualvm 连接 JVM 

注：jvisualvm 路径：D:\java\jdk1.8\jdk1.8.0_92\bin    这是我本机jdk路径  你们找到自己的jdk路径打开即可

![](E:\学习\JVM 调优\JVM 调优\imgs\jvisualvm应用路径.png)

* 连接步骤：

步骤一

![](E:\学习\JVM 调优\JVM 调优\imgs\jvisualvm-1.png)



步骤二

![](E:\学习\JVM 调优\JVM 调优\imgs\jvisualvm-2.png)

步骤三

![](E:\学习\JVM 调优\JVM 调优\imgs\jvisualvm-3.png)

步骤四

![](E:\学习\JVM 调优\JVM 调优\imgs\jvisualvm-4.png)