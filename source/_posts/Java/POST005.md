---
title: Java成神之路-JavaSE（四）
tags: Java
category: Java
date: 2018-02-23 13:44:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0130.jpg)

Java成神之路-JavaSE
<!--more-->
# java简介

## 1.java是什么？

java是一种高级的面向对象的程序设计语言 。

## 2.JVM

Java Virtual Machine，是java程序跨平台的关键，不同的平台有不同的JVM，而java字节码不包含任何与平台相关的信息，不直接与平台交互，而是通过JVM间接与平台交互。应用程序在执行时，JVM加载字节码，将字节码解释成特定平台的机器码，让平台执行。

任何一个应用程序都必须转化为机器码，才能与计算机进行交互，如果机器码的来源依赖于具体的平台，那么这个应用程序就不能跨平台。而java应用程序运行时机器码由java体系的一部分JVM提供，不受平台的限制，所以实现了跨平台。

## 3.java程序运行过程

程序员编写的源码经编译器编译转化为字节码，字节码被加载到JVM，由JVM解释成机器码在计算机上运行。

![img](https://images2015.cnblogs.com/blog/1173487/201707/1173487-20170714174029322-511011418.png)

## 4.java版本

针对不同的用途，java分为3个版本：

1. Java SE：java的标准版，是其他版本的基础，主要用于开发桌面应用程序。
2. Java EE：java的企业版，主要用于开发企业级分布式网络程序。
3. Java ME：主要用于嵌入式系统开发。

## 5.JDK

Java Develop Kits，使用java语言开发应用程序必备的工具包，主要包含包括了编译器、JVM、Java基础API等。

## 6.JRE

Java Run Environment，java运行所依赖的环境，包括JVM以及java基础API。

## 7.API

Application Programming Interface，应用程序编程接口，是使用java语言编写应用程序的入口，包含源码、字节码帮助文档三部分。应用程序由一系列方法构成，方法有哪些要求？什么样的方法是编程语言接受的？API提供了一些基础的方法，程序员要实现某项功能必须遵循java语言规范，调用这些方法编写更高级的方法。

## 8.java特性

1. 简单：java语言是从C++发展起来的，取消了C++中复杂难以掌握的部分，如指针。
2. 面向对象：java语言的基础。java将一切问题都看做对象与对象之间的交互，将对象抽象成方法与属性的集合。
3. 分布性：包含操作分布性与数据分布性两个方面。操作分布性是指由多个主机共同完成一项功能，数据分布性是分布在多台主机上的数据当做一个完成的整体处理。
4. 跨平台：java语言编写的应用程序，不受平台限制，可以由一种平台迁移到另一种平台。
5. 解释型：使用java语言编写的源码被转化为字节码，字节码只有被JVM解释成机器码才能被计算机执行。
6. 安全性：java语言的底层设计可以有效避免非法操作。
7. 健壮性：java提供了许多机制防止运行时出现严重错误，如编译时类型检查、异常处理。
8. 多线程：java支持多线程，允许进程内部多个线程同时工作。

# window系统安装java

## 下载JDK

首先我们需要下载java开发工具包JDK，下载地址：<http://www.oracle.com/technetwork/java/javase/downloads/index.html>，点击如下下载按钮：

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-download.jpg)

在下载页面中你需要选择接受许可，并根据自己的系统选择对应的版本，本文以 Window 64位系统为例：

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-download-1.jpg)

下载后JDK的安装根据提示进行，还有安装JDK的时候也会安装JRE，一并安装就可以了。

安装JDK，安装过程中可以自定义安装目录等信息，例如我们选择安装目录为 **C:\Program Files (x86)\Java\jdk1.8.0_91**。

## 配置环境变量

1.安装完成后，右击"我的电脑"，点击"属性"，选择"高级系统设置"；

![img](http://www.runoob.com/wp-content/uploads/2013/12/win-java1.png)

2.选择"高级"选项卡，点击"环境变量"；

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win2.png)

然后就会出现如下图所示的画面：

在"系统变量"中设置3项属性，JAVA_HOME,PATH,CLASSPATH(大小写无所谓),若已存在则点击"编辑"，不存在则点击"新建"。

变量设置参数如下：

- 变量名：**JAVA_HOME**
- 变量值：**C:\Program Files (x86)\Java\jdk1.8.0_91**        // 要根据自己的实际路径配置


- 变量名：**CLASSPATH**
- 变量值：**.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;**         //记得前面有个"."


- 变量名：**Path**
- 变量值：**%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;**

> **注意：**在 Windows10 中，因为系统的限制，path 变量只可以使用 JDK 的绝对路径。%JAVA_HOME% 会无法识别，导致配置失败。如下所示：
>
> ```
> C:\Program Files (x86)\Java\jdk1.8.0_91\bin;C:\Program Files (x86)\Java\jdk1.8.0_91\jre\bin;
> ```

### JAVA_HOME 设置

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win4.png)

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win5.png)

### PATH设置

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win6.png)

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win7.png)

### CLASSPATH 设置

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win8.png)

这是 Java 的环境配置，配置完成后，你可以启动 Eclipse 来编写代码，它会自动完成java环境的配置。

> **注意：**如果使用1.5以上版本的JDK，不用设置CLASSPATH环境变量，也可以正常编译和运行Java程序。

### 测试JDK是否安装成功

1、"开始"->"运行"，键入"cmd"；

2、键入命令: **java -version**、**java**、**javac** 几个命令，出现以下信息，说明环境变量配置成功；

![img](http://www.runoob.com/wp-content/uploads/2013/12/java-win9.png)

------

## Linux，UNIX，Solaris，FreeBSD环境变量设置

环境变量PATH应该设定为指向Java二进制文件安装的位置。如果设置遇到困难，请参考shell文档。

例如，假设你使用bash作为shell，你可以把下面的内容添加到你的 .bashrc文件结尾: export PATH=/path/to/java:$PATH

------

## 流行JAVA开发工具

正所谓工欲善其事必先利其器，我们在开发java语言过程中同样需要依款不错的开发工具，目前市场上的IDE很多，本文为大家推荐以下下几款java开发工具：

- **Eclipse（推荐）:**另一个免费开源的java IDE，下载地址： <http://www.eclipse.org/>

  选择 **Eclipse IDE for Java Developers**：
  ![img](http://www.runoob.com/wp-content/uploads/2013/12/5A92DEAE-EFB9-493D-AC4D-808E529B533C.jpg)

- **Notepad++ : **Notepad++ 是在微软视窗环境之下的一个免费的代码编辑器，下载地址：[ http://notepad-plus-plus.org/](http://notepad-plus-plus.org/)

- **Netbeans:**开源免费的java IDE，下载地址： <http://www.netbeans.org/index.html>

------

## 使用 Eclipse 运行第一个 Java 程序

视频演示如下所示：

HelloWorld.java 文件代码：

```java
public class HelloWorld {    
	public static void main(String []args) {        
	System.out.println("Hello World");    
}}
```

# Java基本语言元素

## 规则

1. 命名规则 

- 类名称：首字母大写，尽可能采取驼峰式命名:MaLin HelloWorld 
- 命名标识符规范：数字、字母、下划线、$组成，但是不能以数字开头，不能是关键字或者保留字。
- 变量名称 ：首字母必须小写          常量：必须全大些 PI MAX 
- 方法名称：首字母必须小写 

2. 严格区分大小写 
3. 以分号 ‘;’ 结束

## 数据类型

### 基本数据类型（四类八种） 

1. **简单类型** 

* 第一类：整型 byte short int long
* 第二类：浮点型 float double
* 第三类：逻辑型 boolean(它只有两个值可取true false)
* 第四类：字符型 char

2. **封装类型**（数据类型转换简单类型） 

`Byte Short Integer Long Float Double Character Boolean` 

- 基本类型只能按值传递，而每个基本类型对应的封装类是按引用传递的。 
- 从性能上说java中的基本类型是在堆栈上创建的，而所有的对象类型都是在堆上创建的，（对象的引用在堆栈上创建） 

3. 引用类型

数组、 类（对象）、接口



说明： 

​       导包快捷键 ctrl+shift+o

## 变量、常量

**1. 语法**： 
数据类型 变量名称 [= 值];

```
char sex; //声明变量
        sex = '男';//初始化、赋值 
        int age = 10; 
        float score = 93.2F; 
        int x,y,z=20;
```

final 数据类型 变量名称 [= 值]; final int X=1; 
先声明 、初始化 、使用

**2. 类型之间的转换：** 
2.1小——>大：自动类型转换

```
short  y = 1;
System.out.println(y);
double x =  y;
```

System.out.println(x);—>小： 强制类型转换

```
at score = 13;//13(int)-->小，到
         System.out.println(score);
         int rs = (int)score; // 0.3截取丢失
         System.out.println(rs);
```



## 字符串类型

String在java.lang.String 
**1. 必须掌握： = = 、 equals() 字符串比较差别**：

**2. 熟练进行 简单类型字符串类型** 
String.valueOf(参数) 任意类型+”” 
字符串简单类型（封装类型：parseXxx()）

```
public class Test2 {
    public static void main(String[] args) {
        float num = 3.1f;
        String str = String.valueOf(num);
        System.out.println(str);//3.1(String)
        num =  Float.parseFloat(str) ;
    }
}
```

**3. 掌握：String类中常用功能** 


| SN(序号) | 方法描述                                                     |
| -------- | ------------------------------------------------------------ |
| 1        | [char charAt(int index)](http://www.runoob.com/java/java-string-charat.html)返回指定索引处的 char 值。 |
| 2        | [int compareTo(Object o)](http://www.runoob.com/java/java-string-compareto.html)把这个字符串和另一个对象比较。 |
| 3        | [int compareTo(String anotherString)](http://www.runoob.com/java/java-string-compareto.html)按字典顺序比较两个字符串。 |
| 4        | [int compareToIgnoreCase(String str)](http://www.runoob.com/java/java-string-comparetoignorecase.html)按字典顺序比较两个字符串，不考虑大小写。 |
| 5        | [String concat(String str)](http://www.runoob.com/java/java-string-concat.html)将指定字符串连接到此字符串的结尾。 |
| 6        | [boolean contentEquals(StringBuffer sb)](http://www.runoob.com/java/java-string-contentequals.html)当且仅当字符串与指定的StringButter有相同顺序的字符时候返回真。 |
| 7        | [static String copyValueOf(char[\] data)](http://www.runoob.com/java/java-string-copyvalueof.html)返回指定数组中表示该字符序列的 String。 |
| 8        | [static String copyValueOf(char[\] data, int offset, int count)](http://www.runoob.com/java/java-string-copyvalueof.html)返回指定数组中表示该字符序列的 String。 |
| 9        | [boolean endsWith(String suffix)](http://www.runoob.com/java/java-string-endswith.html)测试此字符串是否以指定的后缀结束。 |
| 10       | [boolean equals(Object anObject)](http://www.runoob.com/java/java-string-equals.html)将此字符串与指定的对象比较。 |
| 11       | [boolean equalsIgnoreCase(String anotherString)](http://www.runoob.com/java/java-string-equalsignorecase.html)将此 String 与另一个 String 比较，不考虑大小写。 |
| 12       | [byte[\] getBytes()](http://www.runoob.com/java/java-string-getbytes.html) 使用平台的默认字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中。 |
| 13       | [byte[\] getBytes(String charsetName)](http://www.runoob.com/java/java-string-getbytes.html)使用指定的字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中。 |
| 14       | [void getChars(int srcBegin, int srcEnd, char[\] dst, int dstBegin)](http://www.runoob.com/java/java-string-getchars.html)将字符从此字符串复制到目标字符数组。 |
| 15       | [int hashCode()](http://www.runoob.com/java/java-string-hashcode.html)返回此字符串的哈希码。 |
| 16       | [int indexOf(int ch)](http://www.runoob.com/java/java-string-indexof.html)返回指定字符在此字符串中第一次出现处的索引。 |
| 17       | [int indexOf(int ch, int fromIndex)](http://www.runoob.com/java/java-string-indexof.html)返回在此字符串中第一次出现指定字符处的索引，从指定的索引开始搜索。 |
| 18       | [int indexOf(String str)](http://www.runoob.com/java/java-string-indexof.html) 返回指定子字符串在此字符串中第一次出现处的索引。 |
| 19       | [int indexOf(String str, int fromIndex)](http://www.runoob.com/java/java-string-indexof.html)返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始。 |
| 20       | [String intern()](http://www.runoob.com/java/java-string-intern.html) 返回字符串对象的规范化表示形式。 |
| 21       | [int lastIndexOf(int ch)](http://www.runoob.com/java/java-string-lastindexof.html) 返回指定字符在此字符串中最后一次出现处的索引。 |
| 22       | [int lastIndexOf(int ch, int fromIndex)](http://www.runoob.com/java/java-string-lastindexof.html)返回指定字符在此字符串中最后一次出现处的索引，从指定的索引处开始进行反向搜索。 |
| 23       | [int lastIndexOf(String str)](http://www.runoob.com/java/java-string-lastindexof.html)返回指定子字符串在此字符串中最右边出现处的索引。 |
| 24       | [int lastIndexOf(String str, int fromIndex)](http://www.runoob.com/java/java-string-lastindexof.html) 返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索。 |
| 25       | [int length()](http://www.runoob.com/java/java-string-length.html)返回此字符串的长度。 |
| 26       | [boolean matches(String regex)](http://www.runoob.com/java/java-string-matches.html)告知此字符串是否匹配给定的正则表达式。 |
| 27       | [boolean regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)](http://www.runoob.com/java/java-string-regionmatches.html)测试两个字符串区域是否相等。 |
| 28       | [boolean regionMatches(int toffset, String other, int ooffset, int len)](http://www.runoob.com/java/java-string-regionmatches.html)测试两个字符串区域是否相等。 |
| 29       | [String replace(char oldChar, char newChar)](http://www.runoob.com/java/java-string-replace.html)返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。 |
| 30       | [String replaceAll(String regex, String replacement](http://www.runoob.com/java/java-string-replaceall.html)使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。 |
| 31       | [String replaceFirst(String regex, String replacement)](http://www.runoob.com/java/java-string-replacefirst.html) 使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。 |
| 32       | [String[\] split(String regex)](http://www.runoob.com/java/java-string-split.html)根据给定正则表达式的匹配拆分此字符串。 |
| 33       | [String[\] split(String regex, int limit)](http://www.runoob.com/java/java-string-split.html)根据匹配给定的正则表达式来拆分此字符串。 |
| 34       | [boolean startsWith(String prefix)](http://www.runoob.com/java/java-string-startswith.html)测试此字符串是否以指定的前缀开始。 |
| 35       | [boolean startsWith(String prefix, int toffset)](http://www.runoob.com/java/java-string-startswith.html)测试此字符串从指定索引开始的子字符串是否以指定前缀开始。 |
| 36       | [CharSequence subSequence(int beginIndex, int endIndex)](http://www.runoob.com/java/java-string-subsequence.html) 返回一个新的字符序列，它是此序列的一个子序列。 |
| 37       | [String substring(int beginIndex)](http://www.runoob.com/java/java-string-substring.html)返回一个新的字符串，它是此字符串的一个子字符串。 |
| 38       | [String substring(int beginIndex, int endIndex)](http://www.runoob.com/java/java-string-substring.html)返回一个新字符串，它是此字符串的一个子字符串。 |
| 39       | [char[\] toCharArray()](http://www.runoob.com/java/java-string-tochararray.html)将此字符串转换为一个新的字符数组。 |
| 40       | [String toLowerCase()](http://www.runoob.com/java/java-string-tolowercase.html)使用默认语言环境的规则将此 String 中的所有字符都转换为小写。 |
| 41       | [String toLowerCase(Locale locale)](http://www.runoob.com/java/java-string-tolowercase.html) 使用给定 Locale 的规则将此 String 中的所有字符都转换为小写。 |
| 42       | [String toString()](http://www.runoob.com/java/java-string-tostring.html) 返回此对象本身（它已经是一个字符串！）。 |
| 43       | [String toUpperCase()](http://www.runoob.com/java/java-string-touppercase.html)使用默认语言环境的规则将此 String 中的所有字符都转换为大写。 |
| 44       | [String toUpperCase(Locale locale)](http://www.runoob.com/java/java-string-touppercase.html)使用给定 Locale 的规则将此 String 中的所有字符都转换为大写。 |
| 45       | [String trim()](http://www.runoob.com/java/java-string-trim.html)返回字符串的副本，忽略前导空白和尾部空白。 |
| 46       | [static String valueOf(primitive data type x)](http://www.runoob.com/java/java-string-valueof.html)返回给定data type类型x参数的字符串表示形式。 					|

频繁的操作字符串：不建议使用String类，而是使用StringBuilder & StringBuffer

## 运算符

**1. 算术运算符** 
双目： * / %(取余、求模) + - 
单目： ++ – 
a 前缀（num++;）

```
int num = 4;
        ++num;
        int rs = ++num*2;
        System.out.println(rs);//?
```

b 后缀

```
int num = 4;
        int x = 3;
        num++;//5
        int rs = num++ +x; //rs = 8  num=6
        System.out.println(rs++);//?
        System.out.println(rs);
```

**2. 关系运算符**：true/false

> < >= <= ==(恒等于) != 
> 逻辑运算符：true/false 
> ！（取反） &&（短路且） ||（短路或）

```
int x=3,y=4,z=10;
boolean rs = x>y&&++z>10;// true / false
System.out.println(z);
```

算符 = 
**3. 赋值运算符** 
赋值运算符： = 
复合赋值运算符： += -= *= /= %=

```
int x = 5;
//      x = x + 10;
        x+=10;
        System.out.println(x);
```

**4. 三目运算符**： 
exp1 ? exp2 : exp3; 
exp1:true exp2; 
exp1:false exp3; 
**5. 位运算符**： 
~ 非 |或 &与 ^异或 
按位~运算符：10100101=01011010 
按位&运算符：1101&1010=1000 
按位|运算符： 1101 | 1010= 1111 
按位异或运算符：1101 ^ 1010 = 0111 
**6. 位移运算符** 
<< 3<<3=24 >> 
在数字没有溢出的前提下，对于正数和负数，左移一位都相当于乘以2的1次方，左移n位就相当于乘以2的n次方 
**7. 转义字符**： 

```
\n 换行 
\r 回车 
\t 水平制表 
\v 垂直 制表 
\” “ 
\’ ‘ 
\ \
```

# Java流程控制

## 介绍

Java流程控制包括**顺序控制、条件控制和循环控制**。

* 顺序控制，就是从头到尾依次执行每条语句操作。
* 条件控制，基于条件选择执行语句，比方说，如果条件成立，则执行操作A，或者如果条件成立，则执行操作A，反之则执行操作B。
* 循环控制，又称为回路控制，根据循环初始条件和终结要求，执行循环体内的操作。
* 分支结构:  顺序结构只能顺序执行，不能进行判断和选择，因此需要分支结构。

Java有两种分支结构：

- if语句

- switch语句

Java中有三种主要的循环结构：

- while循环

- do…while循环

- for循环

## 笔记

```java
package com.hgd.study2;

import java.util.Scanner;

/**
 * java的流程控制：顺序结构 分之机构 循环结构
 * 
 * @author HuTiger 顺序结构：通过debug模式可以看出java程序的运行时顺序结构的
 * 
 *         分支结构：if语句
 *
 */
public class ProcessControl {

    public static void main(String[] args) {
        // IfStudy();
        // SwitchCaseStudy();
        // WhileStudy();
    }

    /*
     * IF语句
     */
    private static void IfStudy() {

        /*
         * 根据条件表达的世界(true||false)来判断是否进入语句块 if(条件表达式){ 语句块 } 继续执行后面的语句
         */
        int i = 100;
        if (i > 60) {
            System.out.println(i);
        }
        System.out.println("后面需要执行的语句");

        /*
         * if else 语句
         */

        // system.in就是标准输入，可以获取从键盘输入的值
        // 通过scanner(jdk提供给我们的工具)来处理获取到的数据
        System.out.println("请输入分数!");
        Scanner sc = new Scanner(System.in);

        int j = sc.nextInt();// 把用户输入的数赋值给j
        System.out.println("控制台获取到的值是：" + j);

        if (j > 60) {
            System.out.println("通过");
        } else {
            System.out.println("没通过");
        }
        System.out.println("当if else 执行后需要执行的内容");

        /*
         * if else if else if ...else
         */
        // 场景：将一个5(score)分制分为 :5分的评价等级A 4==B 3==C 其他是D
        Scanner sca = new Scanner(System.in);
        int score = sca.nextInt();
        if (score >= 0 && score <= 5) {
            if (score == 5) {
                System.out.println("A");
            } else if (score == 4) {
                System.out.println("B");
            } else if (score == 3) {
                System.out.println("C");
            } else {
                System.out.println("D");
            }
        } else {
            System.out.println("输入不合法");
        }

        /*
         * 练习：百分制系统 90-100 优秀 75-89 良好 60-74 合格 其他 不合格
         */
        Scanner scan = new Scanner(System.in);
        int score1 = scan.nextInt();
        if (score1 >= 0 && score1 <= 100) {
            if (score1 >= 90 && score1 <= 100) {
                System.out.println("优秀");
            } else if (score1 >= 75) {
                System.out.println("良好");
            } else if (score1 >= 60) {
                System.out.println("合格");
            } else {
                System.out.println("不合格");
            }
        } else {
            System.out.println("输入不合法");
        }

    }

    /*
     * switch case
     */
    private static void SwitchCaseStudy() {

        /*
         * 分支语句：switch case key：需要比较的表达式 value：与表达式进行比较的值
         * 执行流程：如果key和value比较的结果为true，那么将执行case部分的代码，case部分可以有多个 类似于else if 部分
         * 区别是key和value之间的比较只能是== default部分是不满足以上任何去执行的代码 ，类似于else
         * 
         * switch 后面括号中的表达式的值必须是符合byte，char，short，int类型的常量表达式 jdk1.7以后可以使用string
         * ，而不能用浮点型或long类型
         * 
         * switch(key) { case value: break; default: break; }
         */

        // 场景：将一个5(score)分制分为 :5分的评价等级A 4==B 3==C 其他是D
        Scanner sc = new Scanner(System.in);
        int score = sc.nextInt();
        switch (score) {
        case 5:
            System.out.println("A");
            break;// 标准写法 break不能少 跳出当前语句块，如果没有break会直接进入下一个case语句
        case 4:
            System.out.println("B");
            break;
        case 3:
            System.out.println("C");
            break;
        default:
            System.out.println("D");
            break;
        }
    }

    /*
     * while 循环和do while
     */
    private static void WhileStudy() {

        /*
         * 执行流程： 当条件表达式为true的时候进入代码块，执行需要执行的代码 当条件表达式为false的时候执行后面的语句
         * 
         * while(条件表达式){ 需要执行的代码部分 } 后面的语句
         */

        /*
         * 场景：输入1-100的整数分析：给输出的值一个变量I，当i在1-100之间的时候输出
         */
        int i = 1;// 循环的起点
        while (i <= 100) {
            System.out.println(i);
            // 给出循环的步长
            i++;
        }
        System.out.println("打印结束");
        
        
        /*
         * do while
         * 
         * do{
         * }while(条件表达式)
         */
        
        int a=1;
        do{//语句块中的内容无论条件是否满足都会先执行一次
            System.out.println(a);
            a++;
        }
        while(a<=0);
        
    }

    /*
     * for循环
     */
    private static void ForStudy() {

        /*
         * 场景：打印1-100 int i=1是循环的起点 i++ 循环的补偿 i<=100 循环的条件
         */
        for (int i = 1; i <= 100; i++) {
            System.out.println(i);
        }
        System.out.println("打印结束");
    }
}
```

# Java 数组

数组对于每一门编程语言来说都是重要的数据结构之一，当然不同语言对数组的实现及处理也不尽相同。

Java 语言中提供的数组是用来存储固定大小的同类型元素。

你可以声明一个数组变量，如 numbers[100] 来代替直接声明 100 个独立变量 number0，number1，....，number99。

本教程将为大家介绍 Java 数组的声明、创建和初始化，并给出其对应的代码。

------

## 声明数组变量

首先必须声明数组变量，才能在程序中使用数组。下面是声明数组变量的语法：

dataType[] arrayRefVar;   // 首选的方法 或 dataType arrayRefVar[];  // 效果相同，但不是首选方法

**注意:** 建议使用 **dataType[] arrayRefVar** 的声明风格声明数组变量。 dataType arrayRefVar[] 风格是来自 C/C++ 语言 ，在Java中采用是为了让 C/C++ 程序员能够快速理解java语言。

实例

下面是这两种语法的代码示例：

double[] myList;         // 首选的方法 或 double myList[];         //  效果相同，但不是首选方法

------

## 创建数组

Java语言使用new操作符来创建数组，语法如下：

```
arrayRefVar = new dataType[arraySize];
```

上面的语法语句做了两件事：

- 一、使用 dataType[arraySize] 创建了一个数组。
- 二、把新创建的数组的引用赋值给变量 arrayRefVar。

数组变量的声明，和创建数组可以用一条语句完成，如下所示：

```
dataType[] arrayRefVar = new dataType[arraySize];
```

另外，你还可以使用如下的方式创建数组。

```
dataType[] arrayRefVar = {value0, value1, ..., valuek};
```

数组的元素是通过索引访问的。数组索引从 0 开始，所以索引值从 0 到 arrayRefVar.length-1。

实例

下面的语句首先声明了一个数组变量 myList，接着创建了一个包含 10 个 double 类型元素的数组，并且把它的引用赋值给 myList 变量。

TestArray.java 文件代码：

```java
public class TestArray {
   public static void main(String[] args) {
      // 数组大小
      int size = 10;
      // 定义数组
      double[] myList = new double[size];
      myList[0] = 5.6;
      myList[1] = 4.5;
      myList[2] = 3.3;
      myList[3] = 13.2;
      myList[4] = 4.0;
      myList[5] = 34.33;
      myList[6] = 34.0;
      myList[7] = 45.45;
      myList[8] = 99.993;
      myList[9] = 11123;
      // 计算所有元素的总和
      double total = 0;
      for (int i = 0; i < size; i++) {
         total += myList[i];
      }
      System.out.println("总和为： " + total);
   }
}
```

以上实例输出结果为：

```
总和为： 11367.373
```

下面的图片描绘了数组 myList。这里 myList 数组里有 10 个 double 元素，它的下标从 0 到 9。

![java数组结构说明](https://www.runoob.com/wp-content/uploads/2013/12/12-130Q0221Q5602.jpg)

------

## 处理数组

数组的元素类型和数组的大小都是确定的，所以当处理数组元素时候，我们通常使用基本循环或者 foreach 循环。

示例

该实例完整地展示了如何创建、初始化和操纵数组：

TestArray.java 文件代码：

```java
public class TestArray {
   public static void main(String[] args) {
      double[] myList = {1.9, 2.9, 3.4, 3.5};
 
      // 打印所有数组元素
      for (int i = 0; i < myList.length; i++) {
         System.out.println(myList[i] + " ");
      }
      // 计算所有元素的总和
      double total = 0;
      for (int i = 0; i < myList.length; i++) {
         total += myList[i];
      }
      System.out.println("Total is " + total);
      // 查找最大元素
      double max = myList[0];
      for (int i = 1; i < myList.length; i++) {
         if (myList[i] > max) max = myList[i];
      }
      System.out.println("Max is " + max);
   }
}
```

以上实例编译运行结果如下：

```
1.9
2.9
3.4
3.5
Total is 11.7
Max is 3.5
```

------

## foreach 循环

JDK 1.5 引进了一种新的循环类型，被称为 foreach 循环或者加强型循环，它能在不使用下标的情况下遍历数组。

示例

该实例用来显示数组myList中的所有元素：

TestArray.java 文件代码：

```java
public class TestArray {
   public static void main(String[] args) {
      double[] myList = {1.9, 2.9, 3.4, 3.5};
 
      // 打印所有数组元素
      for (double element: myList) {
         System.out.println(element);
      }
   }
}
```

以上实例编译运行结果如下：

```
1.9
2.9
3.4
3.5
```

------

## 数组作为函数的参数

数组可以作为参数传递给方法。

例如，下面的例子就是一个打印 int 数组中元素的方法:

```java
public static void printArray(int[] array) {
  for (int i = 0; i < array.length; i++) {
    System.out.print(array[i] + " ");
  }
}
```

下面例子调用 printArray 方法打印出 3，1，2，6，4 和 2：

printArray(new int[]{3, 1, 2, 6, 4, 2});

------

## 数组作为函数的返回值

```java
public static int[] reverse(int[] list) {
  int[] result = new int[list.length];
 
  for (int i = 0, j = result.length - 1; i < list.length; i++, j--) {
    result[j] = list[i];
  }
  return result;
}
```

以上实例中 result 数组作为函数的返回值。

------

## 多维数组

多维数组可以看成是数组的数组，比如二维数组就是一个特殊的一维数组，其每一个元素都是一个一维数组，例如：

String str[][] = new String[3][4];

### 多维数组的动态初始化（以二维数组为例）

1. 直接为每一维分配空间，格式如下：

type arrayName = new type[arraylenght1][arraylenght2];

type 可以为基本数据类型和复合数据类型，arraylenght1 和 arraylenght2 必须为正整数，arraylenght1 为行数，arraylenght2 为列数。

例如：

int a[][] = new int[2][3];

解析：

二维数组 a 可以看成一个两行三列的数组。

2. 从最高维开始，分别为每一维分配空间，例如：

```java
String s[][] = new String[2][];
s[0] = new String[2];
s[1] = new String[3];
s[0][0] = new String("Good");
s[0][1] = new String("Luck");
s[1][0] = new String("to");
s[1][1] = new String("you");
s[1][2] = new String("!");
```

解析：

**s[0]=new String[2]** 和 **s[1]=new String[3]** 是为最高维分配引用空间，也就是为最高维限制其能保存数据的最长的长度，然后再为其每个数组元素单独分配空间 **s0=new String("Good")** 等操作。

### 多维数组的引用（以二维数组为例）

对二维数组中的每个元素，引用方式为 **arrayName[index1][index2]**，例如：

num[1][0];

------

## Arrays 类

java.util.Arrays 类能方便地操作数组，它提供的所有方法都是静态的。

具有以下功能：

- 给数组赋值：通过 fill 方法。
- 对数组排序：通过 sort 方法,按升序。
- 比较数组：通过 equals 方法比较数组中元素值是否相等。
- 查找数组元素：通过 binarySearch 方法能对排序好的数组进行二分查找法操作。

具体说明请查看下表：

| 序号 | 方法和说明                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **public static int binarySearch(Object[] a, Object key)**用二分查找算法在给定数组中搜索给定值的对象(Byte,Int,double等)。数组在调用前必须排序好的。如果查找值包含在数组中，则返回搜索键的索引；否则返回 (-(*插入点*) - 1)。 |
| 2    | **public static boolean equals(long[] a, long[] a2)**如果两个指定的 long 型数组彼此*相等*，则返回 true。如果两个数组包含相同数量的元素，并且两个数组中的所有相应元素对都是相等的，则认为这两个数组是相等的。换句话说，如果两个数组以相同顺序包含相同的元素，则两个数组是相等的。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。 |
| 3    | **public static void fill(int[] a, int val)**将指定的 int 值分配给指定 int 型数组指定范围中的每个元素。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。 |
| 4    | **public static void sort(Object[] a)**对指定对象数组根据其元素的自然顺序进行升序排列。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。 |

## 笔记列表

1. 数组倒序实例：

   ```
   public class Test2 {
       public static void main(String[] args){
           int[] test= {1,2,4,5,7};
           for (int i : test) {
               System.out.print(i+" ");
           }
           System.out.println("\n");
           test = Test2.reverse(test);
           for (int i : test) {
               System.out.print(i+" ");
           }
       }

       public static int[] reverse(int[] arr){
           int[] result = new int[arr.length];
           for (int i = 0,j=result.length-1; i < arr.length; i++,j--) {
               result[j] = arr[i];
           }
           return result;
       }
   }
   ```

2. ​

   ```
   // 声明二维数组：有两行，列数待定，数组结构 = { { }, { } }

   String s[][] = new String[2][]; 

   // 确定每行的元素个数，第一行有2个元素，第二行有3个元素，

   // 数组结构 = {{"E1", "E2"}, {"E1", "E2", "E3"}}

   s[0] = new String[2];

   s[1] = new String[3];
   ```

3. 实现数组和字符串的转换处理

   ```
   public class Test {
       public static void main(String args[]) {
           String str = "helloworld";
           char[] data = str.toCharArray();// 将字符串转为数组
           for (int x = 0; x < data.length; x++) {
               System.out.print(data[x] + "  ");
               data[x] -= 32;
               System.out.print(data[x] + "  ");
           }
           System.out.println(new String(data));
       }
   }
   ```

4. 冒泡排序

   ```
   public class BubbleSort {
   /**
    * N个数字要排序完成，总共进行N-1趟排序，每i趟的排序次数为(N-i)次，所以可以用双重循环语句，外层控制循环多少趟，内层控制每一趟的循环次数。
    * @param args
    */
       public static void main(String[] args) {
           int arr[] = {26,15,29,66,99,88,36,77,111,1,6,8,8};
           for(int i=0;i < arr.length-1;i++) {//外层循环控制排序趟数
               for(int j=0; j< arr.length-i-1;j++) {
                           //内层循环控制每一趟排序多少次
                   // 把小的值交换到前面
                   if (arr[j]>arr[j+1]) {
                       int temp = arr[j];
                       arr[j] = arr[j+1];
                       arr[j+1] = temp;
                   }
               }
               System.out.print("第"+(i+1)+"次排序结果：");
                                   //列举每次排序的数据
               for(int a=0;a<arr.length;a++) {
                   System.out.print(arr[a] + "\t");
               }
               System.out.println("");
           }
           System.out.println("最终排序结果：");
           for(int a = 0; a < arr.length;a++) {
               System.out.println(arr[a] + "\t");
           }
       }
   }
   ```

5. 选择排序：（比冒泡排序更快，运行次数更少）：

   ```
   public class Start
   {
       public static void main(String[] args)
       {
           int[] arr={20,60,51,81,285,12,165,51,81,318,186,9,70};
           for(int a:arr)
           {
               System.out.print(a+" ");
           }
           
           System.out.println("\n"+"---------------从大到小---------------");
           
           arr=toSmall(arr);
           for(int a:arr)
           {
               System.out.print(a+" ");
           }
           
           System.out.println("\n"+"---------------从小到大---------------");
           
           arr=toBig(arr);
           for(int a:arr)
           {
               System.out.print(a+" ");
           }
       }
   //    从大到小
       public static int[] toSmall(int[] arr)
       {
   //遍历数组里除最后一个的其他所有数，因为最后的对象没有与之可以相比较的数
           for(int i=0;i<arr.length-1;i++)
           {
   /*遍历数组里没有排序的所有数，并与上一个数进行比较
    *“k=i+1”因为自身一定等于自身，所以相比没有意义
    *而前面已经排好序的数，在比较也没有意义
    */
               for(int k=i+1;k<arr.length;k++)
               {
                   if(arr[k]<arr[i])//交换条件（排序条件）
                   {
                       int number=arr[i];
                       arr[i]=arr[k];
                       arr[k]=number;
                   }//交换
               }
           }
           return arr;
       }
   //    从小到大
   //和前面一样
       public static int[] toBig(int[] arr)
       {
           for(int i=0;i<arr.length-1;i++)
           {
               for(int k=i+1;k<arr.length;k++)
               {
                   if(arr[k]>arr[i])
                   {
                       int number=arr[i];
                       arr[i]=arr[k];
                       arr[k]=number;
                   }
               }
           }
           return arr;
       }
   }
   ```

   ​

6. java.util.Arrays类能方便地操作数组，它提供的所有方法都是静态的。具有以下功能：

   - ** 给数组赋值：通过fill方法。
   - ** 对数组排序：通过sort方法,按升序。
   - ** 比较数组：通过equals方法比较数组中元素值是否相等。
   - ** 查找数组元素：通过binarySearch方法能对排序好的数组进行二分查找法操作。

   ```
   import java.util.Arrays;

   public class TestArrays {
       public static void output(int[] array) {
           if (array != null) {
               for (int i = 0; i < array.length; i++) {
                   System.out.print(array[i] + " ");
               }
           }
           System.out.println();
       }

       public static void main(String[] args) {
           int[] array = new int[5];
           // 填充数组
           Arrays.fill(array, 5);
           System.out.println("填充数组：Arrays.fill(array, 5)：");
           TestArrays.output(array);
           // 将数组的第2和第3个元素赋值为8
           Arrays.fill(array, 2, 4, 8);
           System.out.println("将数组的第2和第3个元素赋值为8：Arrays.fill(array, 2, 4, 8)：");
           TestArrays.output(array);
           int[] array1 = { 7, 8, 3, 2, 12, 6, 3, 5, 4 };
           // 对数组的第2个到第6个进行排序进行排序
           Arrays.sort(array1, 2, 7);
           System.out.println("对数组的第2个到第6个元素进行排序进行排序：Arrays.sort(array,2,7)：");
           TestArrays.output(array1);
           // 对整个数组进行排序
           Arrays.sort(array1);
           System.out.println("对整个数组进行排序：Arrays.sort(array1)：");
           TestArrays.output(array1);
           // 比较数组元素是否相等
           System.out.println("比较数组元素是否相等:Arrays.equals(array, array1):" + "\n" + Arrays.equals(array, array1));
           int[] array2 = array1.clone();
           System.out.println("克隆后数组元素是否相等:Arrays.equals(array1, array2):" + "\n" + Arrays.equals(array1, array2));
           // 使用二分搜索算法查找指定元素所在的下标（必须是排序好的，否则结果不正确）
           Arrays.sort(array1);
           System.out.println("元素3在array1中的位置：Arrays.binarySearch(array1, 3)：" + "\n" + Arrays.binarySearch(array1, 3));
           // 如果不存在就返回负数
           System.out.println("元素9在array1中的位置：Arrays.binarySearch(array1, 9)：" + "\n" + Arrays.binarySearch(array1, 9));
       }
   }
   ```

   输出结果：

   ```
   填充数组：Arrays.fill(array, 5)：
   5 5 5 5 5 
   将数组的第2和第3个元素赋值为8：Arrays.fill(array, 2, 4, 8)：
   5 5 8 8 5 
   对数组的第2个到第6个元素进行排序进行排序：Arrays.sort(array,2,7)：
   7 8 2 3 3 6 12 5 4 
   对整个数组进行排序：Arrays.sort(array1)：
   2 3 3 4 5 6 7 8 12 
   比较数组元素是否相等:Arrays.equals(array, array1):
   false
   克隆后数组元素是否相等:Arrays.equals(array1, array2):
   true
   元素3在array1中的位置：Arrays.binarySearch(array1, 3)：
   1
   元素9在array1中的位置：Arrays.binarySearch(array1, 9)：
   -9
   ```

   ​

