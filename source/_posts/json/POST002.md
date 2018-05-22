---
title: JSON.stringify()&JSON.parse()的使用

category: JSON
date: 2018-04-20 20:30:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0176.jpg)
JSON.stringify()&JSON.parse()

<!--more-->

#### 两者对比JSON.stringify()&JSON.parse()

| 对比 | .stringify()                                 | .parse()                    |
| ---- | -------------------------------------------- | --------------------------- |
| 定义 | json对象->字符串                             | 字符串->json对象            |
| 语法 | JSON.stringify(value [, replacer] [, space]) | JSON.parse(text[, reviver]) |

##### parse用于从一个字符串中解析出json对象

如

```js
var str = '{"name":"huangxiaojian","age":"23"}'
```

结果：

```js
JSON.parse(str)
```

```
Object

1. age: "23"
2. name: "huangxiaojian"
3. proto: Object
```

注意：单引号写在{}外，每个属性名都必须用双引号，否则会抛出异常。

##### stringify()用于从一个对象解析出字符串

如

```js
var a = {a:1,b:2}
```

结果：

```js
JSON.stringify(a)
```

```
"{"a":1,"b":2}"
```

#### JSON.stringify()

##### JSON.stringify(value）

对象转化为字符串输出

```js
var data = [
    {name: "1", sex:1, age: 1},
    {name: "2", sex:0, age: 2},
    {name: "3", sex:1, age: 3}
];
console.log(JSON.stringify(data));
```

```json
[{"name":"1","sex":1,"age":1},{"name":"2","sex":0,"age":2},{"name":"3","sex":1,"age":3,"info":{"sex":"male"}}]
```

##### JSON.stringify(value [, replacer]）

输出部分数据

```js
var data = [
    {name: "1", sex:1, age: 1},
    {name: "2", sex:0, age: 2},
    {name: "3", sex:1, age: 3}
];
console.log( JSON.stringify(data, ["name", "sex"]));
```

```json
[{"name":"1","sex":1},{"name":"2","sex":0},{"name":"3","sex":1}]
```

##### JSON.stringify(value [, replacer][, space])

```js
var data = [
    {name: "1", sex:1, age: 1},
    {name: "2", sex:0, age: 2},
    {name: "3", sex:1, age: 3,info:{sex:'male',getSex:function(){return 'sex';}}}
];

var censor = function(key,value){
    if(typeof(value) == 'function'){
         return Function.prototype.toString.call(value)
    }
    return value;
}
console.log(JSON.stringify(data,censor,4))
```

```json
[
    {
        "name": "1",
        "sex": 1,
        "age": 1
    },
    {
        "name": "2",
        "sex": 0,
        "age": 2
    },
    {
        "name": "3",
        "sex": 1,
        "age": 3,
        "info": {
            "sex": "male",
            "getSex": "function (){return 'sex';}"
        }
    }
]
```

#### JSON.parse()

##### JSON.parse(text)

```javascript
var data = '[{"name":"1","sex":1,"age":1},{"name":"2","sex":0,"age":2},{"name":"3","sex":1,"age":3}]';
JSON.parse(data);
```

![这里写图片描述](https://img-blog.csdn.net/20170306112338483?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcGFta2k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

##### JSON.parse(text[, reviver])

```javascript
var data = '[{"name":"1","sex":1,"age":1},{"name":"2","sex":0,"age":2},{"name":"3","sex":1,"age":3}]';
var str_json = JSON.stringify(JSON.parse(data), function (k, v) {
    if (k === "sex") {
        return ["女", "男"][v];
    }
    return v;
});//sex 0,1->女，男
JSON.parse(str_json);
```

![这里写图片描述](https://img-blog.csdn.net/20170306113357371?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcGFta2k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

#### jQ操作json

##### .serialize()方法

```javascript
格式：var data = $("#formID").serialize();
功能：将表单内容序列化成一个以&拼接的字符串，键值对的形式，name1=val1&name2=val2&，空格以%20替换。
```

![这里写图片描述](https://img-blog.csdn.net/20170306115534358?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcGFta2k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

##### .serializeArray()方法

```javascript
格式：var jsonData = $("#formID").serializeArray();
功能：将页面表单序列化成一个JSON结构的对象。注意不是JSON字符串。
```

　![这里写图片描述](https://img-blog.csdn.net/20170306133919438?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcGFta2k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

##### .$.param()方法

```javascript
格式：var string = $("#formID").param();
功能：可以把json格式数据序列化成字符串形
```

```javascript
     var obj={a:1,b:2};
     $.param(obj);
```

```javascript
"a=1&b=2"
```

##### 自定义方法.serializeJson()

```javascript
格式：var jsonData = $("#formID").serializeJson();
功能：serializeArray()方法的扩展，格式转换为键值对name：val。

$.fn.serializeJson= function()
{
    var o = {};
    var a = this.serializeArray();
    $.each(a, function(){
        if(o[this.name]){
            if(!o[this.name].push){
                o[this.name] = [o[this.name]];
            }
            o[this.name].push(this.value ||'');
        } else {
            o[this.name] = this.value || '';
        }
    });
    return o;
};
```

![这里写图片描述](https://img-blog.csdn.net/20170306135113350?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcGFta2k=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
