---
title: Java成神之路-Java异常处理、集合框架（六）
tags: Java
category: Java
date: 2018-02-23 14:44:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0131.jpg)

Java成神之路-Java异常处理、集合框架
<!--more-->
# Java异常处理

## 一、异常概述

异常：Exception，是在运行发生的不正常情况。

原始异常处理：

代码阅读性差，臃肿不堪，与正常流程代码结合的很紧密，所以，在JAVA中进行一系列的改良，将一系列常见的问题，用面向对象的思考方式，对其进行了描述、封装。

在JAVA中，用类的形式对不正常情况进行了描述和封装对象。当程序出现问题时，调用相应的处理办法。

描述不正常情况的类，就称为异常类。将流程代码和异常代码进行分离。

异常就是JAVA通过面向对象的思想，将问题封装成了对象。用异常类对其进行描述。不同的问题，用不同的类进行描述。那么意味着，问题有多少，类就有多少。

## 二、异常体系

问题很多，意味着描述的类也很多，将其共性进行向上抽取，就形成了异常体系。最终异常分为两大类：

Throwable（父类）：问题发生，就应该抛出，让调用者处理。该体系的特点就在于Throwable及其子类都具有可抛性。

　　两个关键字实现可抛性：throws、throw

　　|--1.一般不可处理的。Error（错误）

　　　　特点：是由JVM（java虚拟机）抛出的严重性的问题。这种问题发生，一般不针对性处理，直接修改程序。

　　|--2.可以处理的。Exception（异常）

 　　　　特点：子类的后缀名都是用其父类名作为后缀，阅读性很强。

## 三、异常-原理&异常对象的抛出throw

可以看出，异常时，底层throw直接调用异常方法，抛出异常，只不过这些都在底层完成，我们看不到而已。

JAVA虚拟机它有一套异常处理机制，就是会把异常的各种信息，位置等报出来，以供解决异常。

真正开发的时候，这些异常信息是不会直接报出来的，会存成日志，我们定期查看。而且这个异常信息给用户也没用，只有给我们才有用。

## 四、异常-自定义异常&异常类的抛出throws

自定义异常：JAVA给出的一堆现有的异常没有我们需要的，这时候可以自定义了。但是这个类一定要继承Exception类。

## 五、异常-编译时检测异常和运行时异常的区别&throw和throws的区别

Exception体系分两种：
1.一种是编译时被检测异常（throws）。除runtimeException子类的所有子类。这样的问题可以针对性的处理。

2.运行时异常（throw）。Exception的子类中runtimeException和其子类。这种问题一般不处理，直接编译通过，在运行时让调用时的程序强制停止。

## 六、异常-异常捕捉try-catch

异常处理的捕捉形式：具体格式：

建立日志文件：第三方插件-log4j

## 七、异常-多catch情况

一个try对应多个catch的时候，小细节：

当多catch需要存在catch(Exception e)的时候，需要放到最后，不然会挂，因为Exception为父类，能接收所有的异常，放它之后，其他的就多余了，所以，它要放在最后的catch。

## 八、异常-异常处理原则

异常就是问题，JAVA对一些常见的问题已经弄好了，拿来用就好了。

如果，个别问题只在你自己的项目里出现，并且JAVA里没有这类问题，那就需要自己描述该问题。

1.方法内如果抛出需要检测的异常，那么方法上必须要声明，否则必须在方法内用try-catch捕捉，否则编译失败。

2.如果调用了声明异常的函数，要么try-catch要么throws，否则编译失败。

3.什么时候catch，什么时候throws？功能内容可以解决，用catch，解决不了，用throws告诉调用者，有调用者解决。

4.如果一个功能抛出了多个异常，那么调用时必须有对应多个catch进行针对性的处理。

## 九、异常-finally代码块

finally为一定会执行的代码，只有一种情况，finally不会执行。

try-catch-finally代码块组合特点：

1.try-catch-finally常见组合体

2.try-catch(可以多个catch)没有finally，没有资源需要释放（关闭），可以不用finally。

3.try-finally，没有catch时，方法旁边需要throws声明，因为没catch没处理。异常无法直接catch处理，但是资源需要关闭，这时用此组合。

## 十、异常的注意事项

1.子类在覆盖父类方法时，父类的方法如果抛出了异常，那么子类的方法只能抛出父类的异常或者该异常的子类。

 2.如果父类抛出多个异常，那么子类只能抛出父类异常的子集。----子类覆盖父类只能抛出父类异常或者子类或者子集。如果父类的方法没有抛出异常，那么子类覆盖时绝对不能抛，只能try。

 

常用异常方法：

Error类的常见子类：

![img](http://ovi3ob9p4.bkt.clouddn.com/Java/error.png)

 Exception类的常见子类：

![img](http://ovi3ob9p4.bkt.clouddn.com/Java/Exception.png)

RuntimeException类的常见的子类：

![img](http://ovi3ob9p4.bkt.clouddn.com/Java/RuntimeException.png)

# JAVA集合类汇总

## 一、集合与数组

数组（可以存储基本数据类型）是用来存现对象的一种容器，但是数组的长度固定，不适合在对象数量未知的情况下使用。

集合（只能存储对象，对象类型可以不一样）的长度可变，可在多数情况下使用。

## 二、层次关系

Collection接口是集合类的根接口，Java中没有提供这个接口的直接的实现类。但是却让其被继承产生了两个接口，就是Set和List。

1. Set中不能包含重复的元素。
2. List是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式。

Map是Java.util包中的另一个接口，它和Collection接口没有关系，是相互独立的，但是都属于集合类的一部分。Map包含了key-value对。Map不能包含重复的key，但是可以包含相同的value。

3. Iterator，所有的集合类，都实现了Iterator接口，这是一个用于遍历集合中元素的接口，主要包含以下三种方法：

* hasNext()是否还有下一个元素。
* next()返回下一个元素。
* remove()删除当前元素。

## 三、几种重要的接口和类简介

1. List（有序、可重复）

List里存放的对象是有序的，同时也是可以重复的，List关注的是索引，拥有一系列和索引相关的方法，查询速度快。因为往list集合里插入或删除数据时，会伴随着后面数据的移动，所有插入删除数据速度慢。

2. Set（无序、不能重复）

Set里存放的对象是无序，不能重复的，集合中的对象不按特定的方式排序，只是简单地把对象加入集合中。

3. Map（键值对、键唯一、值不唯一）

Map集合中存储的是键值对，键不能重复，值可以重复。根据键得到值，对map集合遍历时先得到键的set集合，对set集合进行遍历，得到相应的值。

对比如下：

|            |             | 是否有序           | 是否允许元素重复                                          |
| ---------- | ----------- | ------------------ | --------------------------------------------------------- |
| Collection |             |                    |                                                           |
| List       | 是          | 是                 |                                                           |
| Set        | AbstractSet | 否                 | 否                                                        |
|            | HashSet     |                    |                                                           |
|            | TreeSet     | 是（用二叉排序树） |                                                           |
| Map        | AbstractMap | 否                 | 使用key-value来映射和存储数据，key必须唯一，value可以重复 |
|            | HashMap     |                    |                                                           |
|            | TreeMap     | 是（用二叉排序树） |                                                           |

 

## 四、遍历

 在类集中提供了以下四种的常见输出方式：

1）Iterator：迭代输出，是使用最多的输出方式。

2）ListIterator：是Iterator的子接口，专门用于输出List中的内容。

3）foreach输出：JDK1.5之后提供的新功能，可以输出数组或集合。

4）for循环

代码示例如下：

 for的形式：

```java
for（int i=0;i<arr.size();i++）{
	...
}
```

 foreach的形式： 

```java
for（int　i：arr）{
	...
}
```

 iterator的形式：

```java
Iterator it = arr.iterator();
while(it.hasNext()){ 
	object o =it.next(); 
...}
```



## 五、ArrayList和LinkedList

ArrayList和LinkedList在用法上没有区别，但是在功能上还是有区别的。LinkedList经常用在增删操作较多而查询操作很少的情况下，ArrayList则相反。

## 六、Map集合

实现类：HashMap、Hashtable、LinkedHashMap和TreeMap

* HashMap 

HashMap是最常用的Map，它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的。因为键对象不可以重复，所以HashMap最多只允许一条记录的键为Null，允许多条记录的值为Null，是非同步的

* Hashtable

Hashtable与HashMap类似，是HashMap的线程安全版，它支持线程的同步，即任一时刻只有一个线程能写Hashtable，因此也导致了Hashtale在写入时会比较慢，它继承自Dictionary类，不同的是它不允许记录的键或者值为null，同时效率较低。

* ConcurrentHashMap

线程安全，并且锁分离。ConcurrentHashMap内部使用段(Segment)来表示这些不同的部分，每个段其实就是一个小的hash table，它们有自己的锁。只要多个修改操作发生在不同的段上，它们就可以并发进行。

* LinkedHashMap

LinkedHashMap保存了记录的插入顺序，在用Iteraor遍历LinkedHashMap时，先得到的记录肯定是先插入的，在遍历的时候会比HashMap慢，有HashMap的全部特性。

* TreeMap

TreeMap实现SortMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序（自然顺序），也可以指定排序的比较器，当用Iterator遍历TreeMap时，得到的记录是排过序的。不允许key值为空，非同步的；

### map的遍历

#### 第一种：KeySet()

将Map中所有的键存入到set集合中。因为set具备迭代器。所有可以迭代方式取出所有的键，再根据get方法。获取每一个键对应的值。 keySet():迭代后只能通过get()取key 。
取到的结果会乱序，是因为取得数据行主键的时候，使用了HashMap.keySet()方法，而这个方法返回的Set结果，里面的数据是乱序排放的。
典型用法如下：

```java
Map map = new HashMap();
map.put("key1","lisi1");
map.put("key2","lisi2");
map.put("key3","lisi3");
map.put("key4","lisi4");  
```


//先获取map集合的所有键的set集合，keyset（）

```java
Iterator it = map.keySet().iterator();
 //获取迭代器
while(it.hasNext()){
	Object key = it.next();
System.out.println(map.get(key));
}
```

#### 第二种：entrySet（）

`Set<Map.Entry<K,V>>` entrySet() //返回此映射中包含的映射关系的 Set 视图。（一个关系就是一个键-值对），就是把(key-value)作为一个整体一对一对地存放到Set集合当中的。Map.Entry表示映射关系。entrySet()：迭代后可以e.getKey()，e.getValue()两种方法来取key和value。返回的是Entry接口。
典型用法如下：

```java
Map map = new HashMap();
map.put("key1","lisi1");
map.put("key2","lisi2");
map.put("key3","lisi3");
map.put("key4","lisi4");
```


//将map集合中的映射关系取出，存入到set集合

```java
Iterator it = map.entrySet().iterator();
	while(it.hasNext()){
	Entry e =(Entry) it.next();
	System.out.println("键"+e.getKey () + "的值为" + e.getValue());
}
```


推荐使用第二种方式，即entrySet()方法，效率较高。
对于keySet其实是遍历了2次，一次是转为iterator，一次就是从HashMap中取出key所对于的value。而entryset只是遍历了第一次，它把key和value都放到了entry中，所以快了。两种遍历的遍历时间相差还是很明显的。

## 七、 List集合

1. list中添加，获取，删除元素；

2. list中是否包含某个元素；
3. list中根据索引将元素数值改变(替换)；
4. list中查看（判断）元素的索引；
5. 根据元素索引位置进行的判断；
6. 利用list中索引位置重新生成一个新的list（截取集合）；
7. 对比两个list中的所有元素；
8. 判断list是否为空；
9. 返回Iterator集合对象；
10. 将集合转换为字符串；
11. 将集合转换为数组；
12. 集合类型转换；
13. 去重复；

```java
package MyTest01;
 
import java.util.ArrayList;
import java.util.List;
 
public class ListTest01 {
 
    public static void main(String[] args) {
         
            //list中添加，获取，删除元素
            List<String> person=new ArrayList<>();
            person.add("jackie");   //索引为0  //.add(e)
            person.add("peter");    //索引为1
            person.add("annie");    //索引为2
            person.add("martin");   //索引为3
            person.add("marry");    //索引为4
             
            person.remove(3);   //.remove(index)
            person.remove("marry");     //.remove(Object o)
             
            String per="";
            per=person.get(1);
            System.out.println(per);    ////.get(index)
             
            for (int i = 0; i < person.size(); i++) {
                System.out.println(person.get(i));  //.get(index)
            }
             
             
         
            //list总是否包含某个元素
            List<String> fruits=new ArrayList<>();
            fruits.add("苹果");
            fruits.add("香蕉");
            fruits.add("桃子");
            //for循环遍历list
            for (int i = 0; i < fruits.size(); i++) {
                System.out.println(fruits.get(i));
            }
            String appleString="苹果";
            //true or false
            System.out.println("fruits中是否包含苹果："+fruits.contains(appleString));
             
            if (fruits.contains(appleString)) {
                System.out.println("我喜欢吃苹果");
            }else {
                System.out.println("我不开心");
            }
             
            //list中根据索引将元素数值改变(替换)
            String a="白龙马", b="沙和尚", c="八戒", d="唐僧", e="悟空";
            List<String> people=new ArrayList<>();
            people.add(a);
            people.add(b);
            people.add(c);
            people.set(0, d);   //.set(index, element)      //将d唐僧放到list中索引为0的位置，替换a白龙马
            people.add(1, e);   //.add(index, element);     //将e悟空放到list中索引为1的位置,原来位置的b沙和尚后移一位
             
            //增强for循环遍历list
            for(String str:people){
                System.out.println(str);
            }
             
            //list中查看（判断）元素的索引
            List<String> names=new ArrayList<>();
            names.add("刘备");    //索引为0
            names.add("关羽");    //索引为1
            names.add("张飞");    //索引为2
            names.add("刘备");    //索引为3
            names.add("张飞");    //索引为4
            System.out.println(names.indexOf("刘备"));
            System.out.println(names.lastIndexOf("刘备"));
            System.out.println(names.indexOf("张飞"));
            System.out.println(names.lastIndexOf("张飞"));
             
            //根据元素索引位置进行的判断
            if (names.indexOf("刘备")==0) {
                System.out.println("刘备在这里");
            }else if (names.lastIndexOf("刘备")==3) {
                System.out.println("刘备在那里");
            }else {
                System.out.println("刘备到底在哪里？");
            }
             
            //利用list中索引位置重新生成一个新的list（截取集合）
            List<String> phone=new ArrayList<>();
            phone.add("三星");    //索引为0
            phone.add("苹果");    //索引为1
            phone.add("锤子");    //索引为2
            phone.add("华为");    //索引为3
            phone.add("小米");    //索引为4
            //原list进行遍历
            for(String pho:phone){
                System.out.println(pho);
            }
            //生成新list
            phone=phone.subList(1, 4);  //.subList(fromIndex, toIndex)      //利用索引1-4的对象重新生成一个list，但是不包含索引为4的元素，4-1=3
            for (int i = 0; i < phone.size(); i++) { // phone.size() 该方法得到list中的元素数的和
                System.out.println("新的list包含的元素是"+phone.get(i));
            }
             
            //对比两个list中的所有元素
            //两个相等对象的equals方法一定为true, 但两个hashcode相等的对象不一定是相等的对象
            if (person.equals(fruits)) {
                System.out.println("两个list中的所有元素相同");
            }else {
                System.out.println("两个list中的所有元素不一样");
            }
             
            if (person.hashCode()==fruits.hashCode()) {
                System.out.println("我们相同");
            }else {
                System.out.println("我们不一样");
            }
             
             
            //判断list是否为空
            //空则返回true，非空则返回false
            if (person.isEmpty()) {
                System.out.println("空的");
            }else {
                System.out.println("不是空的");
            }
             
            //返回Iterator集合对象
            System.out.println("返回Iterator集合对象:"+person.iterator());
             
            //将集合转换为字符串
            String liString="";
            liString=person.toString();
            System.out.println("将集合转换为字符串:"+liString);
             
            //将集合转换为数组，默认类型
            System.out.println("将集合转换为数组:"+person.toArray());
             
            ////将集合转换为指定类型（友好的处理）
            //1.默认类型
            List<Object> listsStrings=new ArrayList<>();
            for (int i = 0; i < person.size(); i++) {
                listsStrings.add(person.get(i));
            }
            //2.指定类型
            List<StringBuffer> lst=new ArrayList<>();
            for(String string:person){
                lst.add(StringBuffer(string));
            }
             
             
             
             
    }
 
    private static StringBuffer StringBuffer(String string) {
        return null;
    }
 
 
    }
```

## 八、Set集合

```java
//对 set 的遍历  
  
//1.迭代遍历：  
Set<String> set = new HashSet<String>();  
Iterator<String> it = set.iterator();  
while (it.hasNext()) {  
  String str = it.next();  
  System.out.println(str);  
}  
  
//2.for循环遍历：  
for (String str : set) {  
      System.out.println(str);  
}  
  
  
//优点还体现在泛型 假如 set中存放的是Object  
  
Set<Object> set = new HashSet<Object>();  
//for循环遍历：  
for (Object obj: set) {  
      if(obj instanceof Integer){  
                int aa= (Integer)obj;  
             }else if(obj instanceof String){  
               String aa = (String)obj  
             }  
              ........  
}
```



## 九、主要实现类区别小结

### Vector和ArrayList

1. vector是线程同步的，所以它也是线程安全的，而arraylist是线程异步的，是不安全的。如果不考虑到线程的安全因素，一般用arraylist效率比较高。
2. 如果集合中的元素的数目大于目前集合数组的长度时，vector增长率为目前数组长度的100%，而arraylist增长率为目前数组长度的50%。如果在集合中使用数据量比较大的数据，用vector有一定的优势。
3. 如果查找一个指定位置的数据，vector和arraylist使用的时间是相同的，如果频繁的访问数据，这个时候使用vector和arraylist都可以。而如果移动一个指定位置会导致后面的元素都发生移动，这个时候就应该考虑到使用linklist,因为它移动一个指定位置的数据时其它元素不移动。

ArrayList 和Vector是采用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，都允许直接序号索引元素，但是插入数据要涉及到数组元素移动等内存操作，所以索引数据快，插入数据慢，Vector由于使用了synchronized方法（线程安全）所以性能上比ArrayList要差，LinkedList使用双向链表实现存储，按序号索引数据需要进行向前或向后遍历，但是插入数据时只需要记录本项的前后项即可，所以插入数度较快。

### arraylist和linkedlist

1. ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。
2. 对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。
3. 对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。 这一点要看实际情况的。若只对单条数据插入或删除，ArrayList的速度反而优于LinkedList。但若是批量随机的插入删除数据，LinkedList的速度大大优于ArrayList. 因为ArrayList每插入一条数据，要移动插入点及之后的所有数据。

### HashMap与TreeMap

1. HashMap通过hashcode对其内容进行快速查找，而TreeMap中所有的元素都保持着某种固定的顺序，如果你需要得到一个有序的结果你就应该使用TreeMap（HashMap中元素的排列顺序是不固定的）。
2. 在Map 中插入、删除和定位元素，HashMap是最好的选择。但如果您要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。使用HashMap要求添加的键类明确定义了hashCode()和 equals()的实现。

两个map中的元素一样，但顺序不一样，导致hashCode()不一样。
同样做测试：
在HashMap中，同样的值的map,顺序不同，equals时，false;
而在treeMap中，同样的值的map,顺序不同,equals时，true，说明，treeMap在equals()时是整理了顺序了的。

### HashTable与HashMap

1. 同步性:Hashtable是线程安全的，也就是说是同步的，而HashMap是线程序不安全的，不是同步的。
2. HashMap允许存在一个为null的key，多个为null的value 。
3. hashtable的key和value都不允许为null。
