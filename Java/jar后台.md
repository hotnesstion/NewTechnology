```shell
//后台启动jar
start javaw -jar xx.jar
//根据端口号查询jar包进程PID
netstat -ano | findstr  8080
//根据PID关闭进程
taskkill /pid 1988 /f
```

Windows关闭Java进程

```shell
jps -l
taskkill /pid 1234 /f
```





```shell
java -jar slipper-backstage-2.0.0.jar > D:\cyshop\shop\server.log 2>&1 &
```

这种启动方式，当前命令窗口关闭后则，程序停止



```shell
javaw -Xms128m -Xmx1024m -jar slipper-backstage-2.0.0.jar
javaw -Xms128m -Xmx1024m -jar slipper-backstage-2.0.0.jar > D:\测试jar包\server.log 2>&1 &
```



批处理

```shell
@echo off
start javaw -Xms128m -Xmx1024m -jar slipper-backstage-2.0.0.jar > D:\测试jar包\server.log 2>&1 &
exit
```

把批处理做成自启动

1，Windows+R运行，输入gpedit.msc进入组策略编辑器，选中windows设置-启动，然后点击添加脚本即可。

![image-20230617091843979](https://cdn.jsdelivr.net/gh/hotnesstion/online-pic@main/Typora/202306170918035.png)

![image-20230617091859498](https://cdn.jsdelivr.net/gh/hotnesstion/online-pic@main/Typora/202306170918536.png)