<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Java基础](#java%E5%9F%BA%E7%A1%80)
  - [数组常见异常](#%E6%95%B0%E7%BB%84%E5%B8%B8%E8%A7%81%E5%BC%82%E5%B8%B8)
    - [第一种:](#%E7%AC%AC%E4%B8%80%E7%A7%8D)
    - [第二种:](#%E7%AC%AC%E4%BA%8C%E7%A7%8D)
    - [第三种:](#%E7%AC%AC%E4%B8%89%E7%A7%8D)
  - [array复制](#array%E5%A4%8D%E5%88%B6)
  - [array元素反转](#array%E5%85%83%E7%B4%A0%E5%8F%8D%E8%BD%AC)
  - [数组排序](#%E6%95%B0%E7%BB%84%E6%8E%92%E5%BA%8F)
- [面向对象](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1)
  - [总结](#%E6%80%BB%E7%BB%93)
  - [overload重载](#overload%E9%87%8D%E8%BD%BD)
  - [匿名类对象](#%E5%8C%BF%E5%90%8D%E7%B1%BB%E5%AF%B9%E8%B1%A1)
  - [可变个数的形参的方法(数据类型要一样)](#%E5%8F%AF%E5%8F%98%E4%B8%AA%E6%95%B0%E7%9A%84%E5%BD%A2%E5%8F%82%E7%9A%84%E6%96%B9%E6%B3%95%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E8%A6%81%E4%B8%80%E6%A0%B7)
  - [*方法参数传递*](#%E6%96%B9%E6%B3%95%E5%8F%82%E6%95%B0%E4%BC%A0%E9%80%92)
  - [面向对象特征之一: 封装(Encapsulation)](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%B8%80-%E5%B0%81%E8%A3%85encapsulation)
  - [类的成员之三: 构造器(constructor)](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E4%B8%89-%E6%9E%84%E9%80%A0%E5%99%A8constructor)
  - [this](#this)
  - [package](#package)
  - [import](#import)
  - [面向对象特征之二:继承(inheritance)](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%BA%8C%E7%BB%A7%E6%89%BFinheritance)
    - [override重写](#override%E9%87%8D%E5%86%99)
    - [super](#super)
  - [面向对象特征之三: 多态性](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%B8%89-%E5%A4%9A%E6%80%81%E6%80%A7)
    - [object类](#object%E7%B1%BB)
    - [toString方法](#tostring%E6%96%B9%E6%B3%95)
    - [Wrapper包装类](#wrapper%E5%8C%85%E8%A3%85%E7%B1%BB)
  - [static](#static)
  - [类的成员之四: 代码块](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E5%9B%9B-%E4%BB%A3%E7%A0%81%E5%9D%97)
  - [final](#final)
  - [Abstract](#abstract)
  - [interface 接口](#interface-%E6%8E%A5%E5%8F%A3)
  - [类的成员之五: 内部类](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E4%BA%94-%E5%86%85%E9%83%A8%E7%B1%BB)
- [异常处理(Exception&Error)](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86exceptionerror)
  - [common *RuntimeException*:](#common-runtimeexception)
  - [如何处理异常](#%E5%A6%82%E4%BD%95%E5%A4%84%E7%90%86%E5%BC%82%E5%B8%B8)
- [集合](#%E9%9B%86%E5%90%88)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

#  Java基础



## 数组常见异常

- ArrayIndexOutofBoundsException

```java
public static void main(String[] args) {
		int[] i = new int[10];
		i[10]= 99;
    
```

- NullPointerException

### 第一种:

```java
boolean[] b = new boolean[3];
b = null;
System.out.println(b[0]);

```

### 第二种:

```java
String[] str = new String[4];
System.out.println(str[3].toString());

```

### 第三种:

```java
int[][]j = new int[3][];
j[2][0] = 33;

```



## array复制

```java
int[] array1, array2;
array1 = new int[] { 2, 3, 8};
/* 
array2 = array1
error:如果修改array2会同时修改1,因为这样只是传递了地址给2
*/
array2 = new int[array1.length];
for (int i = 0; i < array1.length; i++){
    array2[i] = array1[i];
}
```



## array元素反转

```java
int[] arr = new int[]{ 9, 88, 5};
for(int i = 0;i < arr.length/2;i++){
    int temp = arr[i];
    arr[i] = arr[arr.length - 1 - i];
    arr[arr.length - 1 - i] = temp;
}//第一种
/*第二种
for(int x = 0,y = arr.length - 1;x < y;x++,y--){
	int temp = arr[x];
	arr[x] = arr[y];
	arr[y] = temp;
}
*/
```



## 数组排序

- 冒泡

  ```java
  public static void main(String[] args) {
  			int[]arr = new int[]{49,343,45,87,3,13,67};
  			for(int i = 0; i < arr.length -1; i++){
  				for(int j = 0; j < arr.length -1 - i; j++){
  					if (arr[j] > arr[j+1]) {
  						int temp = arr[j];
  						arr[j] = arr[j + 1];
  						arr[j + 1] = temp;
  		           }
  		       }
  		    }
  		    System.out.println("从小到大排序以后:");
  		    for(int i = 0; i < arr.length; i++){
  		    	System.out.println(arr[i] + "\t");
  		    }
  		}
  ```

- 直接选择顺序

  ```java
  public static void main(String[] args) {
  		int[]arr = new int[]{49,343,45,87,3,13,67};
  		for(int i = 0; i < arr.length - 1; i++) {
  			int t = i;//默认i是最小
  			for(int j = i; j < arr.length; j++) {
  				//一旦在i后发现存在比i小的元素,记录那个下角标
  				if(arr[t] > arr[j]) {
  					t = j;
  				}
  			}
  			if(t != i) {
  				int temp = arr[t];
  				arr[t] = arr[i];
  				arr[i] = temp;
  			}
  		}
  		 System.out.println("从小到大排序以后:");
  		    for(int i = 0; i < arr.length; i++){
  		    	System.out.println(arr[i] + "\t");}// TODO Auto-generated method stub
  
  	}
  ```



# 面向对象

## 总结

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-16-%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.JPG)

## overload重载

同一个类中,方法名相同,而参数列表不同(类型/个数),与返回类型无关

```java
class Overload{
    public int getSum(int i,int j){
        return i + j;
    }
    public int getSum(int i, int j, int k){
        return i + j + k;
    }
    public int getSum(double a, double b){
        return a * b;
    }
    public void getSum(double a, double b, double c){
        System.out.println(a + b + c);
    }
}
```

```java
class Overload{
    public void method(int i, String j){
        
    }
    public void method(String j, int i){
        
    }
}
```



## 匿名类对象

创建的类的对象是匿名的

- 只需要**一次**调用类的对象

```java
p.printAreas(new Circle(), 6);
//System.out.println(c.getRadius);
```



## 可变个数的形参的方法(数据类型要一样)

- 调用时, 个数从0开始

```java
// 以下三个sayHello()仍为overload
public void sayHello(String str1){
    System.out.println("hello" + str1);
}
public void sayHello(){
    for(int i = 0; i < args.length; i++){
        System.out.println(args[i]);
    }
}
// 可变个数形参
public void sayHello(String... args){
    for(int i = 0; i < args.length; i++){
        System.out.println(args[i]);
    } 
}
```

- 若方法中存在可变个数的形参,一定要声明在最后

```java
public void sayHello(int i, String... args){
    for(int i = 0; i < args.length; i++){
        System.out.println(args[i]);
    } 
}
```

- 一个方法只能有一个可变个数的形参



## *方法参数传递*

pass by value 值传递:

- argument是primitive: 将parameter的值传递给argument的基本数据类型变量
- argument是reference: 将reference的值(对应堆空间的对象实体的首地址值) 传递给argument的引用数据类型变量



## 面向对象特征之一: 封装(Encapsulation) 

问题： 不让对象直接作用属性，而是通过“方法.属性”来控制对象对属性的访问

- 封装: 
  1. 将类的属性私有化
  2. 提供公共方法来实现调用

```java
public class TestAnimal {
    public static void main(String[] args){
        Animal a1 = new Animal();
        a1.setLegs(4);
        a1.setname("花花");
        a1.getLegs();
        a1.getName;
    }
}

class Animal{
    private String name;
    private int legs;
    //private 修饰的属性只能在本类中来调用,出了本类,只能用公共方法来调用
    public void setLegs(int l){
        if(l > 0 && l % 2 ==0){
            legs = l;
        }else{
            System.out.println("您输入的数据有误");
        }
    }
    public void setName(String n){
        //...
        name = n;
    }
    //设置类的属性
    public int getLegs(){
        return legs;
    }    
    public String getName(){
        return name;
    }
    //获取类的属性
}
```



- class/ method 权限修饰符: public protected default private



| 修饰符    | 类内部 | 同一个包 | 子类 | 任何地方 |
| --------- | :----: | :------: | :--: | :------: |
| private   |  yes   |          |      |          |
| (default) |  yes   |   yes    |      |          |
| protected |  yes   |   yes    | yes  |          |
| public    |  yes   |   yes    | yes  |   yes    |

  > class 只能用（default）和 public



  ## 类的成员之三: 构造器(constructor)

  > 前两个是属性(field),方法(method)

  作用: 

  1. 创建对象
  2. 给创建的对象的属性赋值


- 如何声明: 权限修饰符 类名 (形参) { }
- 设计类时, 若不显式声明类的构造器, 程序会默认提供一个空参的构造器
- 有显式的定义类的构造器, 不在提供默认的构造器
- 类的多个构造器之间构成重载

```java
public class TestPerson{
    public static void main(String[] args){
        //Person p1 = new Person(); 默认的空参
        Person p2 = new Person("Jack", 23);
        System.out.println(p2.getName);
        System.out.println(p2.getAge);// Jack  0
        Person p3 = new Person("Rose", 22);
        System.out.println(p3.getName + "\t" + p3.getAge); //Rose	22 
    }
}

class Person{
  	// 属性
    private String name;
    private int age;
    
    // 构造器 
    public Person(String n){
        name = n;
    }
    public Person(int m){
        age = m;
    }
    public Person(String n, int m){
        name = n;
        age = m;
    }
    // 方法
    public void setName(String n){
        name = n;
    }
    public void setAge(int m){
        age = m;
    }
    public getName(){
        return name;
    }
    public getAge(){
        return age;
    }
   
}
```

> 类对象的属性赋值先后: 1. 默认初始化 2. 显式 3. 构造器 4. "对象.方法()"

## this 

- this.当前对象或当前正在创建的对象

- 可修饰 属性, 方法, 构造器

- 在构造器中, "this(argument)": 调用当前类重载的指定构造器

  > - 在构造器内部必须是首行!
  > - 若一个类中有n个构造器, 那么最多有 n - 1 个构造器中使用this(argument), 否则会出现环路

```java
class Person{
    private int age;
    private String name;
    
    public Person(String name){
        this.name = name;
    }
    public Person(int age){
        this.age = age;
    }
    // this.age: 当前正在创建的对象
    public Person(int age, String name){
        this(age);// 显式的调用当前类的重载的指定构造器
        this.name = name;// this(name);
    }
    
    public void setAge(int age){
        this.age = age;
    }
    //this.age: 当前对象
    public void info(){
        System.out.println("age:" + this.age);
        this.show();// this.show(): 当前方法
    }
    public void show(){
        System.out.println("我是一个人,我的年龄是:" + this.age);
    }
}
```



## package

- 声明源文件所在的包, 写在程序的第一行

- 每**"."**一次, 表示一层文件目录

  > ```java
  > package study.qinghu.java
  > ```

- 小写



## import

- 显式导入指定包下的类或接口

- 若导入java.lang包下的,如: System, String, Math, etc, 不用显示声明

- ".*"

  ```java
  import java.util.*
  ```

- 同名类的导入, 如: 在util包和sql包下同时存在Date类

  ```java
  import java.util.*
    ...
    Date d = new Date();
  	java.sql.Date d1 = new java.sql.Date(23423428L);
  ```

- import static 表示导入指定类的static的*属性/方法*

- 只能导入包下的所有类/接口, **不能**导入*子包*下的类或接口



## 面向对象特征之二:继承(inheritance)

```java
public class Person{
    public void eat{
        System.out.println("吃饭");
    }
}
public class Worker extends Person{
    public static void main(String[] args) {
        Student s = new Student();
        s.eat();
    }
}
```

- 当父类中有private class或method,子类获取的到,但由于封装性,使得子类不能*直接*调用
- 单继承: 子类只能extends一个父类, 一个父类可以有多个子类 

### override重写

对父类重名的类进行重写. 修饰符 返回值类型 方法名 (参数列表) { }

```java
public class Worker extends Person{
    public void eat() {
        System.out.println("工人吃饭");
    }
}
```

- 原因: 子类继承父类后, 若父类的方法对子类不适用, 那么子类可以对父类的方法覆盖

- 规则:

  1. 子类方法的" 返回值类型 方法名 (参数列表) { }" 与父类方法一样
  2. 子类方法的修饰符 **>=** 父类方法
  3. 子类方法抛的异常 **<=** 父类
  4. 子父类的方法必须同为static或同为非static


### super

- 父类 属性, 方法, 构造器
1. 当子类与父类有同名的属性时, 可以通过"super.属性" 显式的调用*父类*中同名的属性; "this.属性"调用*子类*中同名的属性

2. 当子类重写父类的方法后, "super.方法"在子类中显式调用父类中被重写的方法

3. 在子类中使用"super(形参列表)"来显式的调用父类中指定的构造器

   > - 在构造器中, "super(形参列表)"必须声明在首行. 所以super和this只能出现其中一个
   > - 在构造器中, 不显式调用"this(argument)"或"super(argument)"任何一个, 默认调用的是父类空参的构造器

4. 建议: 设计一个类时, 尽量要提供一个空参的构造器



## 面向对象特征之三: 多态性

1. 多态性

   1. 方法的重载和重写

   2. 子类对象的多态性

2. 子类对象的多态性使用前提:
   1. 要有类的继承
   2. 子类对父类方法的重写

3. 编译和运行
    编译时, "看左边", 将此引用变量理解为父类的类型
    运行时, "看右边", 关注真正的对象的实体: 子类的对象. 执行的方法就是子类重写的.

4. 向下转型:

    1) 强转符:  Man m1 = (Man) p1;

    2) 保证不报错ClassCastException, 最好向下转型前, 进行判断: if (p1 **instanceof**  Woman){ }

5. 子类对象的多态性, 并不适用于属性. 即"看左边"

```java
public class JavaPolymorphism {
    public static void main(String[] args) {
        ...
        //子类对象的多态性,父类的引用指向子类对象
        Person p1 = new Man();//向上转型
        //虚拟方法调用: 通过父类的引用指向子类的对象实体, 实际执行的是子类重写父类的方法
        p1.eat();
        p1.walk();
        //p1.shaving(); 编译不通过, 因为Person类里没有Man类的方法
        Man m1 = (Man)p1;//向下转型, 使用强转符
        m1.shaving();
//      Women w = (Woman)p1; 
//      w1.shopping;编译通过, 运行报错
     	
        //instanceof:返回值boolean
        if (p1 instanceof Woman) {
            Woman w1 = (Woman)p1;
            w1.shopping();
        }
         if (p1 instanceof man) {
            man m1 = (man)p1;
            m1.shaving();
        }
    }
}
```



### object类
- java.lang.Object 类, 是所有类的根父类
- 仅有一个空参构造器: public Object() {}
- method: 
  - equals()

    1. 只能比较引用类型变量
    2. 比较两个变量的地址值是否相等

```java
Person p1 = new Person();
Person p2 = new Person();
System.out.println(p1.equals(p2));//false
System.out.println(p1 == p2);//false
```

​		3. String,Package类 ,File类 , Data类 重写Object类的equals()方法, 比较两个对象的"内容"是否完全相同

```java
String str1 = new String("AA");
String str2 = new String("AA");
String str3 = "AA";
String str4 = "AA";
System.out.println(str1 == str2);//false
System.out.println(str1.equals(str2));//true
System.out.println(str3 == str4);// true "AA"在常量池
System.out.println(str1.equals(str3));// true
```

  		4. 自定义一个类, 希望比较两个对象的属性值都相同的情况下返回true, 就需要重写equals(Object obj)方法

```java
//自定义
public boolean equals(Object obj){
    if (this == obj){
        return true;
    }
    if (obj instanceof Person){
        Person p = (Person)obj;
        return this.equals(p.name) == p.name && this.age == p.age;
    } else {
        return false;
    }
}
```

> == : 
>
> - primitive: 比较值
> - reference: 比较地址值



### toString方法

- java.lang.Object.toString:

  ```java
  public String toString() {
      return getClass().getName() + "@" + Interger.toHexString(hashCode());
  }
  ```

  - 当打印一个对象的引用时, 默认调用的是这个对象的toString()方法

  - 当打印的对象所在类没有重写Object中toString()时, 那么调用的是Object定义的返回对象所在的类及对应的堆空间对象的首地址值

  - 常常如下重写了toString(), 将对象的属性信息返回 

    ```java
    public String toString() {
        return "Person: name = " + name + " age= " + age;
    }//手动
    
    //自动
    ```

  - String, Wrapper, File, Data, 已经实现了Object中toString()  override



### Wrapper包装类

| Primitive |    Wrapper    |
| :-------: | :-----------: |
|  boolean  |    Boolean    |
|   byte    |     Byte      |
|   short   |     Short     |
|    int    |  **Integer**  |
|   long    |     Long      |
|   char    | **Character** |
|   float   |     Float     |
|  double   |    Double     |

> - Wrapper 默认null
> - autoboxing/ unboxing

- Wrapper与Primitive, String相互转化

  ```java
  @Test
  public void test2() {
      //Primitive, Wrapper ---> String: 
      int i1 = 10;
      String str1 = i1 + "";//"10" 方法1
      
      Integer i2 = i1;
      String str2 = String.valueOf(i2);//方法2: 调用String override的valueOf(Xxx x)方法
      String str3 = String.valueOf(true);
      
      //String--->Primitive, Wrapper:
      int i3 = Integer.parseInt(str2);//方法1:  调用Wrapper的静态的parseXxx(String)方法
      boolean b1 = Boolean.parseBoolean(str3);
      
  }
  
  @Test//Primitive <---> Wrapper
  public void test1(){
      int i = 0;
      System.out.println(i);
      boolean a = false;
      
      Integer i1 = new Integer(i);
      System.out.println(i1.toString());
      Float f = new Float(22.5F);
      //Float f = new Float("22.5F");
      System.out.println(f);
      
      //java.lang.NumberFormatException
      //i1 = new Integer("12abc");
      //System.out.println(i1);
      
      Boolean b = new Boolean("false");
      System.out.println(b);//"false"
      //Boolean: 当形参是"true" 返回true, 除此之外返回false
      Boolean b1 = new Boolean("trueabc");
      System.out.println(b1);// "false"
      
      Order o = new Order();
      System.out.println(o.c);//null
      
      //Wrapper ---> Primitive: 调用包装类Xxx的XxxValue()方法
      int i2 = i1.intValue();
      System.out.println(i2);
      
      //JDK 5.O后, autoboxing,unboxing
      Integer i3 = 30;//autoboxing
      Boolean jj = false;
      
      int i4 = i3;//unboxing
  }
  
  class Order{
      Boolean c;
  }
  ```

## static

static修饰属性, 方法, *代码块, *内部类

- static修饰属性(类变量)

  - 由类创建的所有的对象, 都共用这一个属性, 存在**静态域**中. 对此属性进行修改, 会导致其他对象对此属性的调用.

    > 实例变量(非static修饰的变量,各个对象各自拥有一套副本)

  - 类变量随着类的加载而加载,早于对象, 且只一份

    > 实例变量(随着对象的创建而被加载)

  - 静态的变量可以直接通过"类.类变量"来调用, 也可以通过"对象.类变量"来调用, 但是"类.实例变量"不行.

- static修饰方法(类方法)

  - 只能调用静态的属性和静态的方法, 非静态的方法能调用静态的属性和方法

  > - *static修饰的方法里不能有this|super*
>
  > - constructor 看作和方法一样

> 静态的结构(static的field method 代码块 内部类)生命周期比非静态结构长: 加载早于非静态, 被回收晚于非静态

![static变量的内存结构图](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-045620.jpg)

应用: 

利用静态的变量达到**累加**的效果, 因为静态的内容独一份,被多个对象所共用, 比如记录创建对象的次数/ 每个对象某个属性有关联

```java
public class TestAccount {
    psvm{
        Account a1 = new Account("abc", 1000);
        Account a2 = new Account("CDF", 2000);
        sout(a1);
        sout(a2);
    }
}
class Account{
    private int id;//账号
    private String password;
    private double balance;
    private static double minbalance = 1;
    private static double rate = 0.05;//利率
    private static int init = 1000;//初始金额
    
    public Account(String password, double balance) {
        this.id = init++;
        this.password = password;
        this.balance = balance;
    }
    ...
}
```



## 类的成员之四: 代码块

- 代码块只能有static修饰

- 非静态代码块:

  - 对类的属性(静态||非静态)进行初始化
  - 可以有输出语句
  - 一个类中可以有多个代码块,多个代码块之间按照**顺序**结构执行
  - 每创建一个类的对象, 非静态代码块就加载一次
  - 非静态代码块的执行**早于**构造器

> 属性赋值的操作:
>
> ①默认的初始化
>
> ②显式的初始化||初始化块(此两结构按照顺序执行)
>
> ③构造器
>
> ——— 以上是对象的属性初始化的过程———
>
> ④通过方法对对象的相应的属性进行修改

- 静态代码块
  - 可以有输出语句
  - 随着类的加载而加载, 而且只被加载一次
  - 多个静态代码块按照顺序执行, 均早于非静态
  - 静态代码块中只能执行静态的结构(类属性,类方法)

```java
public class TestOrder {
    psvm {
        Order o1 = new Order();
        sout(o1);
        
        Order o2 = new Order();
        sout(o2);
    }
}
class Order{
    private int orderId = 1001;
    private String orderName;
    //静态代码块
    {
     	orderId = 1002;
        orderName = "AA";
        sout("我是非静态代码块1")
    }//我是非静态代码块1
     //Order[orderId = 1002, orderId = AA]
    static{
        sout("静态代码块3")
    }//静态代码块3
     //我是非静态代码块1
     //Order[orderId = 1002, orderId = AA]
    ...
}
```

## final

- 修饰类, 属性, 方法

  - final class: 不能被继承, eg. String, StringBuffer, System

  - final method: 不能被重写, eg. Object.getClass()

  - final field: 此属性是常量. 用大写字符, eg. final int L

    > 在哪赋值: ①不能默认赋值②可以显式赋值: 代码块, 构造器

  - 全局常量: 被static, final修饰, eg. Math.PI

    > public static final double PI

> diff: finally,  finalize()

## Abstract 

- 可以修饰类, 方法

- 不能被实例化, 但可以定义构造器

  > 所有类都有构造器

- 有抽象方法的一定是抽象类, 抽象类不一定有抽象方法

- 若子类继承抽象类, 并重写了*所有* 的抽象方法, 则此类是"实体类", 即可以实例化;

  若子类继承抽象类, 并未重写了*所有* 的抽象方法, 则此类仍为抽象类.

```java
public class TestAbstract {
    psvm {
        //Person p1 = new Person();
        //p1.eat;
        Student s1 = new Student();
        s1.eat;
    }
abstract class Person {
	String name;
    
    public Person() {
    }
    public Person(String name) {
        this.name = name;
    }
    //abstract method
    public abstract void eat();
    public abstract void walk();
}
    
class Student extends Person {
	public void eat() {
        sout("student eat");
    }
    public void walk() {
        sout("student walk");
    }     
}
}
```

**总结**: 抽象类作为多个子类的通用模版, 子类在抽象类的基础上拓展.

**解决的问题**: 

1. 当功能内部一部分实现是确定的, 一部分实现是不确定的. 把不确定的部分放在抽象类, 让子类重写
2. 编写一个抽象父类, 父类提供子类的通用方法, 并把>= 一个方法留给子类实现.



## interface 接口

- interface是与class并行的
- 接口看作特殊的抽象类, 包含*常量*, *抽象方法*, 不能包含变量, 一般的方法.
- 没有构造器, 所以不能创建对象
- 定义的是一种功能, 可以被类实现(**implements**)
- 实现接口的类, 必须重写其中*所有* 的抽象方法, 才能实例化, 否则仍为一个抽象类
- 类能实现多个接口(Java中是单继承)
- 接口与接口之间是继承
- 只能被public, (default)修饰

```java
public class TestInterface {
    
}

interface AA {
    //常量
    int I = 12//public static final int I = 12;所有常量都有这些修饰符,所以省略
    //int i;不能有变量
    
    //抽象方法
    void method1();//public abstract void method1);所有方法都有这些修饰符,所以省略
}

abstract class BB implements AA {

}
class DD {
        
}
interface MM {
    void method2();
}


//接口被类实现, 类能实现多个接口
class CC extends DD implements AA, MM {
    public void method1() {
        
    } 
    public void method2() {
        
    }
}

//接口继承接口
interface JJ extends AA, MM {
    void method1();
    void method2();
}
```



## 类的成员之五: 内部类

1. 在类的内部再定义类, 外面的类:外部类. 里面的类: 内部类
2. 分类: 

   - 成员内部类: 声明在类的方法外
   - 局部内部类: 声明在类的方法里
3. 成员内部类:

   - 外部类的成员: 
     - 有**4**个修饰符
     - static final
     - 可调用外部类的属性, 方法
   - 类的特点: 
     -  abstract
     - 还能在内部定义属性, 方法, 构造器
4. 局部内部类:

> 掌握: 
>
> - 如何创建成员内部类的对象
> - 如何区分调用外部类, 内部类的变量(尤其是变量重名时)
> - 局部内部类的使用





# 异常处理(Exception&Error)

## common *RuntimeException*:

- 空指针 NullPointerException

  ```java
  @Test
  public void test1() {
      Person p = new Person();
      p = null;
      sout(p.toString());
  }
  ```

- 数组下标越界 ArrayIndexOutOfBoundsException

  ```java
  @Test
  public void test2() {
      int[] i = new int[10];
      sout(i[10]);
  }
  ```

- 算术异常 ArithmeticException

  ```java
  @Test
  public void test3() {
      int i = 10;
      sout(i / 0);
  }
  ```

- 类型转换  ClassCastException

  ```java
  @Test
  public void test4() {
      Object obj = new Date();Date向上转型为Object
      String str = (String)obj;将Object向下转型String, 但Date不支持
      //String str = (String)new Date();编译异常
  }
  ```



> 一旦出现异常, 下面的代码就不执行了



## 如何处理异常

- 抓抛模型 

  2. "抓": 抓住上一步抛出来的异常类的对象.

     - try-catch-(finally)
     
     ```java
     try {
     
     //可能出现异常的代码
     
     } catch (Exception e1) {
     
     //处理的方式1
     
     } catch (Exception e2) {
     
     //处理的方式2
     
     }
     finally {
     
     //一定要执行的代码
     
     ```
  
}
     ```
  
     
     
     > 1. try内声明的变量,类似于局部变量, 出了try{}, 就不能被调用
     > 2. finally{ }可省略
     > 3. catch() 对异常对象的处理:
     >    - getMessage();
     >    - printStackTrace();
     > 4. 可以有多个catch(), try{} 中抛出的异常类从上往下匹配catch()中异常类的类型, 满足一个并执行完处理方式后就跳出其后多条catch()
     > 5. 异常处理之后的代码可以执行
     > 6. catch()中多个异常类型是子父类,  子类**必须**放上面, 否则编译不通过
     > 7. finally{ }中的代码一定被执行, 不管try{}, catch() {}中是否有仍未处理的异常/ 是否有return
     > 8. try-catch可以嵌套
     
     - throws
     
       在方法声明处, 显式抛出该异常对象的类型.
     
       ```java
       public staic void method() throws Exception{
         ...
       }
     ```

  2. "抛": 当我们执行代码时,一旦出现异常,会在异常代码处生成一个对应的异常类型的对象,并将此对象抛出,且程序终止.(自动抛/手动抛)

     > 此异常类的对象抛给方法的调用者

     - 手动抛`throw`+ 异常类的对象
  
       ```java
     throw new RuntimeException("wrong");
       ```

       - 自定义异常类

         仿造RuntimeException
  
     - 子类重写父类方法, 抛出的异常类型 <= 被重写的方法抛的异常 



# 集合

![Collection接口继承树](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-03-181351.jpg)

![Map接口继承树](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-045626.jpg)

```java
public class TestCollection {
    @Test
    public void testCollection1() {
        Collection coll = new Arraylist();
        //1. size();返回集合中元素个数
        sout(coll.size());
        //2. add(Object obj);添加一个元素,*默认是object*
        coll.add(123);
        coll.add("aa");
        coll.add(new Date());
        //3. addAll(Collection coll):
        Collection coll1 = Arrays.asList(1,2,3);
        coll.addAll(coll1);
        sout(coll.size());//6
        //查看集合元素
        sout(coll);//Arraylist重写了toString()
        //4. isEmpty(); return boolean
        //5. clear(); 
    }
    
    @Test
    public void testCollection2() {
        Collection coll = new Arraylist();
        coll.add(123);
        coll.add("aa");
        coll.add(new Date());
        coll.add("bb");
        //6. contains(Object obj)
        //判断依据: 根据元素所在类的equals()进行判断, 
        //如果存入集合中的元素是自定义类的对象.要求:自定义类要重写euqals()!
        boolean b1 = coll.comtains(123)
        //7. containsAll(Collection coll)
        Collection coll1 = new Arraylist();
        coll1.add(123);
        coll1.add("AA");
        boolean b3 = coll.containsAll(coll1);
        sout("#" + b3);
    }
}
```

