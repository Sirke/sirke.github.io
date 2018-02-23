---
title: Java成神之路-JavaScript（三）
tags: Java
category: Java
date: 2018-02-23 11:44:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0128.jpg)

Java成神之路-JavaScript
<!--more-->
# JavaScript

## 基本语法

### 分类

ECMAScript  js基本语法与标准
DOM         Document Object Model文档对象模型
BOM         Browser Object Model浏览器对象模型

tips：DOM和BOM都是一套API（Application programing interface）

### 注释方式

```
style   /*  */
body    <!-- --!>
script  //
        /* */
        /**
        *   js说明文档注释
        */
```

### 简单指令

```
alert("");          提示框；
confirm("");        确认框，点击后会响应返回true或false；             
prompt();           弹出一个输入框；
document.write("");
console.log("");    在控制台打印相应的信息；
console.dir("");    在控制台打印出该对象的所有信息；
```

### 变量命名

数字（0-9）、字母（a-z，A-Z）、下划线（_）；

tips:应避免保留字和关键字；

### NaN和isNaN

isNaN(number),如果number不是数字，则为true；
Number(number),在转换为数字类型时，若number不是数字，则返回NaN；

### 转义字符

```
\       
\r  回车
\n  空格
\t  缩进
\\  反斜杠
```

### 逻辑短路、逻辑中断

```
true || 6;      逻辑或短路，左边为ture返回右值；
6   &&  true;   逻辑与短路，左边false返回右值；
```

### 优先级

```
    * / %
    +   -
    &&
    ||
    ?
tips：自上而下优先级越来越高
```

### 类型转换（type）

```
parseInt("12a3");   转为数字，尝试强转；
parseFloat("123.123");

data.toString();
String(data);

tips:变量声明未赋值，其值为undefined；
        对象为空，其值为null；

```

### 三元表达式

```
eg  :   a>b?a=1:a=2;

格式:
    判断条件？true的时候执行的操作：false的时候执行的操作；
```

### 数组Array

```
（1）、定义法
    构造函数：
            var arr = new Array("123","abc","xxx");
    字面量：
            var arr = ["123","646","abc"]; 
    数组长度：
            var arr = new Array(6);(数组长度为6)；
（2）、赋值
    arr[0]=1;
```

### 形参和实参

```
定义函数时，function funcA(a,b,c){}，其中的a、b、c即为形参；
调用函数时，funcA(1,2,3);其中的1、2、3即为实参；

tips：function里面有一个arguments对象，里面存有所有传进函数的实参；
```

### 函数function

```
（1）、函数命名
    1、  可以使用字符、数字、下划线、$；
    2、  不能以数字开头；
    3、  不能使用关键字和保留字；
    4、  区分大小写；
    5、  建议要有意义 --  动词+名字结构；
    6、  驼峰命名法；
    7、  函数名不能重名，后面写的重名函数会把前面写的函数给覆盖掉；

（2）、函数的返回值
返回值：
    当函数执行完毕之后，所得到的结果就是一个函数返回值
    任意函数都有返回值

1、  在函数内部没有显示的写有return的时候，函数的返回值是undefined；
2、  当函数内部有return，但是return后面没有跟着任何内容或者数据的时候，
函数的返回值是undefined，并且return后面的代码不会执行；
3、  当return后面跟着内容或者数据的时候，函数的返回值就是这个跟着的内容或者数据；


（3）、函数的四种形式：
    1、没有参数，没有return；
            通常在于封装一段过程；
    2、没有参数，有return；
            通常用于内部封装引用其他函数（闭包，回调）；
    3、有参数，没有return；
            通常用于执行操作的封装；
    4、有参数，有return；
            常见形式；

（4）、匿名函数
    匿名函数的name属性值为anonymous；
    函数仅用一次的情况，即用即废；

    eg:
        setTimeout(function(){
            console.log(this.name);
        },1000);
    tips:在1秒后在控制台打印出本函数的名称；

（5）、回调函数
    在一个函数当中，另一个函数作为参数传入该函数中，另一个的这个函数即为回调函数；
    eg:
        function atack(callback){
            return callback;
        }
    tips:在调用该函数时，指定callback是哪个函数；
        atack（func）；

（6）、短路运算
    作用：防止传入函数的数据不足，造成无法运行；
    eg：
        function getResult(a,b,fn) {
            fn && fn();
        }（通常使用逻辑与的短路来决定是否执行回调函数；）

        function getResult_2(a,b){
            a || 0;
        }（通常用逻辑或的短路来防止实参不足的情况，强行赋值；）

（7）、自执行函数
    （function func2(){

    }）()

    tips:在函数定义的结束最后写入一个（），该函数定义完成后直接被调用执行；

（8）、递归
    在函数执行的最后再一次的调用自身；

    tips:递归是一种非常耗资源的做法，通常为了简化运算，还会结合缓存进行；
    并且注意，递归必须要有结束判断条件（if），否则该函数被调用后就是死循环；
```

### 数据类型

```
（1）、简单数据类型
    string、number、boolean

（2）、复杂数据类型
    String、Number、Boolean、Array、Math、Date、Obeject、function、RegExp(正则表达式)

（3）、空数据类型
    * Null  ---→Null的数据类型会返回一个Object
    * undifined

    tips：用typeof可以进行判断数据类型；

    tips：定义的简单数据类型变量，其数据保存在变量中；
        而复杂数据类型，其变量保存的是数据所在的内存地址；
```

### 内置对象

```
Array、Date、Math、String；
```

### （Math）数学对象

```
向上取整        Math.ceil(number);
向下取整        Math.floor(number);
四舍五入        Math.round(number);

求多个数字之间的最大值     Math.max();
求多个数字之间的最小值     Math.min();

求x的y次幂      Math.pow(x,y);

求正弦值            Math.sin(x);
    example:
        求一个角度的正弦值，要求x必须是一个额弧度值
        角度和弧度的转换公式：
            弧度 = 角度 * 2 * Math.PI / 360;

        Math.sin(30*2*Math.PI/360)

Math.abs(x);    得到一个数字的绝对值

```

### （Array）数组对象

```
（1）、arr1.concat(arr2);
        数组拼接，结果为将arr2拼接到arr1的最后；

（2）、arr.join()；
        数组字符串输出，括号内可以指定元素连接的符号；
        eg:
            arr=["a","b","c","d"];
            console.log(arr.join("|"));     (结果为"a|b|c|d")

（3）、arr.pop();
        切除数组的最后一个元素，返回值为该元素；

（4）、arr.slice(start,end)
        获取，获取数组的指定片段，start必须有，如果参数为负数则从末尾开始选取；
        返回值为该片段组成的，一个新的数组；

（5）、arr.push
        添加，用于向数组的末尾添加新的元素，参数可以是多个；
        返回值为数组的新长度；

（6）、arr.splice
        1、用于向数组中指定的索引添加元素；
            arr.splice(2, 0, "William","asdfasdf");
                在第2个元素开始，删除的元素个数（可以为0，为0到结尾），
                加入元素为"William"、"asdfasdf"；

        2、用于替换数组中的元素；
            arr.splice(2,1,"William")；          

        3、用于删除数组中的元素；
             arr.splice(2,2);

（7）、arr.indexOf(element);
        查找，在数组中查找element，返回值为索引，如果没有该元素返回-1；

（8）、arr.sort(function);
        排序，function为一个函数；
            eg:
                function sortNumber(a,b){
                    return a-b;
                }
                arr.sort(sortNumber);(从小到大排序)

    tips：如果a-b改成b-a，那么执行的操作为从大到小；
    tips:字符串对象（String）的方法与Array的方法类似；

```

### （Date）日期对象

```
date.getTime()
date.getMilliseconds()
date.getSeconds()
date.getMinutes()
date.getHours()
date.getDay()
date.getDate()
date.getMonth()
date.getFullYear()

tips:很多，查文档

```

### （String）对象

```
charAt(index)
str[index]          获取字符串指定位置的字符

concat()        拼接字符串
---------------------------
slice(start,end)/
substring(start,end)    截取从start开始，end结束的字符，
                返回一个新的字符串，若start为负数，那么从最后一个字符开始；

substr(start,length)    截取从start开始，length长度的字符，得到一个新的的字符串
---------------------------

indexOf(char)       获取指定字符第一次在字符串中的位置
lastIndexOf(char)   获取指定字符最后一次出现在字符串中的位置

trim()      去除字符串前后的空白
---------------------------
toUpperCase()
toLocaleUpperCase()     转换为大写

toLowerCase()
toLocaleLowerCawse()    转换为小写
---------------------------

replace()       替换字符
split()         分割字符串为数组

```

### 自定义对象

```
对象：无序属性的集合；
    特征：属性（key）；
    行为：方法（value）；

js是基于对象的弱类型语言；

继承：基于类，子类可以从父类得到的特征；    

工厂模式：定义一个function构造函数，作为对象，要创建对象直接调用该构造函数，加new关键字；

构造函数：定义对象的函数，里面存有该对象拥有的基本属性和方法；
    命名首字母大写，this会自动指代当前对象；

访问对象属性：
    obj[key];
    obj.key;

遍历对象：
    for(key in obj){
        key         为属性名；
        obj[key]    为属性值（value）；
    }

```

### JSON

```
{
   "name" : "李狗蛋",
   "age" : 18,
   "color" : "yellow"
}

1、  所有的属性名，必须使用双引号包起来；
2、  字面量侧重的描述对象，JSON侧重于数据传输；
3、  JSON不支持undefined；
4、  JSON不是对象，从服务器发来的json一般是字符串，
通过JSON.parse(jsonDate.json)可以将其转换成js对象；

```

### JS解析

```
（1）、作用域
全局作用域：整个代码所有地方都可以调用；
局部作用域：在函数内部声明的变量，只可以在函数内部使用；

（2）、变量提升和函数提升
预解析：在解析的时候，var和function都会被提升到代码的最顶端；
    但是赋值操作不会被提升，定义和函数才会被提升；
    if里面的变量定义也会被提升，但是赋值操作不会；

```

### 其他细节（tips）

```
(1)、元素由对象组成的数组进行排序
    eg：
        var data = [
            {title: "老司机", count: 20},
            {title: "诗人", count: 5},
            {title: "歌手", count: 10},
            {title: "隔壁老王", count: 30},
            {title: "水手", count: 7},
            {title: "葫芦娃", count: 6},
        ];
            //该数组的元素都为对象。我们需求为根据count的值给数组重新排序。
            //解决方案：使用sort方法，对传入的函数做手脚。

        function sortArr(a,b){
            return a.count > b.count;   
        }
        data.sort(sortArr);

            //原本的a和b的比较方法变成a.count和b.count；
            //原本的比较方法可以参见17，数组对象
            //至此，data将以count值从小到大排列。

    tips:Array对象的sort方法传入的为比较函数，比较函数里return排序比较的方法；
        原始的sort方法传入的函数内部return的值为a>b，
        通过修改sort传入的函数，可以实现对元素为对象的数组的排序！
```

## JavaScript的内部对象

按创建方式不同分为：使用变量声明的隐性对象，使用new创建的显性对象

### 隐性对象

在赋值和声明后就是一个隐性对象，隐性对象不支持prototype属性，也无法随意扩展对象属性。

### 显性对象

显性对象支持prototype属性，支持新建对象属性。

### JavaScript提供了十一种内部对象

**Boolean对象**

Boolean对象是一种数据类型，提供构造函数可以创建布尔数据类型的对象

objboolean=new Boolean();

**Funcation对象**

JavaScript函数就是一个funcation对象，Funcation对象是函数，如果函数有参数，这些传入的参数都是argument对象

**Global对象**

Global对象不能使用new来创建，在脚本语言初始化时会自动创建此对象。

**Number对象**

Number对象，用于创建数值类型的变量

**Object对象**

使用Object对象创建自定义对象

**RegExp对象**

JavaScript的正则表达式对象

5-2JavaScript的string对象

### 创建string对象

var obj="javascript";或var obj2=new string("JavaScript");两种方式

#### string对象提供了一系列的格式编排方法

####String 对象方法

方法 描述

anchor() 创建 HTML 锚。

big() 用大号字体显示字符串。

blink() 显示闪动字符串。

bold() 使用粗体显示字符串。

fixed() 以打字机文本显示字符串。返回<tt>string</tt>中内容

fontcolor() 使用指定的颜色来显示字符串。

fontsize() 使用指定的尺寸来显示字符串。

fromCharCode() 从字符编码创建一个字符串。

link() 将字符串显示为链接。

italics() 使用斜体显示字符串。

localeCompare() 用本地特定的顺序来比较两个字符串。

slice() 提取字符串的片断，并在新的字符串中返回被提取的部分。

small() 使用小字号来显示字符串。

strike() 使用删除线来显示字符串。

sub() 把字符串显示为下标。

sup() 把字符串显示为上标。

toSource() 代表对象的源代码。

toString() 返回字符串。

valueOf() 返回某个字符串对象的原始值。


```
 <script  type ="text/javascript">
        var obj = "JavaScript程序设计";
        document.write("anchor():" + obj.anchor() + "<br/>");
        document.write("big():" + obj.big() + "<br/>");
        document.write("blink():" + obj.blink() + "<br/>");
        document.write("bold():" + obj.bold() + "<br/>");
        document.write("fixed():" + obj.fixed() + "<br/>");
        document.write("fontcolor(red):" + obj.fontcolor("red") + "<br/>");
        document.write("fontsize(6):" + obj.fontsize(6) + "<br/>");
        document.write("italics()" + obj.italics() + "<br/>");
        document.write("link()" + obj.link("https://home.cnblogs.com/u/cyjy/") + "<br/>");
        document.write("small()" + obj.small() + "<br/>");
        document.write("strike():" + obj.strike() + "<br/>");
        document.write("sub():" + obj.sub() + "<br/>");
        document.write("sup():" + obj.sup() + "<br/>");
        
    </script>
```

![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222144134882-756115220.png)

#### 字符串的长度与大小写

length属性是用于获取字符串的长度

toLocaleLowerCase() 把字符串转换为小写。

toLocaleUpperCase() 把字符串转换为大写。

toLowerCase() 把字符串转换为小写。

toUpperCase() 把字符串转换为大写。



```
<script  type ="text/javascript">
         var obj = "JavaScript";
         var obj2 = new String("程序设计");
         document.write("英文测试字符串：" + obj  + "<br/>");
         document.write("中文测试字符串：" + obj2 + "<br/>");
         document.write("英文测试字符串length：" + obj.length + "<br/>");
         document.write("中文测试字符串length：" + obj2.length+ "<br/>");
         document.write("英文测试字符串小写：" + obj.toLowerCase() + "<br/>");
         document.write("英文测试字符串大写：" + obj.toUpperCase() + "<br/>");
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222145606601-1803819854.png)

#### **获取字符串的指定字符**

charAt(index) 返回在指定位置的字符。

charCodeAt(index) 返回在指定的位置的字符的 Unicode 编码。



```
<script  type ="text/javascript">
         var obj = "JavaScript";
         var obj2 = new String("程序设计");
         document.write("英文测试字符串：" + obj + "<br/>");
         document.write("中文测试字符串：" + obj2 + "<br/>");
         document.write("英文测试字符串.charAt(4)：" + obj.charAt(4) + "<br/>");
         document.write("英文测试字符串charCodeAt(4)：" + obj.charCodeAt(4) + "<br/>");
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222145959945-2050085451.png)

#### **子字符串的搜索**

indexOf(string,index) 检索字符串。返回第一次找到字符串的索引位置，没有找到返回-1，传入的string是要搜索的参数，index为要搜索的索引位置

lastIndexOf(string) 从后向前搜索字符串。

match(string) 找到一个或多个正则表达式的匹配。没有找到返回null

search(string) 检索与正则表达式相匹配的值。

 



```
<script  type ="text/javascript">
        var obj = "JavaScript";
        var obj2 = new String("程序设计");
        document.write("英文测试字符串indexOf('a')：" + obj.indexOf('a') + "<br/>");
        document.write("英文测试字符串indexOf('a',2)：" + obj.indexOf('a',2) + "<br/>");
        document.write("中文测试字符串.indexOf('程序')：" + obj2.indexOf('程序') + "<br/>");
        document.write("英文测试字符串.lastIndexOf('a') ：" + obj.lastIndexOf('a') + "<br/>");
        document.write("英文测试字符串.match('Java')：" + obj.match('Java') + "<br/>");
        document.write("中文测试字符串.match('程序')：" + obj2.match('程序') + "<br/>");
        document.write("英文测试字符串.search('Java')：" + obj.search('Java') + "<br/>");
        document.write("中文测试字符串.search('学校')：" + obj2.search('学校') + "<br/>");
    </script>
```

![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222152320148-611445502.png)

#### 子字符串的处理

replace(string1，string2) 替换与正则表达式匹配的子串。将string1换成string2

split() 把字符串分割为字符串数组。返回数组对象。

 substr(index,length) 从起始索引号提取字符串中指定数目的字符。从index开始取出length个字符串

substring(index1，index2) 提取字符串中两个指定的索引号之间的字符。

concat(string) 连接字符串。将string字符串添加到string对象的字符串之后.



```
 <script  type ="text/javascript">
        var obj = "JavaScript";
        var obj2 = new String("程序设计");
        document.write("英文测试字符串：" + obj + "<br/>");
        document.write("中文测试字符串：" + obj2 + "<br/>");
        document.write("英文测试字符串.replace('Script', '')" + obj.replace('Script', '') + "<br/>");
        document.write("中文测试字符串.split('序')" + obj2.split('序') + "<br/>");
        document.write("英文测试字符串.substr(2,4)" + obj.substr(2, 4) + "<br/>");
        document.write("英文测试字符串obj2.substring(2,5)" + obj2.substring(2, 5) + "<br/>");
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222153835195-446460131.png)

将12/5/2012变为2012-5-12；

 var obj = "12/5/2012";          
​      var obj = obj.replace(/\//g,"-"); 
  var obj2=obj.replace(/(\d{2})-(\d{1}|\d{2})-(\d{4})/g,'$3-$2-$1');
​      alert(obj2); 

 

 

#### **JavaScript的Array对象**

 JavaScript数据类型中没有数组，而是使用Array对象来创建数组，每一个数组元素事实上就是Array对象的属性。

创建一维数组

 new Array();

new Array(*size*);

new Array(element0, element1, ..., elementn);



```
<script  type ="text/javascript">
        var arr = new Array(1,2,3,4);
        var arr2 = new Array(3);
        arr2[0] = "one";
        arr2[1] = "two";
        arr2[2] = "three";
        //用循环显示数组值
        for (var i = 0; i <=arr.length; i++)
        {
            document.write(arr[i] + "<br/>");
        }
        for (var i = 0; i <3; i++) {
            document.write(arr2[i] + "<br/>");
        }
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222155826616-1708664414.png)

 

### **Array对象的属性与方法**

length属性获取数组长度

方法 描述
concat(arry)	连接两个或更多的数组，并返回结果。将参数合并到当前的数组中
join()	把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。

pop() 删除并返回数组的最后一个元素
push()	向数组的末尾添加一个或更多元素，并返回新的长度。
shift()	删除并返回数组的第一个元素
slice()	从某个已有的数组返回选定的元素
splice()	删除元素，并向数组添加新元素。
toSource()	返回该对象的源代码。
toString()	把数组转换为字符串，并返回结果。
reverse() 颠倒数组中元素的顺序。*sort*(arry)将数组的所有元素排序**

```
<script  type ="text/javascript">
        var arr = new Array(1,2,3,4);
        var arr2 = new Array(3);
        arr2[0] = "one";
        arr2[1] = "two";
        arr2[2] = "three";
        function showarr(arr) {
            for (var i = 0; i < arr.length; i++) {
                document.write(arr[i] + ",");

            }
        }
        document.write("数组长" + arr2.length + "<br/>");
        document.write(arr2.join() + "<br/>");
        arr2.reverse();//反转数组
        document.write("<br/>");
        showarr(arr);
        document.write("<br/>");
        arr = arr.concat(arr2);//连接两个数组
        showarr(arr);
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222162535820-755406468.png)

**JavaScript的多维数组**



```
<script  type ="text/javascript">
          var arr = new Array(3);
          for (var i = 0; i < 3; i++)
          {
              arr[i] = new Array(2);
          }
          arr[0][0] = "1";
          arr[0][1] = "2";
          arr[1][0] = "3";
          arr[1][1] = "4";
          arr[2][0] = "5";
          arr[2][1] = "6";
          for (var j= 0; j< arr.length;j++)
          {
              for (i = 0; i < arr[i].length; i++) {
                  document.write(arr[j][i]);
              }
                  document.write("<br/>");
              
          }
    </script>
```



![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222163949507-2080988031.png)

#### **JavaScript的Date对象**

Date对象可以获取计算机的系统时间和日期，并且提供相关的方法将它转化为所需的日期数据。

创建Date对象

var youDate=new Date()

Date 对象会自动把当前日期和时间保存为其初始值。

Date() 返回当日的日期和时间。
getDate()	从 Date 对象返回一个月中的某一天 (1 ~ 31)。
getDay()	从 Date 对象返回一周中的某一天 (0 ~ 6)，也就是星期日到星期六。
getMonth()	从 Date 对象返回月份 (0 ~ 11)。
getFullYear()	从 Date 对象以四位数字返回年份。
getYear()	请使用 getFullYear() 方法代替。
getHours()	返回 Date 对象的小时 (0 ~ 23)。
getMinutes()	返回 Date 对象的分钟 (0 ~ 59)。
getSeconds()	返回 Date 对象的秒数 (0 ~ 59)。
getMilliseconds()	返回 Date 对象的毫秒(0 ~ 999)。
getTime()	返回 1970 年 1 月 1 日至今的毫秒数。

```
<script  type ="text/javascript">
        var youDate = new Date();
        document.write("系统日期：" + youDate.getDate());
        document.write("<br/>");
        document.write("系统时间：" + youDate.getHours() + ":" + youDate.getMinutes()+":"+youDate.getSeconds());
    </script>
```

![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222165139788-1213666040.png)

**设置时间和日期**

setDate() 设置 Date 对象中月的某一天 (1 ~ 31)。
setMonth()	设置 Date 对象中月份 (0 ~ 11)。
setFullYear()	设置 Date 对象中的年份（四位数字）。
setYear()	请使用 setFullYear() 方法代替。
setHours()	设置 Date 对象中的小时 (0 ~ 23)。
setMinutes()	设置 Date 对象中的分钟 (0 ~ 59)。
setSeconds()	设置 Date 对象中的秒钟 (0 ~ 59)。
setMilliseconds()	设置 Date 对象中的毫秒 (0 ~ 999)。
setTime()	以毫秒设置 Date 对象。

 JavaScript的Date对象可以获取系统时间，只需定时执行JavaScript函数就可以建立一个网页时钟，同时需要使用setTimeout（），参数中可以设置间隔多少时间来执行函数，clearTimeout（）可以清除定时器

#### **JavaScript的Math对象**

Math对象不同于其他JavaScript对象，Math对象是由脚本语言引擎所创建的，不需要使用new来创建。

max(x,y) 返回 x 和 y 中的最高值。
min(x,y)	返回 x 和 y 中的最低值。
pow(x,y)	返回 x 的 y 次幂。
random()	返回 0 ~ 1 之间的随机数。

需要获得更大的随机数乘以相关的倍数就可以了

```
<script  type ="text/javascript">
        var num = Math.round(Math.random() * 100);
        document.write("0~100之间的随机数"+num);
    </script>
```

![img](https://images2015.cnblogs.com/blog/1029626/201702/1029626-20170222171339913-1190372691.png)

**JavaScript的Error对象**

try catch finally处理例外。

**JavaScript对象的共享属性和方法**

属性 constructor属性可以获取创建对象使用的构造函数的函数名称

tostring（）方法和value（）可以显示对象的内容。
