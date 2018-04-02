---
title: Java知识点
tags: Java
category: Java
date: 2018-03-18 20:30:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0156.jpg)

27天学完Java
<!--more-->

### DAY001



![](http://ovi3ob9p4.bkt.clouddn.com/xuexi/001DAY.jpg)

#### DOS命令(理解)

​	(1)切换盘符(掌握)      `d: 回车`

​	(2)显示某目录下的所有文件或者文件夹(掌握)    `dir 回车`

 ​	(3)创建文件夹     `md 文件夹名称 回车`

 ​	(4)删除文件夹	`rd 文件夹名称 回车`

 	(5)进入目录(掌握 )      	`单级进入 cd 目录名称` 	`多级进入 cd 目录名称1\目录名称2\...`

 	(6)回退目录(掌握)         `单级回退 cd..`	`回退根目录 cd\`

 	(7)删除文件	`del 文件名称`	`*.txt 可以表示多个文件名称`

 	(8)清屏(掌握)       	`cls`

 	(9)退出    	`exit`

 	(10)删除带内容的文件夹 	`rd /s 文件夹名称 会提示是否删除`	`rd /q /s 文件夹名称 直接删除`	

#### path环境变量(理解)

​	(1)为什么要配置path环境变量
		为了让javac和java命令可以在任意目录下使用
	(2)如何配置
		A:方式1 直接修改path，在前面追加JDK的bin目录
		B:方式2(掌握) 
			新建JAVA_HOME: JDK的安装目录
			修改path: %JAVA_HOME%\bin;后面是以前的环境变量

#### classpath环境变量(理解)

​	(1)为什么要配置classpath环境变量
		为了让class文件可以在任意目录下运行
	(2)如何配置
		新建：classpath，把你想要在任意目录下运行的class文件所在目录配置过去即可。
		注意：将来在执行的时候，有先后顺序关系
	(3)path和classpath的区别
		path是为了让exe文件可以在任意目录下运行
		classpath是为了让class文件可以在任意目录下运行

#### 注释(掌握)

​	(1)注释:用于解释说明程序的文字
	(2)分类：
		A:单行：//注释文字
		B:多行：/* 注释文字 */
		C:文档注释：/** 注释文字 */
	(3)带注释的HelloWorld案例
	(4)注释的作用：
		A:解释说明程序，提高程序的阅读性
		B:帮助我们调试程序

#### 关键字(掌握)

​	(1)关键字:被Java赋予特定含义的单词
	(2)特点:全部小写
	(3)注意事项：
		A:goto和const作为保留字存在，目前不使用
		B:类似于Editplus这样的高级记事本，会对关键字有特殊颜色标记，方便记忆

#### 标识符(掌握)

```java
/*
	标识符：就是给类,接口,方法,变量等起名字时使用的字符序列(字符串)

	组成规则：
		A:英文字母大小写
		B:数字
		C:_和$

	注意事项：
		A:不能以数字开头
		B:不能是Java中的关键字
		C:区分大小写
			Student,student 这是两个名称

	常见的命名规则：见名知意
		A:包 其实就是文件夹,用于解决相同类名问题
			全部小写
			单级：com
			多级：cn.itcast

		B:类或者接口
			一个单词：首字母大写
				Student,Person,Teacher
			多个单词：每个单词的首字母大写
				HelloWorld,MyName,NameDemo

		C:方法或者变量
			一个单词：全部小写
				name,age,show()
			多个单词：从第二个单词开始，每个单词首字母大写
				myName,showAllStudentNames()

		D:常量
			一个单词：全部大写
				AGE
			多个单词：每个单词都大写，用_连接
				STUDENT_MAX_AGE
*/
class NameDemo {
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}
```



## DAY002

![](http://ovi3ob9p4.bkt.clouddn.com/xuexi/002DAY.jpg)

#### 常量(掌握)

```java
/*
	常量：在程序执行的过程中其值不可以发生改变
			举例：π

	分类：
		A:字面值常量
			1，12.5
		B:自定义常量(面向对象部分讲解)

	字面值常量分类：
		A:字符串常量 用""括起来的内容
		B:整数常量 所有的整数数据
		C:小数常量 所有的带小数的数据
		D:字符常量 用单引号括起来的内容
		E:布尔常量 只有两个值：true和false
		F:空常量 null(数组部分去讲解)
*/
class ConstantDemo {
	public static void main(String[] args) {
		//字符串常量
		System.out.println("HelloWorld");

		//整数常量
		System.out.println(100);

		//小数常量
		System.out.println(12.345);

		//字符常量
		System.out.println('A');
		//下面的是错误的
		//System.out.println('BC');
		System.out.println('1');
		
		//布尔常量
		System.out.println(true);
		System.out.println(false);
	}
}
```

#### 进制(理解)

​	(1)一种计数的方式。x进制表示逢x进1。
	(2)进制转换
		A:其他进制到十进制
			系数*基数^权之和。
		B:十进制到其他进制
			除基取余,直到商为0,余数反转。
		C:快速转换
			a:二进制和十进制
				8421码
			b:二进制和八进制
				三位组合
			c:二进制和十六进制
				四位组合
		D:任意X进制到任意Y进制的转换
			可以使用十进制作为桥梁即可。

#### 有符号数据表示法(理解)

​	(1)计算机中数据的存储和运算都是采用补码进行的。
	(2)数据的有符号表示法
		用0表示正号,1表示负号。
		A:原码
			正数:正常的二进制
			负数:符号为为1的二进制
		B:反码
			正数:和原码相同
			负数:和原码的区别是,符号位不变，数值位取反。1变0，0变1
		C:补码
			正数:和原码相同
			负数:反码+1
	(3)数据的有符号表示法练习
		A:已知原码，求反码和补码
		B:已知补码，求原码。
	(4)补充：float浮点数在计算机中的表示 
			符号位		指数位		底数位
			S		E		M

#### 变量(掌握)

​	(1)变量：在程序的运行过程中，其值发生改变的量。
	(2)定义格式：
		A:数据类型 变量名 = 初始化值;
		B:数据类型 变量名;
		  变量名 = 初始化值;

#### 数据类型(掌握)

​	(1)数据类型分类
		A:基本类型：4类8种
		B:引用类型：类，接口，数组
	(2)基本类型
		

```java
/*
	为了更好的表达现实世界的事物，Java针对不同的事物提供了不同的数据类型。

	数据类型：
		基本类型：4类8种
		引用类型：类，接口，数组。(后面讲)

	基本类型:
		整数：				占用的内存空间
			byte			1字节
								01111111
								10000000(1既表示符号位，又表示数值 -128)
			short			2字节
			int				4字节
			long			8字节
		浮点数：
			float			4字节
			double			8字节
		字符：
			char			2字节
		布尔：
			boolean			未知。1字节

	面试题：
		Java中字符可以存储一个汉字吗?
		可以。因为Java语言采用的是unicode编码，
		而unicode编码的每个字符是两个字节，
		所以，java中的字符可以存储一个汉字。


	注意：
		整数默认是int类型
		浮点数默认是double类型

		long类型的变量，要加l或者L。
		float类型的变量，要加f或者F。

		在同一对{}里面，是不能有同名的变量。
*/
class DataType {
	public static void main(String[] args) {
		//定义变量的格式：
		//数据类型 变量名 = 初始化值;

		//定义byte类型的变量
		byte b = 1;
		System.out.println(1);
		System.out.println(b);

		//定义short类型的变量
		short s = 100;
		System.out.println(s);

		//定义int类型的变量
		int i = 100000;
		System.out.println(i);

		//报错
		//int j = 2147483648;
		//System.out.println(j);

		//定义long类型的变量
		long l = 2147483648L;
		System.out.println(l);

		//定义float类型的变量
		float f = 12.34F;
		System.out.println(f);

		//定义double类型的变量
		double d = 23.56;
		System.out.println(d);

		//定义char类型的变量
		char ch = 'a';
		System.out.println(ch);

		//定义boolean类型的变量
		boolean flag = true;
		System.out.println(flag);
	}
}
```

##### 使用变量的注意事项

​	A:作用域
		每一个变量在它所属的大括号内有效，并且，同一个作用域不能定义同名的变量。

(for循环()中定义的变量与在for{}中定义有相同的作用域)
	B:初始化值
		变量必须先声明，赋值，最后才能使用
	C:在一行上定义的问题
		可以在一行上定义多个变量，但是不建议。

#### 类型转换(掌握)

​	注意：
		boolean类型不参与。

1. 隐式转换：从小到大

			byte,short,char --> int --> long --> float --> double

		long为什么可以到float呢?
		A:因为long和float的底层存储结构不同。
		B:数据范围
			long: 2^63
			float: 3.4*10^38
		
				3.4*10^38 > 3.4*8^38 = 3.4*2^3^38 = 3.4*2^114 > 2^63

2. 强制转换：从大到小

		一般不建议这样做，因为可能有精度的损失。
	格式：
		目标数据类型 变量名 = (目标数据类型)(被转换的数据);

#### 运算符(理解)

1. 运算：对常量和变量进行操作的过程称为运算。

2. 运算符：对常量和变量进行操作的符号称为运算符

3. 表达式：由运算符把常量和变量连接起来的式子

   注意：表达式必须有结果

#### 算术运算符(掌握)

1. +,-,*,/,%,++,--`
2. `+:`

			正号
		加法
		字符串连接符

3. %和/的区别`

			`%：余数`
		`/：商`
			整数相除，结果是整数。想得到小数，可以乘以或者除以1.0

			%的结果的符号和前面的那个数一致。

4. `++,--`

		A:单独使用
		放在数据的前面和后面效果一样。
	B:参与操作使用
		放在数据的前面，先数据变化，再参与运算。
		放在数据的后面，先参与运算，再数据变化。

#### 赋值运算符(掌握)

```java
/*
	赋值运算符：
		基本：=
		复合：+=,-=,*=,/=,%=,...
*/
class OperatorDemo {
	public static void main(String[] args) {
		//把10赋值给int类型的变量a
		int a = 10;

		//复合的用法
		int b = 10;
		b += 20; //结果等价于：b = b + 20;
		System.out.println(b);
	}
}
```

#### 关系运算符(掌握)

```java
/*
	关系运算符：
		==,!=,>,>=,<,<=

	特点：
		无论表达式是简单还是复杂，结果肯定是boolean类型。
	
	注意事项：
		关系运算符“==”不能误写成“=” 。
*/
class OperatorDemo {
	public static void main(String[] args) {
		int a = 10;
		int b = 10;
		int c = 20;
		System.out.println(a == b);
		System.out.println(a == c);
		System.out.println((a + b*c) == (a*b + c));
		System.out.println("----------------");

		System.out.println(a = b); //把b的值赋值给a，把a的值作为结果留下来
		System.out.println(a = c);
	}
}
```

#### 逻辑运算符(掌握)


```java
/*
	&&和&的区别? 前者有短路效果，只要左边是false，右边不执行。而后者，全部执行。
	||和|的区别? 前者有短路效果，只要左边是true，右边不执行。而后者，全部执行。
*/
class OperatorDemo2 {
	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		int c = 30;

		//&:逻辑与	有false则false
		System.out.println(a>b & a>c); //false & false = false
		System.out.println(a>b & a<c); //false & true = false
		System.out.println(a<b & a>c); //true & false = false
		System.out.println(a<b & a<c); //true & true = true
		System.out.println("--------");

		//&&:
		System.out.println(a>b && a>c); //false && false = false
		System.out.println(a>b && a<c); //false && true = false
		System.out.println(a<b && a>c); //true && false = false
		System.out.println(a<b && a<c); //true && true = true
		System.out.println("--------");

		//|:逻辑或	有true则true
		System.out.println(a>b | a>c); //false | false = false
		System.out.println(a>b | a<c); //false | true = true
		System.out.println(a<b | a>c); //true | false = true
		System.out.println(a<b | a<c); //true | true = true
		System.out.println("--------");

		//||:
		System.out.println(a>b || a>c); //false || false = false
		System.out.println(a>b || a<c); //false || true = true
		System.out.println(a<b || a>c); //true || false = true
		System.out.println(a<b || a<c); //true || true = true
		System.out.println("--------");

		int x = 3;
		int y = 4;
		//System.out.println((x++)>3 & (y++)>4); //false & false = false
		//System.out.println(x);//4
		//System.out.println(y);//5
		System.out.println((x++)>3 && (y++)>4);
		System.out.println(x);//4
		System.out.println(y);//4
	}
}
```

```java
/*
	逻辑运算符：
		&,|,!,^
		&&,||

	注意：
		逻辑运算符连接的应该是一个布尔表达式。
*/
class OperatorDemo {
	public static void main(String[] args) {
		//&,|,!,^
		int a = 10;
		int b = 20;
		int c = 30;

		//&:逻辑与	有false则false
		System.out.println(a>b & a>c); //false & false = false
		System.out.println(a>b & a<c); //false & true = false
		System.out.println(a<b & a>c); //true & false = false
		System.out.println(a<b & a<c); //true & true = true
		System.out.println("--------");

		//|:逻辑或	有true则true
		System.out.println(a>b | a>c); //false | false = false
		System.out.println(a>b | a<c); //false | true = true
		System.out.println(a<b | a>c); //true | false = true
		System.out.println(a<b | a<c); //true | true = true
		System.out.println("--------");

		//^:逻辑异或 相同false，不同true。
		//情侣：男男，男女，女男，女女
		System.out.println(a>b ^ a>c); //false ^ false = false
		System.out.println(a>b ^ a<c); //false ^ true = true
		System.out.println(a<b ^ a>c); //true ^ false = true
		System.out.println(a<b ^ a<c); //true ^ true = false
		System.out.println("--------");

		//!:逻辑非
		System.out.println((a>b));//false
		System.out.println(!(a>b));//true
		System.out.println(!!(a>b));//false
		System.out.println(!!!(a>b));//true
		System.out.println(!!!!(a>b));//false
	}
}
```

#### 常用字符与ASCII代码对照表

为了便于查询，以下列出**ASCII****码表**：第128～255号为扩展字符（不常用）

| ASCII码 | 键盘 | ASCII 码 | 键盘  | ASCII 码 | 键盘 | ASCII 码 | 键盘 |
| ------- | ---- | -------- | ----- | -------- | ---- | -------- | ---- |
| 27      | ESC  | 32       | SPACE | 33       | !    | 34       | "    |
| 35      | #    | 36       | $     | 37       | %    | 38       | &    |
| 39      | '    | 40       | (     | 41       | )    | 42       | *    |
| 43      | +    | 44       | '     | 45       | -    | 46       | .    |
| 47      | /    | 48       | 0     | 49       | 1    | 50       | 2    |
| 51      | 3    | 52       | 4     | 53       | 5    | 54       | 6    |
| 55      | 7    | 56       | 8     | 57       | 9    | 58       | :    |
| 59      | ;    | 60       | <     | 61       | =    | 62       | >    |
| 63      | ?    | 64       | @     | 65       | A    | 66       | B    |
| 67      | C    | 68       | D     | 69       | E    | 70       | F    |
| 71      | G    | 72       | H     | 73       | I    | 74       | J    |
| 75      | K    | 76       | L     | 77       | M    | 78       | N    |
| 79      | O    | 80       | P     | 81       | Q    | 82       | R    |
| 83      | S    | 84       | T     | 85       | U    | 86       | V    |
| 87      | W    | 88       | X     | 89       | Y    | 90       | Z    |
| 91      | [    | 92       | \     | 93       | ]    | 94       | ^    |
| 95      | _    | 96       | `     | 97       | a    | 98       | b    |
| 99      | c    | 100      | d     | 101      | e    | 102      | f    |
| 103     | g    | 104      | h     | 105      | i    | 106      | j    |
| 107     | k    | 108      | l     | 109      | m    | 110      | n    |
| 111     | o    | 112      | p     | 113      | q    | 114      | r    |
| 115     | s    | 116      | t     | 117      | u    | 118      | v    |
| 119     | w    | 120      | x     | 121      | y    | 122      | z    |
| 123     | {    | 124      | \|    | 125      | }    | 126      | ~    |

 

**运算符的优先级（从高到低）**

| 优先级 | 描述         | 运算符                  |
| ------ | ------------ | ----------------------- |
| 1      | 括号         | ()、[]                  |
| 2      | 正负号       | +、-                    |
| 3      | 自增自减，非 | ++、--、!               |
| 4      | 乘除，取余   | *、/、%                 |
| 5      | 加减         | +、-                    |
| 6      | 移位运算     | <<、>>、>>>             |
| 7      | 大小关系     | >、>=、<、<=            |
| 8      | 相等关系     | ==、!=                  |
| 9      | 按位与       | &                       |
| 10     | 按位异或     | ^                       |
| 11     | 按位或       | \|                      |
| 12     | 逻辑与       | &&                      |
| 13     | 逻辑或       | \|\|                    |
| 14     | 条件运算     | ?:                      |
| 15     | 赋值运算     | =、+=、-=、*=、/=、%=   |
| 16     | 位赋值运算   | &=、\|=、<<=、>>=、>>>= |

如果在程序中，要改变运算顺序，可以使用()。

### DAY003

![](http://ovi3ob9p4.bkt.clouddn.com/xuexi/003DAY.jpg)

#### 位运算符(了解)

```java
/*
	位运算符：位运算符一定是先把数据转成二进制，然后再运算。

	面试题：&和&&的区别?
			A:&和&&都可以作为逻辑运算，&&具有短路效果。
			B:&还可以作为位运算。
*/
class OperatorDemo {
	public static void main(String[] args) {
		//&,|,^,~
		System.out.println(3 & 4); //0
		System.out.println(3 | 4); //7
		System.out.println(3 ^ 4); //7
		System.out.println(~3); //
	}
}

/*
	A:计算出3，4的二进制
		3的二进制：00000000 00000000 00000000 00000011
		4的二进制：00000000 00000000 00000000 00000100
	B:位&运算	有0则0
		00000000 00000000 00000000 00000011
	   &00000000 00000000 00000000 00000100
	   ------------------------------------
	    00000000 00000000 00000000 00000000
	C:位|运算	有1则1
		00000000 00000000 00000000 00000011
	   &00000000 00000000 00000000 00000100
	   ------------------------------------
	    00000000 00000000 00000000 00000111
	D:位^运算	相同则0，不同则1
		00000000 00000000 00000000 00000011
	   &00000000 00000000 00000000 00000100
	   ------------------------------------
	    00000000 00000000 00000000 00000111
	E:位~运算 把数据每个位都按位取反
		00000000 00000000 00000000 00000011
	   ~11111111 11111111 11111111 11111100
	 反:11111111 11111111 11111111 11111011
	 原:10000000 00000000 00000000 00000100
*/
```

```java
/*
	<<:左移，右边补0
	>>:右移，根据最高位确定补齐是0还是1
	>>>:无符号右移 左边补0
*/
class OperatorDemo2 {
	public static void main(String[] args) {
		/*
		System.out.println(4 << 2); //16 = 4 * 2^2
		System.out.println(3 << 3); //3 * 2 ^ 3
		System.out.println(32 >> 2); //32 / 2^2
		System.out.println(32 >>> 2);
		*/

		System.out.println(-32 >> 2);
		System.out.println(-32 >>> 2);
	}
}

/*
	A:<<
		4的二进制：
			00000000 00000000 00000000 00000100
		(00)000000 00000000 00000000 0000010000

	B:>>>
		原：10000000 00000000 00000000 00100000
		反：11111111 11111111 11111111 11011111
		补：11111111 11111111 11111111 11100000

		>>>
			11111111 11111111 11111111 11100000
			0011111111 11111111 11111111 111000(00)
*/
```

```java
/*
	位^运算符号：针对同一个数据异或两次，其值不变

	 面试题：
		请把两个数据进行交换。
		说明：如果我没有指定数据的类型，默认是int类型。适用于我讲课。
*/
class OperatorTest {
	public static void main(String[] args) {
		/*
		System.out.println(1 ^ 2 ^ 2);//1
		System.out.println(1 ^ 1 ^ 2);//2
		System.out.println(15 ^ 3 ^ 7 ^ 7 ^ 3);//15
		*/

		//定义两个变量
		int a = 10;
		int b = 20;

		//System.out.println(a+"---"+b);
		System.out.println("a="+a+",b="+b);

		//怎么做呢?
		//方式1：使用第三方变量。开发中常用此方案。
		/*
		int temp = a;
		a = b;
		b = temp;
		System.out.println("a="+a+",b="+b);
		*/

		//方式2：不好，可能a+b已经超出范围了。
		/*
		a = a + b; //a=30
		b = a - b; //b=10
		a = a - b; //a=20
		System.out.println("a="+a+",b="+b);
		*/

		//方式3：不好，可能a+b已经超出范围了。
		//a = (a+b) - (b=a); //一句话搞定
		//System.out.println("a="+a+",b="+b);

		//方式4：面试
		a = a ^ b;
		b = a ^ b; //b = a ^ b = a ^ b ^ b = a;
		a = a ^ b; //a = a ^ b = a ^ b ^ a = b;
		System.out.println("a="+a+",b="+b);
		//记忆：左边，a,b,a。右边a^b
	}
}
```

#### 三元运算符(掌握)

​	

```java
/*
	三元运算符：
	格式
		(关系表达式)?表达式1：表达式2；

	执行流程：
		计算关系表达式，看其返回值
			true:表达式1就是整个表达式的值
			false:表达式2就是整个表达式的值

*/
class OperatorDemo {
	public static void main(String[] args) {
		//获取两个数据中的较大值
		int x = 3;
		int y = 4;
		int z = (x > y)? x : y;
		System.out.println(z);

		//比较两个数是否相等
		int a = 4;
		int b = 4;
		//boolean flag = (a==b)?true:false;
		boolean flag = (a == b);
		System.out.println(flag);

		//获取三个数据中的较大值
		int c = 30;
		int d = 40;
		int e = 50;
		//int max = (c>d)?(c>e?c:e):(d>e?d:e);
		int temp = (c>d)?c:d;
		int max = (temp>e)?temp:e;
		System.out.println(max);
	}
}
```

#### 键盘录入数据(掌握)

```java
/*
	为了程序的数据更加的灵活，我们决定加入键盘录入数据。

	如何使用键盘录入数据呢?目前你就给我记住了。
	A:导包
		import java.util.Scanner;

		在class的上面
	B:创建对象
		Scanner sc = new Scanner(System.in);
	C:获取数据
		int i = sc.nextInt();
*/
import java.util.Scanner;

class OperatorDemo {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);

		System.out.println("请输入一个整数：");
		//获取数据
		int i = sc.nextInt();

		System.out.println("i:"+i);
	}
}
```

#### 流程控制(掌握)

​	(1)流程控制语句：
		顺序结构

```java
/*
	是程序中最简单最基本的流程控制，没有特定的语法结构，按照代码的先后顺序，
	依次执行，程序中大多数的代码都是这样执行的。
	
	总的来说：写在前面的先执行，写在后面的后执行
*/
class OrderDemo {
	public static void main(String[] args) {
		System.out.println("我爱林青霞");
		System.out.println("我爱Java");
		System.out.println("我爱张曼玉");
		System.out.println("林青霞爱张曼玉");
	}
}
```

​		选择结构

```java
/*
	if语句的第二种格式和三元运算符的区别：
		三元运算符：
			关系表达式?表达式1:表达式2;

		if语句格式2：
			if(关系表达式){
				语句体1;
			}else {
				语句体2;
			}

	总结：
		三元运算符能够实现的，if语句的第二种格式都可以实现。反之不成立。
		什么时候不成立呢?
			当if语句的语句体是一条输出语句时，就不成立。
			因为三元运算符是一个运算符，要求有结果返回，而输出语句不能作为一个结果返回。
*/
import java.util.Scanner;

class IfDemo4 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);

		//获取键盘录入数据
		System.out.println("请输入第一个数据：");
		int a = sc.nextInt();
		System.out.println("请输入第二个数据：");
		int b = sc.nextInt();

		//使用三元运算符实现
		int c =  (a>b)?a:b;
		System.out.println("c:"+c);

		//用if语句格式2实现
		int d;
		if(a > b) {
			d = a;
		}else {
			d = b;
		}
		System.out.println("d:"+d);
		System.out.println("------------------");

		//直接把结果输出
		if(a > b) {
			System.out.println("a:"+a);
		}else {
			System.out.println("b:"+b);
		}

		//用三元运算符改进
		//(a>b)?System.out.println("a:"+a):System.out.println("b:"+b);
	}
}

```

​	

```java
/*
	if语句格式3：
		if(关系表达式1) {
		     语句体1;
		}else  if (关系表达式2) {
			 语句体2;
		}
		…
		else {
			 语句体n+1;
		}

	执行流程：
		首先判断关系表达式1看其结果是true还是false
		如果是true就执行语句体1
		如果是false就继续判断关系表达式2看其结果是true还是false
		如果是true就执行语句体2
		如果是false就继续判断关系表达式…看其结果是true还是false
		…
		如果没有任何关系表达式为true，就执行语句体n+1。

	需求：
		键盘录入学生成绩，根据成绩输出对于的评价。
			90-100	优秀
			80-90	好
			70-80	良
			60-70	及格
			60以下	不及格
*/
import java.util.Scanner;

class IfDemo5 {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);

		//键盘录入学生成绩
		System.out.println("请输入成绩：");
		int score = sc.nextInt();

		//校验数据的时候，一定要注意：
		//正确数据
		//错误数据
		//边界数据

		/*
		if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else {
			System.out.println("不及格");
		}
		*/

		//这个时候，虽然可以满足要求了。但是没有考虑到错误数据的情况。
		//所以，我们需要加一个判断
		/*
		if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else if(score>=0 && score<60) {
			System.out.println("不及格");
		}else {
			System.out.println("输入的成绩有误");
		}
		*/

		//我们也可以先判断成绩是否有误
		if(score<0 || score>100) {
			System.out.println("输入的成绩有误");
		}else if(score>=90 && score<=100) {
			System.out.println("优秀");
		}else if(score>=80 && score<90) {
			System.out.println("好");
		}else if(score>=70 && score<80) {
			System.out.println("良");
		}else if(score>=60 && score<70) {
			System.out.println("及格");
		}else {
			System.out.println("不及格");
		}
	}
}
```

```java
/*
	switch语句格式：
		switch(表达式) {
			case 值1：
				语句体1;
				break;
		    case 值2：
				语句体2;
				break;
				…
		    default：	
				语句体n+1;
				break;
		}

		格式解释：
			A:switch表示这是switch语句
			B:表达式的取值
				byte,short,int,char
				JDK5以后可以是枚举类型。(enum)
				JDK7以后可以是字符串。(String)
			C:case后面跟的是要和表达式进行比较的值
			D:语句体可以是多条语句
			E:break表示中断，结束的意思，可以结束switch语句
			F:default语句表示所有情况都不匹配的时候，就执行该处的内容，和if语句的else相似。
		
		面试题：
			switch的表达式可以是byte类型吗?可以是long类型吗?可以是String类型吗?
				可以。
				不可以。
				JDK7以后可以。

		执行流程：
			A:首先计算出表达式的值
			B:其次，和case依次比较，一旦有对应的值，就会执行相应的语句，
			  在执行的过程中，遇到break就会结束。
			C:最后，如果所有的case都和表达式的值不匹配，就会执行default语句体部分，然后程序结束掉。

		需求：根据键盘录入的数值1，2，3，…7输出对应的星期一，星期二，星期三…星期日。

		分析：
			A:键盘录入数据，用Scanner实现
			B:对录入的数据进行判断，用switch实现
			C:输出对应的结果
	
	注意事项
		A:case后面只能是常量，不能是变量，而且，多个case后面的值不能出现相同的
		B:default可以省略吗
			可以省略。一般不建议。除非判断的值是固定的。
		C:break可以省略吗
			可以。最后一个肯定是没有任何问题的。
			中间的省略也是可以的，但是不建议，因为可能对我们想要的结果产生影响。
		D:default的位置一定要在最后吗
			不一定，可以在任何和case相对应的位置。
			但是，这个时候，最好加上break。
		E:switch语句的结束条件
			a:遇到break。
			b:执行到程序的末尾

*/
import java.util.Scanner;

class SwitchDemo {
	public static void main(String[] args) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);

		//键盘录入数据
		System.out.println("请输入一个数据(1-7)：");
		int week = sc.nextInt();

		//用switch语句实现
		switch(week) {
			case 1:
				System.out.println("星期一");
				break;
			case 2:
				System.out.println("星期二");
				break;
			case 3:
				System.out.println("星期三");
				break;
			case 4:
				System.out.println("星期四");
				break;
			case 5:
				System.out.println("星期五");
				break;
			case 6:
				System.out.println("星期六");
				break;
			case 7:
				System.out.println("星期日");
				break;
			default:
				System.out.println("你输入的数据有误");
				break;
		}
	}
}
```

​	循环结构

```java
/*
	for和while的区别：
	使用区别：控制条件语句所控制的那个变量，在for循环结束后，就不能再被访问到了，
			  而while循环结束还可以继续使用，如果你想继续使用，就用while，否则推荐使用for。
			  原因是for循环结束，该变量就从内存中消失，能够提高内存的使用效率。
	场景区别：
			for循环适合针对一个范围判断进行操作
				水仙花
			while循环适合判断次数不明确操作
				吃葡萄
*/
class WhileDemo2 {
	public static void main(String[] args) {
		int x = 0;
		while(x<10) {
			System.out.println(x);
			x++;
		}
		System.out.println(x+"---");
		System.out.println("-----------");

		for(int y=0; y<10; y++) {
			System.out.println(y);
		}
		//System.out.println(y+"---");
	}
}
```



```java
/*
	do...while格式：
		do {
			语句体;
		}while(条件表达式);

	变形格式：
		初始化语句;
		do {
			循环体语句;
			控制条件语句;
		}while(判断条件语句);
		
		
		for(初始化语句;判断条件语句;控制条件语句) {
			 循环体语句;
		}
*/
class DoWhileDemo {
	public static void main(String[] args) {
		/*
		int sum = 0;
		for(int x=1; x<=100; x++) {
			sum+=x;
		}
		System.out.println(sum);
		*/

		//do...while
		int sum = 0;
		int x = 1;
		do{
			sum+=x;
			x++;
		}while (x<=100);
		System.out.println(sum);
	}
}
```

```java
/*
	需求：在控制台输出九九乘法表。

		1*1=1
		1*2=2	2*2=4
		1*3=3	2*3=6	3*3=9
		...
		1*9=9	2*9=18	3*9=27	4*9=36	...

	转移字符：
		\t	tab键的位置
*/
class ForForDemo3 {
	public static void main(String[] args) {
		//如果我们把每一行看作一颗*
		//那么这其实就是我们刚才的三角形
		/*
		for(int x=1; x<=9; x++) {
			for(int y=1; y<=x; y++) {
				System.out.print("*"+"\t");
			}
			System.out.println();
		}
		*/

		//接下来，我们要把*替换为表达式
		for(int x=1; x<=9; x++) {
			for(int y=1; y<=x; y++) {
				System.out.print(y+"*"+x+"="+(x*y)+"\t");
			}
			System.out.println();
		}
	}
}

```

### DAY004

![](http://ovi3ob9p4.bkt.clouddn.com/xuexi/004DAY.jpg)

#### 循环语句(掌握)

```java

	(1)for循环
		for(初始化表达式;条件表达式;控制条件表达式){
			循环体;
		}
	执行流程：
		A:首先执行初始化表达式
		B:其次执行条件表达式，看其返回值
			如果是true，就继续
			如果是false，就结束循环
		C:执行循环体;
		D:执行控制条件表达式
		E:回到B
(2)while循环
	基本格式：
	while(条件表达式){
		语句体;
	}
	
	变形：
	初始化表达式;
	while(条件表达式){
		循环体;
		控制条件表达式;
	}
(3)do...while循环(理解)
	基本格式：
	do {
		语句体;
	}while(条件表达式);

	变形:
	初始化表达式;
	do{
		循环体;
		控制条件表达式;
	}while(条件表达式);
(4)三种循环的区别
	A:do...while至少执行一次循环体，而其他两种循环都是先判断在执行。
	B:while和for循环是可以等价转换的。在使用的时候，优先选择for。
		规则：
			a:如果控制条件表达式控制的那个变量，后面还要使用，只能使用while
			b:for适合范围的取值，while适合次数不明确的操作
(5)注意事项：
	死循环：
		for(;;){}

		while(true){}
(6)案例：
	A:输出10次HelloWorld
		for(int x=0; x<10; x++) {
			System.out.println("HelloWorld");
		}
	B:输出1-10
		for(int x=1; x<=10; x++) {
			System.out.println(x);
		}
	C:输出10-1
		for(int x=10; x>0; x--) {
			System.out.println(x);
		}
	D:求1-10的和
		int sum = 0;
		for(int x=1; x<=10; x++) {
			sum += x;
		}
		System.out.println(sum);
	E:求1-100的偶数和(奇数自己写)
		//方式1：
		int sum = 0;
		for(int x=0; x<=100; x+=2) {
			sum += x;
		}
		System.out.println(sum);

		//方式2：
		int sum = 0;
		for(int x=0; x<=100; x++) {
			if(x%2 == 0){
				sum += x;
			}
		}
		System.out.println(sum);
	F:输出水仙花的数
		for(int x=100; x<1000; x++) {
			int ge = x%10;
			int shi = x/10%10;
			int bai = x/10/10%10;

			if(x == (ge*ge*ge+shi*shi*shi+bai*bai*bai)) {
				System.out.println(x);
			}
		}
	G:统计水仙花的个数
		int count = 0;
		for(int x=100; x<1000; x++) {
			int ge = x%10;
			int shi = x/10%10;
			int bai = x/10/10%10;

			if(x == (ge*ge*ge+shi*shi*shi+bai*bai*bai)) {
				count++;
			}
		}
		System.out.println(count);
	H:输出满足条件的5位数
		for(int x=10000; x<100000; x++) {
			int ge = x%10;
			int shi = x/10%10;
			int bai = x/10/10%10;
			int qian = x/10/10/10%10;
			int wan = x/10/10/10/10%10;

			if((ge==wan) && (shi==qian) && (bai==ge+shi+qian+wan)) {
				System.out.println(x);
			}
		}
	I:统计满足条件的数据
		int count = 0;
		for(int x=0; x<1000; x++) {
			if(x%3==2 && x%5==3 && x%7==2) {
				count++;
			}
		}
		System.out.println(count);
	J:折叠次数
		int start = 1;
		int end = 884800;
		int count = 0;

		while(start<=end) {
			count++;

			start*=2;
		}

		System.out.println(count);
	K:小芳存钱的题目，自己把代码看懂即可。
```

#### 控制跳转语句(掌握)

1. break:中断

			A:场景
			switch
			循环语句中
		B:使用
			退出单层循环
			退出多层循环(带标签的使用)

2. continue:继续

			A:场景
			循环语句中
		B:使用
			退出单层循环
			退出多层循环(带标签的使用)

		break和continue的区别：
		break:退出整个循环
		continue:退出一次循环，进行下一次

3. return:返回

		返回，让方法结束。其实在void类型的方法，最后也有一个return。
	只不过是：reutrn;

	. 在控制台输出多少次：	

		"Java基础班"

#### 方法(掌握)

```java
/*
	方法：完成特定功能的代码块

	格式：
		修饰符 返回值类型 方法名(参数类型 参数名1，参数类型 参数名2…) {
			方法体;
			return 返回值;
		}

	修饰符：public static
	返回值类型：功能最终的值的数据类型
	方法名：是为了方便调用而起的一个名字
	参数：
		形式参数：用于接受实际参数的变量
		实际参数：实际参与运算的数据
	方法体：完成特定功能的代码
	return 返回值：通过return把结果返回给调用者

	我们虽然知道了方法的格式，那么我们该如何写一个方法呢?
	两个明确：
		A:返回值类型
			结果的数据类型
		B:参数列表
			有几个参数参加，并且每个参数的数据类型是什么

	需求：求两个数据之和的案例
		A:我没有说数据的类型，默认int类型。
		B:求两个数据的和
			说明有两个参数参加，并且默认都是int类型
		C:两个int类型相加的结果是什么类型呢?
			是int类型，所以返回值类型这里是int类型

	方法的执行特点：
		不调用不执行。

	有明确返回值的方法的调用：
		A:单独调用，没有意义。
		B:输出调用，不是很好，因为我们可能需要针对结果还要进行其他的操作。
		C:赋值调用，推荐方式。
		
	方法的注意事项：
		A:方法不调用不执行
		B:方法与方法是平级关系，不能嵌套定义
		C:方法定义的时候参数之间用逗号隔开
		D:方法调用的时候不用在传递数据类型
			可以传递变量，也可以常量。就是不能加数据类型
		E:如果方法有明确的返回值，一定要有return带回一个值
*/
class MethodDemo {
	public static void main(String[] args) {
		//定义两个变量
		int x = 10;
		int y = 20;

		//单独调用
		//sum(x,y);

		//输出调用
		System.out.println(sum(x,y));

		//赋值调用
		int result = sum(x,y);
		//result进行操作
		System.out.println(result);
	}

	//如果我自己要想写一个方法
	public static int sum(int a,int b) {
		int c = a + b;
		return c;
	}
}
```
### DAY005

#### 方法重载(理解)

​	

```java
/*
	方法重载：
		在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。
		和返回值类型无关。
*/
class MethodDemo {
	public static void main(String[] args) {
		//需求：请写一个功能，实现两个数据的求和
		System.out.println(sum(10,20));

		//需求：请写一个功能，实现三个数据的求和
		//System.out.println(sum2(10,20,30));
		System.out.println(sum(10,20,30));

		System.out.println(sum(1.5,2.5));
	}

	public static int sum(int a,int b) {
		return a + b;
	}

	/*
	public static int sum2(int a,int b,int c) {
		return a + b + c;

		//方法的嵌套调用
		//return sum(sum(a,b),c);
	}
	*/

	//由于方法名要表达的其实是该方法的作用
	//所以，sum2这个名字不好，还是要用sum 比较好
	public static int sum(int a,int b,int c) {
		return a + b + c;
	}

	public static double sum(double a,double b) {
		return a + b;
	}
}
```

#### 一维数组(掌握)

1. 数组:存储同一种数据类型的多个元素的集合

			每个元素都有编号，从0开始。
		最大编号是数组的长度-1

2. 数组的格式：

			A:数据类型[] 数组名;
		B:数据类型 数组名[];

3. 数组的初始化：

			A:动态初始化 只给长度，不给元素
			`int[] arr = new int[3];`
		B:静态初始化 不给长度，给元素
			`int[] arr = new int[]{1,2,3};`
			`简化版：int[] arr = {1,2,3};`

4. java中的内存分配

			A:栈 存储局部变量
		B:堆 new出来的
		C:方法区
		D:本地方法区
		E:寄存器

5. 两个常见小问题

			A:数组越界
		B:空指针异常

	. 数组常见操作	获取数组长度：数组名.length

			A:数组遍历
		B:获取最值
		C:数组反转
		D:查表法
		E:查找指定元素第一次出现的索引

```java
/*
	数组：存储同一种数据类型的多个元素的集合。(也可以称为容器)

	数组的定义格式：
		格式1：数据类型[] 数组名;
			int[] arr;
		格式2：数据类型 数组名[];
			int arr[];

		推荐方式1。

	现在的数组没有元素，使用是没有意义的。
	接下来，我们要对数组进行初始化。
	那么，我们如何对数组进行初始化呢?
		动态初始化：初始化时只指定数组长度，由系统为数组分配初始值。
		静态初始化：初始化时指定每个数组元素的初始值，由系统决定数组长度。

	动态初始化：
		数据类型[] 数组名 = new 数据类型[数组长度];

*/
class ArrayDemo {
	public static void main(String[] args) {
		//按照动态初始化数组的格式，我们来定义一个存储3个int类型元素的数组
		int[] arr = new int[3];

		/*
			左边：
				int:说明数组中的元素的数据类型。
				[]:说明这是一个数组
				arr:数组的名称
			右边：
				new:为实体(对象)开辟内存空间
					Scanner sc = new Scanner(System.in);
				int:说明数组中的元素的数据类型。
				[]:说明这是一个数组
				3:说明的是数组中的元素个数
		*/

		//我们如何获取里面的值呢?
		//数组名称
		System.out.println(arr); //[I@778b3fee 地址值
		//如何获取元素值呢?
		//数组为每个元素分配了一个编号，这个编号的专业叫法：索引。
		//而且是从0开始编号的。也就是说数组的最大编号是长度-1。
		//有了编号以后，我们就可以通过数组名和编号的配合取得数组元素
		//格式：数组名[编号];
		System.out.println(arr[0]); //0
		System.out.println(arr[1]); //0
		System.out.println(arr[2]); //0
	}
}
/*
	静态初始化格式：
		数据类型[] 数组名 = new 数据类型[]{元素1,元素2,…};

		简化版：
		数据类型[] 数组名 =	{元素1,元素2,…};
*/
class ArrayDemo5 {
	public static void main(String[] args) {
		//定义一个数组
		//int[] arr = new int[]{1,2,3};

		//简化后
		int[] arr = {1,2,3};

		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
	}
}

/*
	数组操作常见的两个小问题:
		A:数组索引越界
			ArrayIndexOutOfBoundsException
			因为我们访问了不存在的索引。
		B:空指针异常
			NullPointerException
			因为数组已经不再指向堆内存，所以就不能再去访问堆内存的元素了。
*/
class ArrayDemo6 {
	public static void main(String[] args) {
		//定义数组
		int[] arr = {1,2,3};

		//System.out.println(arr[3]);

		arr = null; //把arr指向堆内存给去掉了，arr没有指向了。
		System.out.println(arr[0]);
	}
}
```

#### 二维数组(理解)

```java
/*
	二维数组：元素为一维数组的数组。

	定义格式1：
		数据类型[][] 变量名 = new 数据类型[m][n];
		
		m:m表示这个二维数组有多少个一维数组
		n:n表示每一个一维数组的元素个数

		变形：
			数据类型 变量名[][] = new 数据类型[m][n];
			数据类型[] 变量名[] = new 数据类型[m][n];

			int[] x,y[];
*/
class Array2Demo {
	public static void main(String[] args) {
		//定义一个二维数组
		int[][] arr = new int[3][2];
		//表示arr这个二维数组有三个元素
		//每个元素是一个一维数组
		//每一个一维数组有2个元素

		System.out.println(arr); //[[I@778b3fee
		System.out.println(arr[0]); //[I@57125f92
		System.out.println(arr[1]);
		System.out.println(arr[2]);

		//如何输出元素呢?
		System.out.println(arr[0][1]);
		System.out.println(arr[2][2]);
	}
}

/*
	定义格式2：
		数据类型[][] 变量名 = new 数据类型[m][];
		
		m:m表示这个二维数组有多少个一维数组
*/
class Array2Demo2 {
	public static void main(String[] args) {
		//定义一个数组
		int[][] arr = new int[3][];
		//这里我们仅仅知道这个二维数组有3个一维数组
		//但是，每个一维数组有几个元素，我们是不知道的

		System.out.println(arr); //[[I@7d3598c3
		System.out.println(arr[0]); //null
		System.out.println(arr[1]); //null
		System.out.println(arr[2]); //null


		arr[0] = new int[3];
		arr[1] = new int[1];
		arr[2] = new int[2];
		System.out.println(arr[0]); //
		System.out.println(arr[1]); //
		System.out.println(arr[2]); //


		arr[2][1] = 100;
		arr[1][3] = 200;
	}
}

/*
	定义格式2：
		数据类型[][] 变量名 = new 数据类型[][]{{元素…},{元素…},{元素…}};

		变形格式：
			数据类型[][] 变量名 = {{元素…},{元素…},{元素…}};
*/
class Array2Demo3 {
	public static void main(String[] args) {
		//定义数组
		//int[][] arr = {{1,2,3},{4,5,6},{7,8,9}};
		int[][] arr = {{1,2,3},{4,5},{8}};

		System.out.println(arr);
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);

		System.out.println(arr[0][0]);
		System.out.println(arr[0][1]);
		System.out.println(arr[1][1]);
		System.out.println(arr[2][1]);
	}
}
```

#### 两个思考题

1. java参数传递问题

```java
/*
	看程序写结果，并总结基本类型和引用类型参数的传递问题(题目在备注部分)
		基本类型：形式参数的改变对实际参数没有影响。
		引用类型：形式参数的改变直接影响实际参数。

	java中有没有引用传递?
		java中只有值传递。
		地址值也是一个值。
*/
class ArgsDemo {
	public static void main(String[] args){
		int a = 10;
		int b = 20;
		System.out.println("a:"+a+",b:"+b); //a:10,b:20
		change(a,b);
		System.out.println("a:"+a+",b:"+b); //a:?,b:?

		int[] arr = {1,2,3,4,5};
		change(arr);
		System.out.println(arr[1]); //?
	}

	public static void change(int a,int b)  //a=10,b=20
	{
		System.out.println("a:"+a+",b:"+b); //a:10,b:20
		a = b; //a=20;
		b = a + b; //b=40;
		System.out.println("a:"+a+",b:"+b); //a:20,b:40
	}

	public static void change(int[] arr) //arr = {1,2,3,4,5}
	{
		for(int x=0; x<arr.length; x++)
		{
			//如果是偶数，数据变为以前的2倍。
			if(arr[x]%2==0)
			{
				arr[x]*=2;
			}
		}

		//{1,4,3,8,5}
	}
}
```

​		java中只有值传递。因为地址值也是一个值。

2. 数据加密问题

   ```java
   /*
   	某个公司采用公用电话传递数据信息，数据是小于8位的整数，为了确保安全，
   	在传递过程中需要加密，加密规则如下：
   		首先将数据倒序，然后将每位数字都加上5，再用和除以10的余数代替该数字，
   		最后将第一位和最后一位数字交换。 请任意给定一个小于8位的整数，
   		然后，把加密后的结果在控制台打印出来。

   	分析：
   		A:数据是小于8位的整数
   			数据是变化的。(不以0开头)
   		B:加密规则
   			假设数据为：123456

   			首先将数据倒序
   				654321
   			然后将每位数字都加上5，再用和除以10的余数代替该数字
   				109876
   			最后将第一位和最后一位数字交换
   				609871
   		C:输出结果
   			609871
   */
   class JiaMiDemo{
   	public static void main(String[] args) {
   		//123456
   		//int[] arr = {1,2,3,4,5,6};

   		//定义数据
   		int number = 123456;

   		//定义数组
   		int[] arr = new int[8];

   		//取得一个数据的任意位上的值
   		//6,5,4,3,2,1
   		/*
   		arr[0] = number%10;
   		arr[1] = number/10%10;
   		arr[2] = number/10/10%10;
   		...
   		*/

   		//第一步
   		//定义一个索引变量
   		int index = 0;

   		while(number>0) {
   			arr[index]  = number%10; //arr[0]=6,arr[1]=5,arr[2]=4,arr[3]=3,arr[4]=2,arr[5]=1
   			number/=10; //number=12345,number=1234,number=123,number=12,number=1,number=0
   			index++; //index=1,index=2,index=3,index=4,index=5,index=6
   		}

   		for(int x=0; x<index; x++) {
   			System.out.print(arr[x]);
   		}
   		System.out.println();

   		//第二步
   		for(int x=0; x<index; x++) {
   			arr[x] += 5;
   			arr[x] %= 10;
   		}	

   		for(int x=0; x<index; x++) {
   			System.out.print(arr[x]);
   		}
   		System.out.println();

   		//第三步
   		int temp = arr[0];
   		arr[0] = arr[index-1];
   		arr[index-1] = temp;

   		for(int x=0; x<index; x++) {
   			System.out.print(arr[x]);
   		}
   		System.out.println();
   	}
   }
   ```

   ```java
   /*
   	A:把实现的代码改进为功能实现
   	B:键盘录入版
   */
   import java.util.Scanner;

   class JiaMiDemo2 {
   	public static void main(String[] args) {
   		//创建键盘录入对象
   		Scanner sc = new Scanner(System.in);

   		//键盘录入数据
   		System.out.println("请输入数据(小于8位的整数)：");
   		int number = sc.nextInt();

   		jiaMi(number);
   	}

   	public static void jiaMi(int number) {
   		int[] arr = new int[8];

   		//第一步
   		int index = 0;

   		while(number>0) {
   			arr[index++] = number%10;
   			number /= 10;
   		}

   		//第二步
   		for(int x=0; x<index; x++) {
   			arr[x] += 5;
   			arr[x] %= 10;
   		}

   		//第三步
   		int temp = arr[0];
   		arr[0] = arr[index-1];
   		arr[index-1] = temp;

   		//输出
   		for(int x=0; x<index; x++) {
   			System.out.print(arr[x]);
   		}
   		System.out.println();
   	}
   }
   ```

   ​

### DAY006

![](http://ovi3ob9p4.bkt.clouddn.com/xuexi/006DAY.jpg)

#### 面向对象：

​	面向对象是基于面向过程的编程思想

- 面向过程：自己一步步的完成操作，强调的是过程。
- 面向对象：调用别人的操作，强调的是结果。

1. 面向对象的思想特点：

		A:是一种更符合我们思想习惯的思想
	B:可以将复杂的事情简单化
	C:将我们从执行者变成了指挥者
		角色发生了转换

2. 举例：

A:洗衣服

- 面向过程：把盆子接水,放洗衣粉-->把衣服扔进去浸泡-->用手揉搓衣服-->漂洗衣服-->拧干-->拿衣架晾起来

- 面向对象：把衣服扔到洗衣机，放洗衣粉,按下启动即可-->拿衣架晾起来

  B:吃饭

- 面向过程：去超市买菜,买米-->洗菜,洗米-->切菜,做饭-->炒菜-->端菜,盛饭-->开吃

- 面向对象：去饭店-->调用服务员的记菜功能-->调用厨师的炒菜功能-->调用服务员的端菜功能-->开吃-->付账

  可以找一个对象帮我们做这些事情。

  C:买电脑
  面向过程：查阅资料-->坐公交-->到赛格电脑城-->各家比较-->选中自己喜爱的并讨价还价-->回家
  面向对象：查阅资料-->京东-->货到付账

  写代码举例：
  	需求：把大象装进冰箱
  	步骤：
  		A:打开冰箱门
  		B:塞进大象
  		C:关闭冰箱门


```java
A:面向过程
	a:打开冰箱门
	b:塞进大象
	c:关闭冰箱门

	代码：

	class Demo {
		public static void main(String[] args) {
			//System.out.println("打开冰箱门");
			//System.out.println("塞进大象");
			//System.out.println("关闭冰箱门");

			//可能打开冰箱门的操作需要做多次
			//并且，打开冰箱门这个功能的代码比较多
			//这个时候，其实我们应该用方法改进
			//调用功能
			open();
			in();
			close();

			//open();
			//open();
		}

		public static void open() {
			System.out.println("打开冰箱门");
		}

		public static void in(){
			System.out.println("塞进大象");
		}

		public static void close() {
			System.out.println("关闭冰箱门");
		}
	}

B:面向对象
	要想做到面向对象，请参照我的三句话：
		a:分析有哪些类存在
			UML(统一建模语言) 名词提取法
		b:分析每个类有哪些功能
		c:分析类与类的关系

	分析我们的问题：
		把大象装进冰箱

		a:分析有哪些类存在
			大象
			冰箱
			测试类(带main方法的那个类)
		b:分析每个类有哪些功能
			大象:进去
			冰箱:打开,关闭
			测试类:main
		c:分析类与类的关系
			在测试类中调用冰箱类和大象类的功能

	代码：
		class 大象 {
			public static void in(){
				System.out.println("塞进大象");
			}
		}

		class 冰箱 {
			public static void open() {
				System.out.println("打开冰箱门");
			}

			public static void close() {
				System.out.println("关闭冰箱门");
			}
		}

		class 测试类 {
			public static void main(String[] args) {
				冰箱的open();
				大象的in();
				冰箱的close();
			}
		}
```

**学完面向对象：**
	以后我们在完成一个需求的时候，请先找是否有对象完成了这个功能，有，我们就直接使用即可。
	如果没有，我们就自己定义一个类，完成功能，将来还可以给别人用。

#### 类与对象(掌握)

我们学习编程语言，是为了把现实世界的事物给表达出来，实现信息化处理。

我们要想通过编程语言来描述事物，首先要知道，事物是如何表达的：
	1. 事物：
		属性	该事物的描述信息(外在特征)
		行为	该事物能够做什么(内在行为)

我们学习的是java语言，而java语言最基本的单位是类。
所以，我们要把事物通过类来体现。
	2. 事物：
		属性	该事物的描述信息(外在特征)
		行为	该事物能够做什么(内在行为)

​	3. 类：
		成员变量	    该事物的描述信息(外在特征)
		成员方法	    该事物能够做什么(内在行为)

类：是一组相关的属性和行为的集合
对象：是该类事物的具体体现

举例：
	学生是类
	张三是对象

#### 类的组成(掌握)

​	(1)成员变量
		其实就是变量，只不过定义在类中，方法外，并且可以不用初始化。
	(2)成员方法
		其实就是方法，只不过不需要static了
	(3)案例：

```java
/*
	第一步：分析事物
		手机事物：
			属性：品牌，价格，颜色
			行为：打电话，发短信

	第二步：把事物转换为类
		手机类：
			成员变量：品牌，价格，颜色
			成员方法：打电话，发短信

	第三步：把类用英文体现
		Phone:
			成员变量：brand，price，color
			成员方法：call(String name)，sendMessage()

	第四步：写代码体现
		成员变量：其实就是一个变量，只不过定义在类中方法外，并且也可以不给初始化值。
		成员方法：其实就是一个方法，只不过不需要static了。
*/
//这是我的手机类
class Phone {
	//品牌
	String brand;
	//价格
	int price;
	//颜色
	String color;

	//打电话的方法
	public void call(String name) {
		System.out.println("给"+name+"打电话");
	}

	//发短信的方法
	public void sendMessage() {
		System.out.println("群发短信");
	}
}
```

#### 类的使用(掌握)

​	(1)创建对象
		格式：类名 对象名 = new 类名();
	(2)使用成员
		成员变量：对象名.变量名;
		成员方法：对象名.方法名(...);

#### 成员变量和局部变量的区别(理解)

​	

```java
/*
	成员变量和局部变量的区别：
		A:在类中的位置不同
			成员变量 类中方法外
			局部变量 方法内或者方法声明上
		B:在内存中的位置不同
			成员变量 堆内存
			局部变量 栈内存
		C:生命周期不同
			成员变量 随着对象的存在而存在，随着对象的消失而消失
			局部变量 随着方法的调用而存在，随着方法的调用完毕而消失
		D:初始化值不同
			成员变量 有默认的初始化值
			局部变量 没有默认的初始化值，必须先定义，赋值，才能使用。

		注意：
			如果有同名的变量，一般会采用就近原则。
*/
class VariableDemo {
	//成员变量
	int x;

	public static void main(String[] args) {
		//局部变量
		int y;
		//System.out.println(y);

		VariableDemo vd = new VariableDemo();
		System.out.println(vd.x);
	}
}
```



#### 形式参数问题(理解)

​	(1)基本类型
		基本类型作为形式参数，需要的是该基本类型的值。
	(2)引用类型
		引用类型作为形式参数，需要的是该引用类型的地址值。(对象)

```java
/*
	匿名对象：没有名字的对象。

	使用场景：
		A:调用方法,该方法仅仅被使用一次的时候适用。
		B:作为实际参数传递
*/

//定义学生类，写一个love方法
class Student  {
	public void love() {
		System.out.println("学生喜欢放假");
	}
}

class StudentDemo {
	public void test(Student s) {
		s.love();
	}
}

//测试类
class NoNameObject {
	public static void main(String[] args) {
		/*
		//创建对象
		Student s = new Student();
		s.love();
		s.love();

		//匿名对象
		new Student().love();
		new Student().love();
		*/

		//有名字的情况
		//StudentDemo sd = new StudentDemo();
		//Student s = new Student();
		//sd.test(s);

		//没有名字的情况
		//StudentDemo sd = new StudentDemo();
		//sd.test(new Student());

		//不妨在来一步
		new StudentDemo().test(new Student());
	}
}
```



#### 匿名对象(理解)

​	(1)匿名对象：没有名字的对象。是对象的简化书写方式。
	(2)使用场景
		A:调用方法，仅仅只调用一次
		B:作为实际参数传递

#### 封装(掌握)

​	(1)隐藏实现细节，提供公共的访问方式
	(2)好处：
		A:隐藏实现细节，提供公共的访问方式
		B:提高了代码的复用性
		C:提高了代码的安全性
	(3)使用原则
		A:把成员变量隐藏
		B:给出该成员变量对应的公共访问方式

#### private关键字(掌握)

​	(1)是一个权限修饰符
	(2)可以修饰类的成员(成员变量和成员方法)
	(3)仅仅在本类中可以访问
	(4)标准代码：
		

```java
		class Student {
			private String name;
			private int age;
		public void setName(String n) {
			name = n;
		}

		public String getName() {
			return name;
		}

		public void setAge(int a) {
			age = a;
		}

		public int getAge() {
			return age;
		}

		public void study() {}
	}
```

#### this关键字(掌握)

​	(1)this：代表本类的对象
	(2)应用场景：
		解决了局部变量隐藏成员变量的问题。
		其他用法和super一起讲。
	(3)标准代码：
		

```java
/*
	我们曾经说过，起名字，要做到见名知意，而现在的n和a都不是一个好的变量名称。

	由于变量在查找的时候，采用的是就近原则，所以，这个时候，就产生了问题。
	本来想给成员变量赋值的，确赋值给了局部变量。
	那么，我们该如何解决这个问题呢?
	java针对这种情况，就提供了一个关键字：this

	this：代表本类的对象

	应用场景：
		局部变量隐藏成员变量
*/
class Student {
	private String name;
	private int age;

	/*
	public void setName(String n) {
		name = n;
	}
	*/

	public void setName(String name) {  //"林青霞"
		this.name = name;
	}

	public String getName() {
		return name; //其实这里隐含了this
	}

	public void setAge(int age) {
		this.age = age;
	}

	public int getAge() {
		return age;
	}
}

class StudentDemo {
	public static void main(String[] args) {
		//创建对象
		Student s = new Student();
		//输出成员变量的值
		System.out.println(s.getName()+"---"+s.getAge());

		//给成员变量赋值
		s.setName("林青霞");
		s.setAge(28);

		//再次输出成员变量的值
		System.out.println(s.getName()+"---"+s.getAge());
	}	
}
```
