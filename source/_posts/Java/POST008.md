---
title: Java成神之路-Tomcat（八）
tags: Java
category: Java
date: 2018-02-23 16:44:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0133.jpg)

Java成神之路-Tomcat
<!--more-->
# tomcat服务

## tomcat的内存设置

Tomcat的启动分为startupo.bat启动和注册为windows服务的启动，下面一一说明。

### startup.bat启动

在tomcat_home/bin目录下找到catalina.bat，用文本编辑器打开，加上下面一行：

```
set JAVA_OPTS= -Xms1024M -Xmx1024M -XX:PermSize=256M -XX:MaxNewSize=256M -XX:MaxPermSize=256M
```

解释一下各个参数：

* -Xms1024M：初始化堆内存大小（注意，不加M的话单位是KB）
* -Xmx1029M：最大堆内存大小
* -XX:PermSize=256M：初始化类加载内存池大小
* -XX:MaxPermSize=256M：最大类加载内存池大小
* -XX:MaxNewSize=256M：这个还不清楚哈，有知道的说声

还有一个-server参数，是指启动jvm时以服务器方式启动，比客户端启动慢，但性能较好，大家可以自己选择。

### windows服务启动

​       如果你的tomcat是注册为windows服务并且是以服务方式启动的，那么上面的方法就无效了，因为这时tomcat启动是读取注册表的参数，而不是读取批处理文件的参数，这时我们有两种方法来设置jvm参数。

1. 第一种比较简单，tomcat为我们提供了一个设置启动参数的窗体，双击tomcat_home/bin目录下的tomcat6w.exe，如图

![Tomcat启动内存设置 - 一个人失眠 - 渴望](http://img853.ph.126.net/19ez1FAxdrVVLOWe75iqjQ==/613615449230442622.jpg)

下方的Initial memory pool就是初始化堆内存大小，Maximun memory pool是最大堆内存大小。

而要设置Perm Gen池的大小就要在Java Option里面加参数了，在里面加上：

* -Dcatalina.base=%tomcat_home%
* -Dcatalina.home=%tomcat_home%
* -Djava.endorsed.dirs=%tomcat_home%\endorsed
* -Djava.io.tmpdir=%tomcat_home%\temp
* -XX:PermSize=256M
* -XX:MaxPermSize=256M
* -XX:ReservedCodeCacheSize=48M
* -Duser.timezone=GMT+08

（PS：网上说每一行后面不要有空格，没试过）

2. 第二种方法是打开注册表->HKEY_LOCAL_MACHINE\SOFTWARE\Apache Software Foundation\Procrun 2.0\Tomcat6\Parameters\Java(路径可能有一点点差别)

![Tomcat启动内存设置 - 一个人失眠 - 渴望](http://img242.ph.126.net/wR1s2msgkQSskIdzeV-hDw==/1430737306621990743.png)

修改Options的值，把刚才上面那些参数加进去就OK了。（别忘了先备份一下注册表）

## 修改tomcat端口

### 默认情况下

tomcat的端口是8080，如果出现8080端口号冲突，用如下方法可以修改Tomcat的端口号：

在C:/Tomcat/conf/Server.xml文件中找到如下文本：

```xml
<Connector port="8080" protocol="HTTP/1.1" 
               maxThreads="150" connectionTimeout="20000" 
               redirectPort="8443" />
```

也有可能是这样的：

```xml
<Connector port="8080" maxThreads="150" minSpareThreads="25" maxSpareThreads="75" enableLookups="false" redirectPort="8443" acceptCount="100" debug="0" connectionTimeout="20000" disableUploadTimeout="true" />
```

等等；

最后：将port="8080"改为如port="8081"等，保存server.xml，重启Tomcat，Tomcat就可以使用8081端口。

### 使用两个tomcat

修改了上面的以后，还要修改两处：

1. 将 

```xml
<Connector port="8009" enableLookups="false" redirectPort="8443" debug="0"
protocol="AJP/1.3" />
```

的8009改为其它的端口。

2. 将

```xml
<Server port="8005" shutdown="SHUTDOWN" debug="0">
```

的8005改为其它的端口。
修改以上三处。

## tomcat改名

1. 找到tomcat下面的这个文件：tomcat_home\bin\catalina.bat 

2. 搜索到：

   ```xml
   :doStart  
   shift  
   if not "%OS%" == "Windows_NT" goto noTitle  
   set EXECJAVA=start "Tomcat" %RUNJAVA%  
   goto gotTitle 
   ```

   将"Tomcat"修改成想替换的名称即可

3. 在tomcat6.0.29以后的版本则如下： 

```xml
:doStart  
shift  
if not "%OS%" == "Windows_NT" goto noTitle  
if "%TITLE%" == "" set TITLE=Tomcat  
set _EXECJAVA=start "%TITLE%" %_RUNJAVA%  
goto gotTitle 
```

同理将 

```
if "%TITLE%" == "" set TITLE=Tomcat 
```

改为： 

```
if "%TITLE%" == "" set TITLE=你的应用服务名
```
