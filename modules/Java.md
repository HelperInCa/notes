<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Java基础](#java%E5%9F%BA%E7%A1%80)
  - [基本语法](#%E5%9F%BA%E6%9C%AC%E8%AF%AD%E6%B3%95)
  - [数组](#%E6%95%B0%E7%BB%84)
    - [常见异常](#%E5%B8%B8%E8%A7%81%E5%BC%82%E5%B8%B8)
    - [复制](#%E5%A4%8D%E5%88%B6)
    - [元素反转](#%E5%85%83%E7%B4%A0%E5%8F%8D%E8%BD%AC)
    - [排序](#%E6%8E%92%E5%BA%8F)
    - [Arrays工具类](#arrays%E5%B7%A5%E5%85%B7%E7%B1%BB)
- [面向对象](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1)
  - [总结](#%E6%80%BB%E7%BB%93)
  - [类和对象](#%E7%B1%BB%E5%92%8C%E5%AF%B9%E8%B1%A1)
    - [内存解析](#%E5%86%85%E5%AD%98%E8%A7%A3%E6%9E%90)
    - [匿名类对象](#%E5%8C%BF%E5%90%8D%E7%B1%BB%E5%AF%B9%E8%B1%A1)
  - [类的成员: 属性, 方法](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98-%E5%B1%9E%E6%80%A7-%E6%96%B9%E6%B3%95)
  - [面向对象特征之一: 封装(Encapsulation)](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%B8%80-%E5%B0%81%E8%A3%85encapsulation)
  - [类的成员之三: 构造器(constructor)](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E4%B8%89-%E6%9E%84%E9%80%A0%E5%99%A8constructor)
  - [this](#this)
  - [JavaBean, UML类图](#javabean-uml%E7%B1%BB%E5%9B%BE)
  - [package](#package)
  - [import](#import)
  - [面向对象特征之二:继承(inheritance)](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%BA%8C%E7%BB%A7%E6%89%BFinheritance)
    - [override重写](#override%E9%87%8D%E5%86%99)
    - [super](#super)
  - [面向对象特征之三: 多态性(Polymorphism)](#%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%89%B9%E5%BE%81%E4%B9%8B%E4%B8%89-%E5%A4%9A%E6%80%81%E6%80%A7polymorphism)
  - [static](#static)
  - [类的成员之四: 代码块](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E5%9B%9B-%E4%BB%A3%E7%A0%81%E5%9D%97)
  - [final](#final)
  - [Abstract](#abstract)
  - [interface 接口](#interface-%E6%8E%A5%E5%8F%A3)
  - [类的成员之五: 内部类](#%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E4%B9%8B%E4%BA%94-%E5%86%85%E9%83%A8%E7%B1%BB)
- [异常处理(Exception&Error)](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86exceptionerror)
  - [common *RuntimeException*](#common-runtimeexception)
  - [如何处理异常](#%E5%A6%82%E4%BD%95%E5%A4%84%E7%90%86%E5%BC%82%E5%B8%B8)
- [集合](#%E9%9B%86%E5%90%88)
  - [Collection接口](#collection%E6%8E%A5%E5%8F%A3)
  - [Map接口](#map%E6%8E%A5%E5%8F%A3)
  - [Collections工具类](#collections%E5%B7%A5%E5%85%B7%E7%B1%BB)
- [泛型 generics](#%E6%B3%9B%E5%9E%8B-generics)
  - [集合中的泛型](#%E9%9B%86%E5%90%88%E4%B8%AD%E7%9A%84%E6%B3%9B%E5%9E%8B)
  - [自定义泛型类](#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%B3%9B%E5%9E%8B%E7%B1%BB)
  - [泛型和继承](#%E6%B3%9B%E5%9E%8B%E5%92%8C%E7%BB%A7%E6%89%BF)
  - [通配符](#%E9%80%9A%E9%85%8D%E7%AC%A6)
- [枚举 Enum](#%E6%9E%9A%E4%B8%BE-enum)
- [注解 Annotation](#%E6%B3%A8%E8%A7%A3-annotation)
- [IO](#io)
  - [File类](#file%E7%B1%BB)
  - [流](#%E6%B5%81)
    - [节点流](#%E8%8A%82%E7%82%B9%E6%B5%81)
    - [缓冲流](#%E7%BC%93%E5%86%B2%E6%B5%81)
    - [转换流](#%E8%BD%AC%E6%8D%A2%E6%B5%81)
    - [标准输入输出流](#%E6%A0%87%E5%87%86%E8%BE%93%E5%85%A5%E8%BE%93%E5%87%BA%E6%B5%81)
    - [打印流](#%E6%89%93%E5%8D%B0%E6%B5%81)
    - [数据流](#%E6%95%B0%E6%8D%AE%E6%B5%81)
    - [对象流](#%E5%AF%B9%E8%B1%A1%E6%B5%81)
    - [RandomAccessFile](#randomaccessfile)
    - [NIO](#nio)
- [多线程](#%E5%A4%9A%E7%BA%BF%E7%A8%8B)
  - [程序 进程 线程](#%E7%A8%8B%E5%BA%8F-%E8%BF%9B%E7%A8%8B-%E7%BA%BF%E7%A8%8B)
  - [线程创建和使用](#%E7%BA%BF%E7%A8%8B%E5%88%9B%E5%BB%BA%E5%92%8C%E4%BD%BF%E7%94%A8)
  - [线程的生命周期](#%E7%BA%BF%E7%A8%8B%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
  - [线程的同步](#%E7%BA%BF%E7%A8%8B%E7%9A%84%E5%90%8C%E6%AD%A5)
  - [线程通信](#%E7%BA%BF%E7%A8%8B%E9%80%9A%E4%BF%A1)
- [常用类](#%E5%B8%B8%E7%94%A8%E7%B1%BB)
  - [Object类](#object%E7%B1%BB)
  - [Wrapper包装类](#wrapper%E5%8C%85%E8%A3%85%E7%B1%BB)
  - [String类](#string%E7%B1%BB)
  - [日期类](#%E6%97%A5%E6%9C%9F%E7%B1%BB)
  - [比较器](#%E6%AF%94%E8%BE%83%E5%99%A8)
  - [Math类](#math%E7%B1%BB)
  - [BigInteger/BigDecimal](#bigintegerbigdecimal)
- [反射](#%E5%8F%8D%E5%B0%84)
  - [Class类](#class%E7%B1%BB)
  - [获取Class类的对象](#%E8%8E%B7%E5%8F%96class%E7%B1%BB%E7%9A%84%E5%AF%B9%E8%B1%A1)
  - [类加载过程与类加载器](#%E7%B1%BB%E5%8A%A0%E8%BD%BD%E8%BF%87%E7%A8%8B%E4%B8%8E%E7%B1%BB%E5%8A%A0%E8%BD%BD%E5%99%A8)
  - [创建运行时类对象并获取其完整结构](#%E5%88%9B%E5%BB%BA%E8%BF%90%E8%A1%8C%E6%97%B6%E7%B1%BB%E5%AF%B9%E8%B1%A1%E5%B9%B6%E8%8E%B7%E5%8F%96%E5%85%B6%E5%AE%8C%E6%95%B4%E7%BB%93%E6%9E%84)
  - [调用指定属性, 方法, 构造器](#%E8%B0%83%E7%94%A8%E6%8C%87%E5%AE%9A%E5%B1%9E%E6%80%A7-%E6%96%B9%E6%B3%95-%E6%9E%84%E9%80%A0%E5%99%A8)
  - [动态代理](#%E5%8A%A8%E6%80%81%E4%BB%A3%E7%90%86)
- [网络编程](#%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B)
  - [网络基础](#%E7%BD%91%E7%BB%9C%E5%9F%BA%E7%A1%80)
- [Java8 新特性](#java8-%E6%96%B0%E7%89%B9%E6%80%A7)
  - [接口的默认和静态方法](#%E6%8E%A5%E5%8F%A3%E7%9A%84%E9%BB%98%E8%AE%A4%E5%92%8C%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95)
  - [Lambda 表达式](#lambda-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
  - [函数式接口](#%E5%87%BD%E6%95%B0%E5%BC%8F%E6%8E%A5%E5%8F%A3)
  - [方法引用和构造器引用](#%E6%96%B9%E6%B3%95%E5%BC%95%E7%94%A8%E5%92%8C%E6%9E%84%E9%80%A0%E5%99%A8%E5%BC%95%E7%94%A8)
  - [Stream API](#stream-api)
  - [Optional 类](#optional-%E7%B1%BB)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

#  Java基础

## 基本语法

- 二进制

  - 二进制的整数有三种形式,计算机底层是使用的数值的补码:

    *原码*: 直接将一个数值换成二进制数。最高位是符号位 
    *负数的反码*: 是对原码按位取反，只是最高位(符号位)确定为1
    *负数的补码*: 其反码加1
    
    > 正数的原码、反码、补码都相同 
    
  - 为什么要使用原码、反码、补码表示形式呢?
  
    计算机辨别“符号位”会让计算机的基础电路设计变复杂! 于是 人们想出了将**符号位也参与运算**的方法. 我们知道, 根据运算法则减去一个正数等于加上一个负数, 即: 1-1 = 1 + (-1) = 0 , 所以机器可以只有加法而没有减法, 这样计算机运算的设计就更简单
  
- 运算符

  - 取余 `%`

    - 结果符号与被除数的符号一致
    - 小数也能进行取余运算

  - 自增/减`++ --`

    ```java
    int a1 = 10;
    int a2 = ++a1;
    System.out.println(a2);// 11
    
    int a1 = 10;
    int a2 = a1++;
    System.out.println(a2);// 10
    ```

  - 赋值运算符`=`

    - 当两侧数据类型不一致时, 使用自动类型转换/强转符处理

    - 拓展赋值运算符`+= -= *= /= %=`

      ```java
      short s1 = 10;
      s1 = s1 + 2;// 编译失败
      s1 += 2;// 不会改变数据类型. 推荐!
      ```

  - 逻辑运算符

    - `&` vs. `&&`区别

      `&`，左边无论真假，右边都进行运算; 

      `&&`，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。
      
      同理`||` 表示: 如果左边为真, 右边不参与运算   
      
    - 异或`^` 两边相同的为 false, 不同为 true

  - 位运算符

    ![20200803162431](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200803162431.png)

  - 运算符的优先级

    > [refer](https://www.cnblogs.com/pinlantu/p/9853493.html)

    若没有圆括号加以约束，那么对于**数值变量**来说，优先级顺序依次为：+正号、-负号 **＞** 乘号*、除号/、取余数符号% **＞** 加号+、减号- **＞** 大于号、等号、小于号、不等号 **＞** 各种赋值符号；

    对于**布尔变量**来说，优先级顺序依次为：逻辑非 **＞** 等号、不等号 **＞** 逻辑与、或、异或 **＞** 各种赋值符号。

- 流程控制

  - `continue` `break` `return`
    - continue语句用于跳过其所在循环语句块的一次执行，继续下一次循环 
    - continue语句出现在多层嵌套的循环语句体中时，可以通过*标签*指明要跳过的是哪一层循环
    - break是终止本层循环
    - return直接结束整个方法，不管这个return处于多少层循环之内

## 数组

### 常见异常

- ArrayIndexOutofBoundsException

```java
public static void main(String[] args) {
		int[] i = new int[10];
		i[10]= 99;
    
```

- NullPointerException

  - 第一种:

    ```java
    boolean[] b = new boolean[3];
    b = null;
    System.out.println(b[0]);
    ```
  
  
  
- 第二种:
  
    ```java
    String[] str = new String[4];
  System.out.println(str[3].toString());
  ```

    

  - 第三种:
  
    ```java
    int[][] j = new int[3][];
    j[2][0] = 33;
    ```
  
    

### 复制

```java
int[] array1, array2;
array1 = new int[] { 2, 3, 8};
/* 
array2 = array1
error:如果修改array2会同时修改1,因为这样只是把1传递了地址给2
*/
array2 = new int[array1.length];
for (int i = 0; i < array1.length; i++){
    array2[i] = array1[i];
}
```



### 元素反转

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

### 排序

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

### Arrays工具类

`java.util.Arrays` 包含了用来操作数组(比如排序和搜索)的各种方法以及能让数组转换为 List 

| 1    |   boolean equals(int[] a,int[] b)    | 判断相等                                    |
| ---- | :----------------------------------: | ------------------------------------------- |
| 2    |       String toString(int[] a)       | 打印                                        |
| 3    |     void fill(int[] a, int val)      | 填充                                        |
| 4    |          void sort(int[] a)          | 排序(快排)                                  |
| 5    |  int binarySearch(int[] a, int key)  | 二分查找                                    |
| 6    |            asList(T... a)            | 将数组转换为 List(不能使用 add/remove等)    |
| 7    |       copyOf(int a, a.length)        | 拷贝(底层采用System.arrayCopy（native方法)) |
| 8    | copyOfRange(int a, int from, int to) | 一定范围拷贝(左闭右开)                      |



# 面向对象

## 总结

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-16-%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.JPG)

## 类和对象

### 内存解析

![image-20200807155215346](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807155340.png)

![image-20200807155617992](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807155618.png) 

### 匿名类对象

创建的类的对象是匿名的

- 只需要**一次**调用类的对象

```java
p.printAreas(new Circle(), 6);
//System.out.println(c.getRadius);
```



- 可变个数的形参的方法(数据类型要一样)
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

  

## 类的成员: 属性, 方法

- 属性(成员变量) field

  - 成员变量 vs. 局部变量

    |              | 成员变量                         | 局部变量                            |
    | ------------ | -------------------------------- | ----------------------------------- |
    | 声明的位置   | 直接声明在类中                   | 方法形参/内部, 代码块内, 构造器内   |
    | 修饰符       | private、public、static、final等 | 能用权限修饰符修饰，可以用final修饰 |
    | 初始化值     | 有默认初始化值                   | 无默认初始化值, 必须先显式赋值      |
    | 内存加载空间 | 堆空间, 静态域                   | 栈空间                              |

    

- 方法 method

  - pass by value 值传递:
    - argument是primitive: 将parameter的值传递给argument的基本数据类型变量
    - argument是reference: 将reference的值(对应堆空间的对象实体的首地址值) 传递给argument的引用数据类型变量

  - overload重载

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
    //设置类的属性
    public void setName(String n){
        //...
        name = n;
    }
    //获取类的属性
    public int getLegs(){
        return legs;
    }    
    public String getName(){
        return name;
    }
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

> 类对象的属性赋值先后: 
>
> 1. 默认初始化 2. 显式 3. 构造器 4. "对象.方法()"

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

## JavaBean, UML类图

- JavaBean

  - 所谓javaBean，是指符合如下标准的Java类: 
    - 类是公共的
    - 有一个无参的公共的构造器 
    - 有属性，且有对应的get、set方法

  - 用户可以使用JavaBean将功能、处理、值、数据库访问和其他任何可以 \用Java代码创造的对象进行打包，并且其他的开发者可以通过内部的JSP 页面、Servlet、其他JavaBean、applet程序或者应用来使用这些对象。用户可以认为JavaBean提供了一种随时随地的复制和粘贴的功能，而不用关心任何改变。

- UML 类图

  ![image-20200810145702484](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200810145703.png)

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

  1. 子类方法的**"方法名 (参数列表) { }"**与父类方法一样
  2. 子类**返回值类型 <= **父类
  3. 子类方法的**权限修饰符 >=** 父类方法
     - private 方法不能被重写
  4. 子类方法抛的**异常 <=** 父类
  5. 子父类的方法必须同为**static**或同为**非static**

### super

- 父类的 属性, 方法, 构造器
1. 当子类与父类有同名的属性时, 可以通过"super.属性" 显式的调用*父类*中同名的属性; "this.属性"调用*子类*中同名的属性

2. 当子类重写父类的方法后, "super.方法"在子类中显式调用父类中被重写的方法

3. 在子类中使用"super(形参列表)"来显式的调用父类中指定的构造器

   > - 在构造器中, "super(形参列表)"必须声明在首行. 所以super和this只能出现其中一个
   > - 在构造器中, 不显式调用"this(argument)"或"super(argument)"任何一个, 默认调用的是父类空参的构造器

4. super的追溯会一层层往上找,不仅限于直接父类,一直到 Object

5. 建议: 设计一个类时, 尽量要提供一个空参的构造器



## 面向对象特征之三: 多态性(Polymorphism)

1. 多态性

   1. 方法的重载和重写

   2. 子类对象的多态性

2. 子类对象的多态性使用前提:
   1. 要有类的继承
   2. 子类对父类方法的重写

3. 编译和运行
    **编译时, "看左边"**, 将此引用变量理解为父类的类型
    **运行时, "看右边"**, 关注真正的对象的实体: 子类的对象. 执行的方法就是子类重写的.

4. 向下转型: (*自动* 类型提升)

    1. 强转符:  Man m1 = (Man) p1;

    2. 保证不报错ClassCastException, 最好向下转型前, 进行判断: if (p1 **instanceof**  Woman){ }

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

6. 继承成员变量和继承方法的区别

   - 若子类重写了父类方法，就意味着子类里定义的方法彻底覆盖了父类里的同名方法
   - 对于属性则不存在这样的现象，即使子类里定义了与父类同名的属性，它依然不可能覆盖父类中定义的属性

   ```java
   class Base {
       int count = 10;
       public void display() {
           System.out.println(this.count);
       }
   }
   
   class Sub extends Base {
       int count = 20;
       public void display() {
           System.out.println(this.count);
       }
   }
   
   @Test
   public void class Test {
       Sub sub = new Sub();
           System.out.println(sub.count);//20
           sub.display();//20
           Base base = sub;
           System.out.println(base == sub);//true
           System.out.println(base.count);//10
           base.display();//20
   }
   ```

   


## static

- 类属性、类方法的设计思想

**类属性**作为该类各个对象之间**共享**的变量。在设计类时,分析哪些属性不因对象的不同而改变，将这些属性设置为类属性。相应的方法设置为类方法。

**类方法**与调用者无关，由于不需要创建对象就可以调用类方法，从而简化了方法的调用。



static修饰属性, 方法, *代码块, *内部类

- static修饰属性(类变量)

  - 由类创建的所有的对象, 都共用这一个属性, 存在**静态域**中. 对此属性进行修改, 会导致其他对象对此属性的调用.

    > 实例变量(非static修饰的变量,各个对象各自拥有一套副本)

  - 类变量随着类的加载而加载,早于对象, 且只一份

    > 实例变量(随着对象的创建而被加载)

  - 静态的变量可以直接通过"类.类变量"来调用, 也可以通过"对象.类变量"来调用, 但是"类.成员变量"不行.

- static修饰方法(类方法)

  - 只能调用静态的属性和静态的方法, 非静态的方法能调用静态的属性和方法

  > - static修饰的方法里不能有this/super, 也不能被重写
>
  > - constructor 看作和方法一样

> 静态的结构(static的field method 代码块 内部类)生命周期比非静态结构长: 加载早于非静态, 被回收晚于非静态

![static变量的内存结构图](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-045620.jpg)

- 应用: 

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

- 代码块(初始化块)只能有`static`修饰

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
> ②显式的初始化||代码块(此两结构按照顺序执行)
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

  - `final class`: 不能被继承, eg. String, StringBuffer, System

  - `final method`: 不能被重写, eg. Object.getClass()

  - `final field`: 此属性是常量. 用大写字符, eg. final int L

    > 在哪赋值: ①不能默认赋值②可以显式赋值: 代码块, 构造器

  - 全局常量: 被`static`, `final`修饰, eg. Math.PI

    `public static final double PI`

> diff: finally,  finalize()

## Abstract

- 只能修饰类, 方法

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
```

**总结**: 抽象类作为多个子类的通用模版, 子类在抽象类的基础上拓展.

**解决的问题**: 

1. 当功能内部一部分实现是确定的, 一部分实现是不确定的. 把不确定的部分放在抽象类, 让子类重写
2. 编写一个抽象父类, 父类提供子类的通用方法, 并把>= 一个方法留给子类实现.



## interface 接口

- interface是与class并行的
- 接口看作特殊的抽象类, 包含**常量**, **抽象方法**, 不能包含变量, 一般的方法. Java8新增默认方法, 静态方法
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

// 实现类必须实现所有方法, 否则需声明为 abstract
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

- 应用: 代理模式(Proxy)

  为其他对象提供一种代理以控制对这个对象的访问

  - 优点
    - 安全代理:屏蔽对真实角色的直接访问。
    - 远程代理:通过代理类处理远程方法调用(RMI)
    - 延迟加载:先加载轻量级的代理对象，真正需要再加载真实对象

  ```java
  // 静态代理
  interface Network {
      public void browse();
  }
  // 被代理类
  class RealServer implements Network {
  	@Override
  	public void browse() {
          sout("真实服务器上网");
      }
  }
  
  // 代理类
  class ProxyServer implements Network {
      private Network network;
      public ProxyServer(Network network) {
  		this.network = network; 
      }
  	public void check() { 
          System.out.println("检查网络连接等操作");
  	}
  	public void browse() { 
          check();
  		network.browse(); 
      }
  }
  public class ProxyDemo {
      public static void main(String[] args) {
  		Network net = new ProxyServer(new RealServer());
  		net.browse(); 
      }
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

- Error & Exception

  Error: Java虚拟机无法解决的严重问题。如:JVM系统内部错误、资源 耗尽等严重情况。比如:StackOverflowError和OOM。一般不编写针对性的代码进行处理。

  Exception: 其它因编程错误或偶然的外在因素导致的一般性问题，可以使 用针对性的代码进行处理。例如:

  空指针访问 试图读取不存在的文件 网络连接中断 数组角标越界

## common *RuntimeException*

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

  1. "抓": 抓住上一步抛出来的异常类的对象.

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
  }
  ```

     1. `try`内声明的变量,类似于局部变量, 出了`try{}`, 就不能被调用
            `finally{ }`可省略

     2. `catch()` 对异常对象的处理:

           - `getMessage();`获取异常信息，返回字符串
  
- `printStackTrace();`获取异常类名和异常信息，以及异常出
        
  现在程序中的位置。返回值void。
        
3. 可以有多个catch(), try{} 中抛出的异常类从上往下匹配catch()中异常类的类型, 满足一个并执行完处理方式后就跳出其后多条catch(). 异常处理之后的代码可以执行
   
4. catch()中多个异常类型是子父类,  子类**必须**放上面, 否则编译不通过
   
5. `finally{ }`中的代码一定被执行, 不管try{}, catch() {}中是否有仍未处理的异常/ 是否有return
        
      6. try-catch可以嵌套   
        
            

  - throws
  
    在方法声明处, 显式抛出该异常对象的类型. 

```java
   public staic void method() throws Exception{
     ...
   }
```

​	2. "抛": 当我们执行代码时,一旦出现异常,会在异常代码处生成一个对应的异		常类型的对象,并将此对象抛出,且程序终止.(自动抛/手动抛)

> 此异常类的对象抛给方法的调用者

- 手动抛`throw`+ 异常类的对象

  ```java
  throw new RuntimeException("wrong");
  ```

  - 自定义异常类

    仿造RuntimeException

- 子类重写父类方法, 抛出的异常类型 <= 被重写的方法抛的异常 



# 集合

![image-20200517221016723](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-18-051017.png)

![image-20200831105640844](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200831105641.png)

## Collection接口

- 方法

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
        sout("#" + b3); // true
        /**
         * 8.删除
         * 	boolean remove(Object obj) :通过元素的equals()判断是否是要删除的那个元素。只会删除找到的第一个元素
		 * 	boolean removeAll(Collection coll):取当前集合的差集
		 *  9. 取两个集合的交集
		 boolean retainAll(Collection c):把交集的结果存在当前集合中，不影响c
		 *  10. 集合是否相等
		 boolean equals(Object obj)
		 *  11. 转成对象数组
		 Object[] toArray()
		 *  12. 获取集合对象的哈希值
		 hashCode()
         */
    }
}
```

- Iterator接口
    - Iterator 仅用于遍历集合，Iterator 本身并**不提供承装对象**的能力。如果需要创建 Iterator 对象，则必须有一个被迭代的集合。
    - 集合对象每次调用iterator()方法都得到一个**全新**的迭代器对象，默认游标都在集合的第一个元素之前。

```java
public class TestIterator {
  @Test
  public void testIterator() {
     		Collection coll = new Arraylist();
        coll.add(123);
        coll.add("aa");
        coll.add(new Date());
    		// 迭代器遍历集合
    		Iterator i = coll.iterator();
    		while(i.hasNext()) {
          sout(i.next());
        }
    		// foreach遍历
    		for(Object o: coll) {
          sout(o);
        }
  }
}
```

- List接口(**有序, 可重复**)

  - 方法

    ![image-20200517230137354](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-18-060137.png)

  - ArrayList(**主要**实现类)
    - 本质是对象引用的一个可变数组
    - 线程不安全(Vector线程安全, 但效率低, 不使用)
    
    > `Arrays.asList()`返回的既不是 ArrayList 实例，也不是 Vector 实例。 是一个固定长度的 List 集合, 不能add remove
  - LinkedList
    - 双向链表
    - 频繁插入/删除时使用

- Set接口(**无序, 不重复**)

  - 无序!=随机

    元素的位置根据hash值存储

  - `hashcode()`,`equals()`, `compareTo()`要*重写*, 保证得到一致的结果

  - HashSet(**主要**实现类)

  - LinkedHashSet(HashSet子类)

    - 使用链表维护*插入*顺序, 但存储是*无序*
    - 性能: 遍历>HashSet, 插入删除<HashSet
  
  - TreeSet
  
    - 底层:红黑树
    - 元素是同一类
    - 查询比 List 快
    - 排序
      - 自然
      - 实现Comparable接口的compareTo()
        - String, 包装类已重写. 升序(小 -> 大, a -> z)
      - 定制
        - 实现Comparator接口的compare()

## Map接口

![Map接口继承树](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-045626.jpg)

> HashSet是HashMap的一种特殊情况, 底层实现有关联

- 保存具有**单向一对一**的数据, 即通过指定的 key 总能找到唯一确定的 value;

  key, value可以是任何引用类型数据;

  key常用Set存, 所以不允许重复, 需重写`hashCode()`, `equals()`;

  value常用String存;

- 方法

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-18-225038.png)

- HashMap(**主要**)

  - 子类: LinkedHashMap 迭代顺序与插入顺序一致

- TreeMap

  类似TreeSet

- Hashtable

  - *过时*, 线程安全. 不允许null作为key, value

  - 子类: Properties

    key, value都为String. 常用于处理属性文件

    ```java
    Properties pros = new Properties();
    pros.load(new FileInputStream("jdbc.properties"));
    String user = pros.getProperty("user");
    Sout(user);
    ```

## Collections工具类

- 提供**静态**方法操作Set, List, Map的元素

  - 排序: reverse(List), shuffle(List), sort(List), sort(List，Comparator)

  - 查找, 替换: Object max(Collection), Object max(Collection，Comparator), intfrequency(Collection，Object), void copy(List dest,List src), boolean replaceAll()
  - 同步: synchronizedXxx()



# 泛型 generics

[泛型与类型擦除](https://blog.csdn.net/briblue/article/details/76736356)

## 集合中的泛型

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-19-193547.png)

```java
public interface List<E> {
  void add(E x);
  Iterator<E> iterator();
}
```

## 自定义泛型类

```java
class person<T> {
  // 定义属性
  private T info;
  // 定义方法
  public T getInfo() {
    return info;
  }
  public void setInfo(T info) {
    this.info = info;
  }
  // 定义构造器
  public Person(T info) {
    this.info = info;
  }
}
```

> - static 方法不能声明泛型
> - try-catch中不能定义泛型

- 泛型方法

  **[**访问权限**]** **<**泛型**>** 返回类型 方法名**([**泛型标识 参数名称**])** 抛出的异常

  ```java
  public class DAO {
    public <E> E get(int id, E e) {...}
  }
  ```

## 泛型和继承

- 父类有泛型，子类可以保留泛型也可指定泛型类型
- 若B是A的一个子类型(类/接口), G是有泛型声明的类/接口, G\<B>**不是**G\<A>子类型

## 通配符

- `?`, 如 `List<?>`, `Map<?>`代表涉及的操作与类型无关
- `List<?>`是`List<String>`、`List<Object>`等各种泛型List的父类
  - *读取* `List<?>`中元素是*安全*的, 因为返回的总是Object
  - *写入* `List<?>`中元素是*不允许*的, 除了null, 因为null是所有类型的成员

- 有限制的通配符
  - `<? extends A>` 允许泛型为A及A子类的调用
  - `<? super A>` 允许泛型为A及A父类的调用
  - `<? extends Comparable>` 允许泛型为实现Comparable接口的实现类的引用调用



# 枚举 Enum

- 枚举类对象的属性不允许被改动**,** 使用 **private final** 修饰

- `java.lang.Enum`

  - 必须在枚举类的第一行声明枚举类对象

  - switch-case: case子句直接使用枚举值

  - 主要方法: 

    - `values()` 返回对象数组. 用于遍历所有枚举值
    - `valueOf(String str)` 把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。否则，会有运行异常。
  - `toString()` 得到当前枚举常量的名称
  
- 实现接口
  
  若需要每个枚举值在调用实现的接口方法呈现出不同的行为方式, 则可以让每个枚举值分别来实现该方法
  
    ```java
    // 多个对象之间用","隔开, 末尾";"结束
    enum Season implements Info{
        SPRING("1", "A") {
            public void show() {
                sout("a");
            }
        },
        SUMMER("2", "B") {
            public void show() {
                sout("b");
            }
        },
        FALL("3", "C"),
        WINTER("4", "D");
    }
    
    interface Info {
      void show();
    }
    ```
  
    
  
  

# 注解 Annotation

- 内置

  - `@Override`: 限定重写父类方法, 只能用于方法
  - `@Deprecated`: 用于表示某个程序元素(类, 方法等)已过时
  - `@SuppressWarnings`: 抑制编译器警告

- 自定义

  ```java
  public @interface MyAnnotation { 
    String str() default "hello";
  }
  ```

- 元注解: 修饰其他注解

  JDK5.0提供四个:
  
  `@Retention`  指定被修饰的注解的生命周期
  
  `@Target` 指定被修饰的注解能用于修饰哪些程序元素
  `@Documented` 指定被修饰的注解所修饰的类将被Javadoc 提取成文档
  `@Inherited` 指定被修饰的注解有继承性
  
- Java 8新特性

    - 可重复的注解
    - 类型的注解

# IO

`package java.io`

## File类

`File`: 文件和目录路径名的抽象表示形式

- 能新建、删除、重命名文件/目录, 但不能访问文件内容本身。如果需要访问文件内容本身，需使用输入/输出流

- File对象可以作为参数传递给流的构造器

- 路径分隔符

    Windows和DOS系统默认使用“\”来表示

    UNIX和URL使用“/”来表示

    为了解决这个隐患，File类提供了一个常量:

    `public static final String separator`根据操作系统，动态提供分隔符

    ```java
    File file = new File("d:" + File.separator + "info.txt");
    ```

- 构造器

    - `public File(String pathname)` 以pathname为路径创建File对象，可以是绝对路径或者相对路径，如果pathname是相对路径，则默认的当前路径在系统属性user.dir中存储。
    - `public File(String parent,String child)` 以parent为父路径，child为子路径创建File对象。
    - `public File(File parent,String child)` 根据一个父File对象和子文件路径创建File对象

- 方法

  - 访问文件名

    getName() 
    getPath() 
    getAbsoluteFile() 
    getAbsolutePath()
    getParent() 
    renameTo(File newName)
    
  - 文件检测
    
    exists()
    
    isFile() 
    
    isDirectory()
    
    canWrite() 
    
    canRead() 
    
  - 获取文件信息
    
    lastModified() 
    
    length()
    
  - 文件操作
    
    createNewFile()
    
    delete()
    
  - 目录操作
    
    mkdir() 
    
    mkdirs() 创建文件目录. 如果上层文件目录不存在, 一并创建 
    
    list()
    
    listFiles()

## 流

- 分类

  - 按操作*数据单位* 不同分为:字节流(8 bit)，字符流(16 bit, 文本)

  - 按*流向* 不同分为:输入流，输出流

  - 按*角色* 的不同分为:节点流(直接处理数据)，处理流(加工节点流)

    | (抽象基类) | 字节流       | 字符类 |
    | ---------- | ------------ | ------ |
    | 输入流     | InputStream  | Reader |
    | 输出流     | OutputStream | Writer |

    > java.io涉及40几个类, 都是从上面4个抽象基类派生的
    >
    > 派生出的子类名以父类名作为后缀

    ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-21-010528.png)

    ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-21-011243.png)

- 打开文件IO不属于内存中资源, 无法被自动回收, 应**显式关闭**IO. 

  `.close()`

### 节点流

- 注意:

    - 在写入一个文件时，如果使用构造`FileOutputStream(file)`，则目录下有同名文件将被覆盖。

        如果使用构造器`FileOutputStream(file,true)`，则目录下的同名文件不会被覆盖, 在文件内容末尾追加内容

    - 字符流操作字符，只能操作普通文本文件。最常见的文本文件: .txt，.java，.c，.cpp 等源代码。.doc,excel,ppt这些不是文本文件。

**用try-catch处理保证流一定关闭**

- FileInputStream/FileReader

  1.建立一个流对象，将已存在的一个文件加载进流。 	FileReader fr = new FileReader(“Test.txt”);
  2.创建一个临时存放数据的数组。							char[] ch = new char[1024];
  3.调用流对象的读取方法将流中的数据读入到数组中。 fr.read(ch);

  - `int read(byte[] b)` `int read(char [] c)`
  - `int read(byte[] b, int offset, int length)` `int read(char[] b, int offset, int length)`

  ![image-20200902171645404](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200902171646.png)

- FileOutputStream/FileWriter

  1.创建流对象，建立数据存放文件 				 FileWriter fw = new FileWriter(“Test.txt”);
  2.调用流对象的写入方法，将数据写入流    	fw.write(“text”);
  3.关闭流资源，并将流中的数据清空到文件中  fw.close();
  
  - `void write(byte[] b/char[] cbuf)`
  - `void write(byte[] b/char[] buff, int offset, int length)`
  - `void write(String str)` `void write(String str, int off, int len)`
### 缓冲流

- 在使用缓冲流类时，会创建一个内部缓冲区数组(默认 8Kb)

- 缓冲流要“套接”在相应的节点流之上，提高了读写的效率，增加了一些新方法

- BufferedInputStream/Reader

  - `BufferedReader br.readline()` 一次读一行

- BufferedOutputStream/Writer

  - 每次写入后刷新缓冲区 `flush()`, 即强制把缓冲区内容写入输出流 

  ![image-20200902180025545](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200902180026.png)

### 转换流

- 在字节流和字符流之间 按指定字符集转换

- 同样要套接在相应节点流上

- `InputStreamReader(InputStream out,String charsetName)` `OutputStreamWriter(OutputStream out,String charsetName)`

- 字节流中的数据都是字符时，转成字符流操作更高效。

    我们使用转换流来处理文件乱码问题。实现编码和解码的功能

### 标准输入输出流

- System.in和System.out分别代表系统标准的输入和输出设备. 默认输入设备是键盘，输出设备是显示器

- System.in的类型是InputStream System.out的类型是PrintStream, 是OutputStream的子

  类FilterOutputStream的子类

- 通过System类的setIn()，setOut()对默认设备进行改变

### 打印流

- PrintStream(字节打印流)和PrintWriter(字符打印流)

### 数据流

- 处理基本数据类型, String,  DataInputStream 和 DataOutputStream

### 对象流

- `ObjectInputStream` `OjbectOutputSteam`

- 存储和读取对象的处理流

- 序列化(Serialize):用ObjectOutputStream类将一个Java对象 写入IO流中
  反序列化(Deserialize):用ObjectInputStream类从IO流中恢复该Java对象
  ObjectOutputStream和ObjectInputStream不能序列化`static`和 `transient`修饰的成员变量

- 类及属性都要实现Serializable接口才能序列化

- 实现Serializable接口的类都有一个表示序列化版本标识符的静态变量: `private static final long serialVersionUID` 

  - 应显示定义.

    如果类没有显示定义这个静态变量，它的值是Java运行时自动生成。若类的源代码作了修改，serialVersionUID可能发生变化

  - 用途: 类的不同版本间的兼容性

### RandomAccessFile

跳到文件的任意地方来读、写文件

- RandomAccessFile对象包含一个记录指针，用以标示当前读, 写处的位置。RandomAccessFile 类对象可以自由移动记录指针:
  `long getFilePointer()`: 获取文件记录指针的当前位置 

  `void seek(long pos)`: 将文件记录指针定位到 pos 位置

- 构造器
  `public RandomAccessFile(String name, String mode)`

  `public RandomAccessFile(File file, String mode)`

  - mode 指定 RandomAccessFile 的访问模式:
  
     ➢ **r:** 以只读方式打开
     ➢ **rw**:打开以便读取和写入
     ➢ **rwd:**打开以便读取和写入;同步文件内容的更新
     ➢ **rws:**打开以便读取和写入;同步文件内容和元数据的更新

### NIO

- IO支持面向缓冲区的(IO是面向流的)、基于通道的IO操作。NIO将以更加高效的方式进行文件的读写操作。

- 提供了两套NIO，一套是针对标准输入输出NIO，另一套就是网络编程NIO。

- Path

    - Path可看成是File类的升级版，实际引用的资源也可以不存在。

    - 提供异常信息

    ```java
    import java.nio.file.Path;
    import java.nio.file.Paths;
    Path path = Paths.get("index.html");    
    ```
    
- Paths工具类

    Paths 类提供的静态 `get()` 方法用来获取 Path 对象:

    `static Path get(String first, String ... more)` : 用于将多个字符连成路径 

    `static Path get(URI uri)`: 返回指定uri对应的Path路径

- Files 工具类

    `Path createDirectory(Path path, FileAttribute<?> ... attr)` : 创建一个目录

    `Path createFile(Path path, FileAttribute<?> ... arr)` : 创建一个文件

    `void deleteIfExists(Path path)` : Path对应的文件/目录如果存在，执行删除

    `long size(Path path)` : 返回 path 指定文件的大小



# 多线程

## 程序 进程 线程

- 程序(program)是为完成特定任务、用某种语言编写的一组指令的集合。即指一段静态的代码，静态对象。 

- 进程(process)是程序的一次执行过程，或是正在运行的一个程序。是一个动态的过程:有它自身的产生、存在和消亡的过程。——生命周期 
  如:运行中的QQ，运行中的MP3播放器
  
  - 程序是静态的，进程是动态的
  
  - **进程作为资源分配的单位**，系统在运行时会为每个进程分配不同的内存区

- 线程(thread)，进程可进一步细化为线程，是一个程序内部的一条执行路径。 

  - 若一个进程同一时间并行执行多个线程，就是支持多线程的 
  - **线程作为调度和执行的单位**，**每个线程拥有独立的运行栈和程序计数器(pc)**，线程切换的开销小 
  - 一个进程中的多个线程共享相同的*堆和方法区*它们从同一堆中分配对象，可以访问相同的变量和对象。这就使得线程间通信更简便、高效。但多个线程操作共享的系统资源可能就会带来安全的隐患。

## 线程创建和使用

1. `java.lang.Thread`类

   创建线程第一种方法: 继承Thread类

   1. 定义子类继承Thread类。
   2. 子类中重写Thread类中的run方法。
   3. 创建Thread子类对象，即创建了线程对象。
   4. 调用线程对象start方法:启动线程，调用run方法。

   ![20200523-Zkyuv3](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200523-Zkyuv3.png)

   ```java
   // 匿名Thread 子类简化代码
   @Test
   public void Test() {
       new Thread() {
       	public void run() {
               for (int i = 0; i < 100; i++) {
                   sout("子线程: " + i);
               }
           }
       }.start();
   }
   ```

   

> - 启动多线程只能用`start()`, 不能手动调用`run()`
> - 一个线程对象只能调用一次`start()`, 重复调用会抛异常

-  构造器
  - `Thread()`:创建新的Thread对象

  - `Thread(String threadname)`:创建线程并指定线程实例名

  - `Thread(Runnable target)`:指定创建线程的目标对象，它实现了Runnable接口中的run方法

  - `Thread(Runnable target, String name)`:创建新的Thread对象

- 常用方法
  - `void start()`: 启动线程，并执行对象的run()方法 

  - `run()`: 线程在被调度时执行的操作

  - `String getName()`: 返回线程的名称

  - `void setName(String name)`:设置该线程名称

  - `static Thread currentThread()`: 返回当前线程

  - `static void yield()`: 暂停当前正在执行的线程，把执行机会让给优先级相同或更高的线程

  - `join()` :当线程 a中调用线程b的 join() 方法时, a将被阻塞，直到 b 执行完为止

  - `static void sleep(long millis)`:(指定时间:毫秒) 令当前活动线程在指定时间段内放弃对CPU控制,使其他线程有机会被执行,时间到后重排队。

  - `boolean isAlive()` 判断线程是否还活着
  
- 线程的优先级控制
    MAX_PRIORITY(10); 

    MIN _PRIORITY (1); 

    NORM_PRIORITY (5); 
  
  高优先级是**概率上更容易**抢占 cpu,不意味着只有当高优先级执行完才开始低优先级
  
    - 线程创建时继承父线程的优先级
  
    方法:
  
    - `getPriority()` :返回线程优先值
  
    - `setPriority(int newPriority)` :改变线程的优先级 
2. `java.lang.Runnable`接口

  创建线程第二种方法: 实现Runnable接口. **优先选择此方式**


1. 定义子类，实现Runnable接口。 
2. 子类中重写Runnable的run() 
3. 通过Thread类含参构造器创建线程对象
4. 将Runnable的子类对象作为实际参数传递给Thread类的构造方法中
5. 调用Thread类的start():开启线程，调用run()

```java
class PrimeRun implements Runnable {
         long minPrime;
         PrimeRun(long minPrime) {
             this.minPrime = minPrime;
         }
         public void run() {
             // 重写
         }
}

PrimeRun p = new PrimeRun(143);
Thread t1 = new Thread(p).start();
Thread t2 = new Thread(p).start();
Thread t3 = new Thread(p).start();
```

- 实现方式 vs. 继承方式

  > public class **Thread** implements **Runnable**

  - 相同: 都要重写`run()`, 将线程执行的逻辑写在`run()`中
  - 优点:
    - 避免了单继承的局限性
    - 多个线程可以共享同一个接口实现类的对象，非常适合多个相同线程来处理同一份资源。
3. `java.util.concurrent.Callable`接口

   - 相比run()方法，可以有返回值
   - 方法可以抛出异常
   - 支持泛型的返回值
   - 需要借助FutureTask类，比如获取返回结果

   步骤:

   1. 创建一个实现 Callable 的实现类
   2. 将此线程需要执行的操作声明在`call()`里面
   3. 创建 Callable 接口实现类的对象
   4. 将此 Callable 接口实现类的对象传到 FutureTask 构造器中, 创建 FutureTask 对象
   5. 将 FutureTask 对象传到 Thread 类的构造器中, 创建 Thread 类的对象, 并调用`start()`
   6. (如需)FutureTask 对象的`get()`获取 Callable 中`call()`的返回值

4. 线程池

   提前创建好多个线程，放入线程池中，使用时直接获取，使用完放回池中。可以避免频繁创建销毁、实现重复利用。

   好处:

   1. 提高响应速度(减少了创建新线程的时间)
   2. 降低资源消耗(重复利用线程池中线程，不需要每次都创建)
   3. 便于线程管理

   ![image-20200815140052087](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200815140052.png)

## 线程的生命周期

![20200523-KJoiD5](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200523-KJoiD5.png)

## 线程的同步

- 提出的问题: 

  多个线程操作共享数据可能出现一个线程未执行完毕时, 另外的线程参与进来而破坏数据。

- 解决办法**:** 

  对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中， 其他线程不可以参与执行。

  - 同步代码块

    **所有线程必须共用同一把锁**; 包裹的代码块不多也不少, 只有共享数据的部分

    > 锁: 1. `this` 2. `类名.class`

    ```java
    // 可以用任意一个类的对象充当同步监视器(锁)
    Object obj = new Object();
    public void run() {
      // Object obj = new Object(); 这样会导致每个线程自己有一把锁, 没有同步的作用
      synchronized(obj) {
      // 需要被同步的代码
      }
    }
    ```

  - 同步方法

    > 同步方法(非静态的)的锁为`this`
    > 同步方法(静态的)的锁为类本身

    ```java
    public synchronized void show (String name){...}
    ```
    
  - 同步的范围

    1、如何找问题，即代码是否存在线程安全?(非常重要) (1)明确哪些代码是多线程运行的代码 (2)明确多个线程是否有共享数据 (3)明确多线程运行代码中是否有多条语句操作共享数据

    2、如何解决呢?(非常重要)

    对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其 他线程不可以参与执行。 即所有操作共享数据的这些语句都要放在同步范围中

    3、切记:

    范围太小:没锁住所有有安全问题的代码  

    范围太大:没发挥多线程的功能。

  > 互斥锁 mutex
  >
  > 防止两条线程同时对同一公共资源进行读写的机制

- 锁

  - 释放锁: 

    - 当前线程的同步方法/代码块执行结束; 
    - 被break, return终止; 
  - 异常抛出
  
- 当前线程的同步方法/代码块执行`wait()`, 暂停当前线程, 并释放锁
  
- 不会释放锁:
  
  - 遇到`sleep()`, `yield()`暂停当前线程
  
- 死锁
  
    不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁.
  
    减少同步资源的定义.
    
  - Lock接口
  
    `java.util.concurrent.locks.Lock`接口是控制多个线程对共享资源进行访问的工具。锁提供了对共享资源的独占访问，每次只能有一个线程对Lock对象加锁，线程开始访问共享资源之前应先获得Lock对象。
  
    ```java
    class A {
        private final ReentrantLock lock = new ReenTrantLock();
        public void m() {
            lock.lock();
            try {
                //保证线程安全的代码;
            }
            finally {
                lock.unlock();
            }
        }
    }
    ```
  
    *注意*:如果同步代码有异常，要将unlock()写入finally语句块
  
  > synchronized 与 Lock 的对比:
  >
  > Lock是显式锁(**手动**开启`lock()`和关闭锁`unlock`)，synchronized是 隐式锁，出了作用域自动释放.
  
  - 优先使用顺序:
  
    Lock -> 同步代码块(已经进入了方法体，分配了相应资源) -> 同步方法 (在方法体之外)

## 线程通信

`java.lang.Object`

- `wait()` 令当前线程挂起并放弃CPU、同步资源，使别的线程可访问并修改共享资源**即释放锁**，而当前线程排队等候再次对资源的访问
- `notify()`:唤醒正在排队等待同步资源的线程中优先级最高者
- `notifyAll()`:唤醒正在排队等待资源的所有线程

> 这三个方法只有在synchronized方法或代码块中使用，否则会报 java.lang.IllegalMonitorStateException异常

![image-20200814191904940](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200814191905.png)





# 常用类

## Object类

- java.lang.Object, 是所有类的根父类

- 仅有一个空参构造器: `public Object() {}` 

- `equals()`

  1. 只能比较引用类型变量

  2. 比较两个变量的地址值是否相等

     ```java
     Person p1 = new Person();
     Person p2 = new Person();
     System.out.println(p1.equals(p2));//false
     System.out.println(p1 == p2);//false
     ```

     

  3. String, Package类 ,File类 , Data类 重写Object类的equals()方法, 比较两个对象的"内容"是否完全相同

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
  > - 两边数据类型必须兼容(包含可自动转换), 否则编译出错

- `toString()`

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
  
- `hashCode()`

## Wrapper包装类

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



- Wrapper与Primitive, String相互转化

  ```java
  @Test
  public void test2() {
      //Primitive, Wrapper ---> String: 
      int i1 = 10;
      String str1 = i1 + "";//"10" 方法1: 连接运算
      
      Integer i2 = i1;
      String str2 = String.valueOf(i2);//方法2: 调用String override的valueOf(Xxx x)方法
      String str3 = String.valueOf(true);
      
      //String--->Primitive, Wrapper:
      int i3 = Integer.parseInt(str2);//调用Wrapper的静态的parseXxx(String)方法
      boolean b1 = Boolean.parseBoolean(str3);
      
  }
  
  @Test//Primitive  ---> Wrapper
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
      
      //JDK 5后, autoboxing,unboxing
      Integer i3 = 30;//autoboxing
      Boolean jj = false;
      
      int i4 = i3;//unboxing
  }
  
  class Order{
      Boolean c;
  }
  ```
  
  ![image-20200811145718122](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200811145718.png)

## String类

- 使用**Unicode**字符编码，一个字符占两个字节
- String是一个`final`类，代表不可变的字符序列. 底层实现是`char[]`

![20200525-tVoKkl](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200525-tVoKkl.png)

> [常量池理解](https://www.jianshu.com/p/c7f47de2ee80)

- 字符串使用特性
  - 常量与常量的拼接结果在常量池。且常量池中不会存在相同内容的常量。  
  - 只要其中有一个是变量，结果就在堆中
  - 如果调用`intern()`，返回值就在常量池中

- 字符串对象操作

  ![image-20200820160214077](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200820160214.png)

  ![image-20200820160239453](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200820160239.png)

  ![image-20200820160256559](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200820160256.png)

- 包装类, 基本数据类型, 字节/字符数组 相互转换

  1. 字符串 与 基本数据类型, 包装类 转换

     - 字符串 -> 基本数据类型/包装类: 包装类的`parseXxx(String str)`
     - 基本数据类型/包装类 -> 字符串: 字符串重载的`valueOf(xxx n)`

  2. 字符串 与 字节数组 转换

     - 字符串 -> 字节数组: 字符串的getBytes()

     - 字节数组 -> 字符串: 字符串的构造器

  3. 字符串 与 字符数组 转换

     - 字符串 -> 字符数组: 字符串的toCharArray()
     - 字符数组 -> 字符串: 字符串的构造器

- StringBuffer

    java.lang.StringBuffer代表**可变**的字符序列，可以对字符串内容进行增删改查. 线程安全.

    - 构造器

      `StringBuffer()`:初始容量为16的字符串缓冲区 
      `StringBuffer(int size)`:构造指定容量的字符串缓冲区
      `StringBuffer(String str)`:将内容初始化为指定字符串内容

    - 方法

        增 `append()`

        删 `delete(int start, int end)`

        改 `setCharAt(int index, char ch)`/ `replace(int start, int end, String str)`

        查 `charAt(int n)`

        插入 `insert(int offset, xxx)`

        反转 `reverse()`

        长度 `length()`

- StringBuilder

    java.lang.StringBuilder和StringBuilder类似, 效率更高, 但线程不安全

## 日期类

- `java.time`基础包

    - `LocalDate`、`LocalTime`、`LocalDateTime` 

        他们的实例是不可变的.

        ![image-20200820203221267](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200820203221.png)

    - `Instant` 瞬时

        表示自1970年1月1日0时0分0秒(UTC)开始的秒数。因为java.time包是基于纳秒计算的，所以Instant的精度可以达到纳秒级.

        | 方法                            | 描述                                                         |
        | ------------------------------- | ------------------------------------------------------------ |
        | `now()`                         | 静态方法，返回默认UTC时区的Instant类的对象                   |
        | `ofEpochMilli(long epochMilli)` | 静态方法，返回在1970-01-01 00:00:00基础上加上指定毫秒 数之后的Instant类的对象 |
        | `atOffset(ZoneOffset offset)`   | 结合即时的偏移来创建一个 OffsetDateTime                      |
        | `toEpochMilli()`                | 返回1970-01-01 00:00:00到当前时间的毫秒数，即为时间戳        |

- `java.time.format.DateTimeFormatter`

    | 方法                         | 描述                                                |
    | ---------------------------- | --------------------------------------------------- |
    | `ofPattern(String pattern)`  | 静态方法，返回一个指定字符串格式的DateTimeFormatter |
    | `format(TemporalAccessor t)` | 格式化一个日期、时间，返回字符串                    |
    | `parse(CharSequence text)`   | 将指定格式的字符序列解析为一个日期、时间            |

- 其他 API

    ![image-20200820204328782](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200820204329.png)

*----------------以下为Java8之前的--------------------*

- `java.lang.System`类下的`public static long currentTimeMillis()`, 用于计算时间差

- `java.util.Date` (及其子类 java.sql.Date)

  - `toString()` dow mon dd hh:mm:ss zzz yyyy 其中: dow是星期几(Mon, Wed, ...), zzz是时间标准
  - `getTime()`

- `java.text.SimpleDateFormat`

  不与语言环境有关的方式来格式化和解析日期的具体类.

  格式化(日期->文本)

  - `SimpleDateFormat()` :默认的模式和语言环境创建对象
  - `public SimpleDateFormat(String pattern)`:该构造方法可以用参数pattern 指定的格式创建一个对象，该对象调用:
  - `public String format(Date date)`:方法格式化时间对象date

  解析(文本->日期)

  - `public Date parse(String source)`:从给定字符串的开始解析文本，以生成 一个日期

- `java.util.Calendar`

  抽象基类，主用用于完成日期字段之间相互操作的功能

  - 获取Calendar实例的方法
    - 使用Calendar.getInstance()方法 
    - 调用它的子类GregorianCalendar的构造器

  - get(int field), set(int field, int value), add(int feild, int amount), Date getTime()/setTime(Date d)
  
      > 获取月份时:一月是0，二月是1 ... 12月是11  
      >
      > 获取星期时:周日是1，周二是2 ... 周六是7

## 比较器

- `java.lang.Comparable` 接口

    - `compareTo(Object o)` 

        返回值>=0: 当前对象 this >= 形参 obj; 

        返回值<0:  当前对象 this < 形参 obj.

    - 默认从小到大

        - String:按照字符串中字符的Unicode值进行比较
        - Character:按照字符的Unicode值来进行比较
        - 数值类型对应的包装类以及BigInteger、BigDecimal:按照它们对应的数值大小进行比较
        - Boolean:true 对应的包装类实例大于 false 对应的包装类实例 
        - Date、Time等:后面的日期时间比前面的日期时间大

- `java.util.Comparator` 接口

    当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码, 或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，可考虑使用 Comparator 的对象来排序

    - `campare(Object o1, Object o2)` 

        - 返回值>=0: o1 >= o2; 

            返回值<0: o1 < o2

## Math类

`java.lang.Math`提供了一系列静态方法用于科学计算;其方法的参数和返回值类型一般为double型

## BigInteger/BigDecimal

不可变 任意精度



# 反射

**Reflection(反射)**是被视为动态语言的关键，反射机制允许程序在执行期借助于Reflection API取得任何类的内部信息且能直接操作. 

## Class类

- `java.lang.Class` 本身是一个类
- 一个类在JVM中只有一个Class对象, 因为只能创建一次

    一个Class对象对应一个加载到JVM的一个.class文件
- 通过Class可以完整得到一个类的结构

## 获取Class类的对象

1. 若已知具体的类，通过类的class属性获取，该方法最安全可靠，性能最高

   ```java
   Class clazz = String.class;
   ```

2. 已知某个类的实例，调用该实例的getClass()方法获取Class对象

   ```java
   Class clazz = “hello, world”.getClass(); 
   ```

   

3. 已知一个类的全类名，且该类在类路径下，可通过 Class类的静态方法*forName()* 获取，可能抛`ClassNotFoundException` 

   ```java
   Class clazz = Class.forName(“java.lang.String”);
   ```

4. 类的加载器(了解)

   ```java
   ClassLoader cl = this.getClass().getClassLoader(); 
   Class clazz4 = cl.loadClass(“类的全类名”);
   ```

   > `getResourceAsStream(String str)`:获取类路径下的指定文件的输入流

## 类加载过程与类加载器

- 类加载过程

    ![image-20200903113331278](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200903113331.png)

- 什么时候发生类的初始化

    - 类的主动引用(一定会发生类的初始化)
        当虚拟机启动，先初始化main方法所在的类;
         new一个类的对象;
         调用类的静态成员(除了final常量)和静态方法;
         使用java.lang.reflect包的方法对类进行反射调用;

         当初始化一个类，如果其父类没有被初始化，则先会初始化它的父类.

    - 类的被动引用(不会发生类的初始化)
        当访问一个静态域时，只有真正声明这个域的类才会被初始化;

        当通过子类引用父类的静态变量，不会导致子类初始化;

        通过数组定义类引用，不会触发此类的初始化;

        引用常量不会触发此类初始化(常量在链接时就存入调用类的常量池中)

- 类加载器

    ![image-20200903113720293](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200903113720.png)

    - `getResourceAsStream(String str)`:获取类路径下的指定文件的输入流

        ```java
        InputStream in = this.getClass().getClassLoader().getResourceAsStream("exer2/test.properties");
        ```

        

## 创建运行时类对象并获取其完整结构

- 创建类的对象

  1. 调用Class对象的`newInstance()`
     - 类必须要有一个*无参*的构造器
     - 类的构造器访问权限足够, 通常为 public
  2. 若类没有无参构造器, 则先取得指定形参的构造器, 显式调用, 再实例化

- 获取对应的运行时类的属性

  - `Field[] getFields()` 获取类中及其父类中声明为public的属性
  - `Field[] getDeclaredFields()` 获取类本身声明的所有属性
    - `int getModifiers()` 以整数形式返回此Field的修饰符
    - `Class<?> getType()` 得到属性类型 
    - `String getName()` 返回属性名

- 获取对应的运行时类的方法

  - `Method[] getMethods()` 返回类或接口本身的public的方法
  - `Method[] getDeclaredMethods()` 返回类及父类的全部方法 
    - `Class<?> getReturnType()`取得全部的返回值  
    - `Class<?>[] getParameterTypes()` 取得全部的参数  
    - `int getModifiers()`取得修饰符
    - `Class<?>[] getExceptionTypes()` 取得异常信息

- 构造器

  - `public Constructor<T>[] getConstructors()`
    返回类的所有public构造方法
  - `public Constructor<T>[] getDeclaredConstructors()`
    返回此类声明的所有构造方法。
    - 取得修饰符: `public int getModifiers()`
    - 取得方法名称: `public String getName()` 
    - 取得参数的类型: `public Class<?>[] getParameterTypes()`

- 注解

  `getAnnotation(Class<T> annotationClass)`
  `getDeclaredAnnotations()`

- 泛型

  - 获取父类泛型类型:`Type getGenericSuperclass()` 
  - 泛型类型: `ParameterizedType` 
  - 获取实际的泛型类型参数数组: `getActualTypeArguments()`

- 类所在的包

  `Package getPackage()`



## 调用指定属性, 方法, 构造器

- 属性

  - `public Field getField(String name)` 返回属性名为name的public属性。
    `public Field getDeclaredField(String name)` 返回属性名为name的属性。

  - `public Object get(Object obj)` 取得指定对象obj上此Field的属性内容
    `public void set(Object obj,Object value)` 设置指定对象obj上此Field的属性内容
> 当类中属性设置为private，在使用set()和get()方法时，首先要使用Field类中的`setAccessible(true)`方法将需要操作的属性设置为可以被外部访问

- 方法

  1. 通过Class类的`getMethod(String name,Class...parameterTypes)`方法取得一个Method对象，并设置此方法操作时所需要的参数类型。 

  2. 调用Class.newInstance()

  3. 若原方法声明为private,则需要在调用invoke()方法前， 显式调用方法对象`setAccessible(true)`方法，将可访问 private的方法。

  4. 使用`Object invoke(Object obj, Object[] args)`进行调用，并向方法中传递要设置的obj对象的参数信息。

     

## 动态代理

- 代理模式: 使用一个代理将对象包装起来, 然后用该代理对象取代原始对象. 任何对原始对象的调用都要通过代理. 代理对象决定是否以及何时将方法调用转到原始对象

- 动态代理步骤

  1. 创建被代理的类, 接口
  2. 创建一个实现接口InvocationHandler的类，必须实现invoke方法，以完成代理的具体操作
  3. 通过Proxy类的静态方法`Object newProxyInstance(ClassLoader loader, Class[] interfaces, InvocationHandler h)` 创建一个代理类对象
  4. 当通过代理类对象发起对被重写的方法调用时, 会转换为`invoke()`调用
  
- AOP (Aspect Orient Programming)

  ![20200528-9cyVe4](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200528-9cyVe4.png)

  ![20200528-qk349Y](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200528-qk349Y.png)

# 网络编程

## 网络基础

- 如何实现网络中主机互相通信

  - 通信双方地址

  - 数据传输的规则: OSI模型, TCP/IP协议

    ![20200528-ACK9ib](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200528-ACK9ib.png)

- IP, 端口号

  - IP

    - 域名-(DNS)->IP

    - java.net.InetAddress类

      没有公共构造器, 提供2个静态方法获取实例:

      `getByName(String host)` 

      `getByAddress(byte[] addr)`

  - 端口号: 进程

    16位整数 0-65535. 其中0-1023被预先定义占用.

- 网络通信协议

  - TCP(Transmission Control Protocol)
    使用TCP协议前，须先采用“三次握手”方式建立连接 
    在连接中可进行大数据量的传输 
    传输完毕，需释放已建立的连接，"四次挥手"

    可靠但效率低

  - UDP(User Datagram Protocol)

    将数据、源、目的封装成数据包，不需要建立连接 

    每个数据报的大小限制在64K内 

    因无需连接，故是不可靠的 

    发送数据结束时无需释放资源，速度快

- Socket 套接字

  - 通信的两端都要有Socket，是两台机器间通信的端点 
  - Socket允许程序把网络连接当成一个流，数据在两个Socket间通过IO传输。
  - 一般主动发起通信的应用程序是客户端，等待通信请求的为服务端

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200528-QQTy0j.png)

  > 当server使用阻塞IO(如InputStream.read()), 在数据没有到达前，read 会挂起，进程会卡住. 需要client在发送完数据后, 显式告诉server发送完毕(`void shutdownOutput()`)

-  UDP通信

  1. DatagramSocket与DatagramPacket

     UDP数据报通过数据报套接字DatagramSocket发送和接收,

     DatagramPacket对象封装了UDP数据报，在数据报中包含了发送端的IP地址和端口号以及接收端的IP地址和端口号

  2. 建立发送端，接收端
  3. 建立数据包
  4. 调用Socket的发送、接收方法
  5. 关闭Socket

- URL编程

  java.net.URL类

  - URL的方法 `InputStream openStream()`:能从网络上读取数据
  - URLConnection: 要发送数据, 则先建立连接. 通过`URLConnection openConnection()`生成URLConnection对象

# Java8 新特性

## 接口的默认和静态方法

- 静态方法:使用 static 关键字修饰。可以通过接口直接调用静态方法，并执行 其方法体。我们经常在相互一起使用的类中使用静态方法。你可以在标准库中 找到像Collection/Collections或者Path/Paths这样成对的接口和类。

- 默认方法:默认方法使用 default 关键字修饰。可以通过实现类对象来调用。 我们在已有的接口中提供新方法的同时，还保持了与旧版本代码的兼容性。 比如:java 8 API中对Collection、List、Comparator等接口提供了丰富的默认 方法。

```java
public static void main( String[] args ) {
    Defaulable defaulable = DefaulableFactory.create( DefaultableImpl::new );
    System.out.println( defaulable.notRequired() );

    defaulable = DefaulableFactory.create( OverridableImpl::new );
    System.out.println( defaulable.notRequired() );
}
```

- 冲突问题

  - 若一个接口中定义了一个默认方法，而另外一个接口中也定义了一个同名同参数的方法(不管此方法是否是默认方法)，在实现类同时实现了这两个接口时，会出现接口冲突。

    **解决办法**:实现类必须覆盖接口中同名同参数的方法，来解决冲突。

    ```java
    interface Filial {// 孝顺的 
        default void help() {
    		System.out.println("老妈，我来救你了"); 
        }
    }
    interface Spoony {// 痴情的 
        default void help() {
    		System.out.println("媳妇，别怕，我来了"); 
        }
    }
    class Man implements Filial, Spoony { 
        @Override
    	public void help() { 
            System.out.println("我该怎么办呢?"); 
    		Filial.super.help();
    		Spoony.super.help();
    	} 
    }
    ```

    

  - 若一个接口中定义了一个默认方法，而父类中也定义了一个同名同参数的非抽象方法，则不会出现冲突问题。因为此时遵守**类优先**原则。接口中具有相同名称和参数的默认方法会被忽略。

    

## Lambda 表达式

- Lambda 是一个**匿名函数**，我们可以把 Lambda 表达式理解为是一段可以**传递**的代码(将代码像数据一样进行传递)。使用它可以写出更简洁、灵活的代码。

- 本质: **函数式**接口的**实例**

- 语法

  例: 

  ```java
  (o1, o2) -> Integer.compare(o1, o2);
  ```

  ->: lambda 操作符

  左边: lambda 形参列表(接口中抽象方法的形参列表)

  右边: lambda 体 (重写的抽象方法的方法体)

  

  使用总结: 

  - 左边: lambda 形参列表的参数类型可以省略(类型推断). 如果形参只有一个, 小括号也能省
  - 右边: 如果 lambda 体只有一条执行语句(可能是 return 语句), 可以省略大括号并同时删掉 return.

## 函数式接口

只含**一个抽象方法**的接口, 称为函数式接口. 

可以使用`@FunctionalInterface` 注解检验.

`java.util.function` :

- 内置四个核心函数式接口

  |           函数式接口           | 参数类型 | 返回类型 |                             用途                             |
  | :----------------------------: | :------: | :------: | :----------------------------------------------------------: |
  |   Consumer<T><br/>消费型接口   |    T     |   void   |        对类型为T的对象操作，方法: `void accept(T t)`         |
  |   Supplier<T><br/>供给型接口   |    \     |    T     |              返回类型为T的对象，方法:`T get()`               |
  | Function<T, R><br />函数型接口 |    T     |    R     | 对类型为T的对象操作，并返回结果。结果是R类型的对象。方法:`R apply(T t)` |
  |     Predicate<T>断定型接口     |    T     | boolean  | 确定类型为T的对象是否满足某约束，并返回 boolean 值。方法:`boolean test(T t)` |

  

- 其他接口

  ![image-20200806111352624](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200806111353.png)

## 方法引用和构造器引用

- 当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用.

- 要求: 实现接口的抽象方法的**参数列表**和**返回值类型**, 与方法引用的都一致.(针对下列情况一/二)

- 三种主要使用情况: `ClassName::methodName`

  - 对象::实例方法名

    ```java
    Consumer<String> con = x -> System.out.println(x);
    等于:
    Consumer<String> consumer = System.out::println;
    ```

    

  - 类::静态方法名

    ```java
    Comparator<Integer> com = (x, y) -> Integer.compare(x, y);
    等于:
    Comparator<Integer> comparator = Integer::compare;
    ```

    

  - 类::实例方法名

    当函数式接口方法的第一个参数是需要引用方法的调用者，并且第二个参数是需要引用方法的参数(或无参数)时

    ```java
    BiPredicate<String, String> biPredicate = (x,y) -> x.equals(y);
    等于:
    BiPredicate<String, String> bp = String::equals;
    ```

    

    ```java
    // Function中 R apply(T t)
    // Employee中 String getName()
    Employee employee = new Employee("Jerry", 23);
    
    Function<Employee, String> function = e -> e.getName();
    等于:
    Function<Employee, String> func = Employee::getName;
    ```

- 构造器引用 `ClassName::new`

  要求: 构造器**参数列表**要与接口中抽象方法的参数列表一致, 且方法的返回值即为构造器对应**类的对象**

  ```java
  Function<Integer, MyClass> function = (n) -> new MyClass(n);
  等于:
  Function<Integer, MyClass> function = MyClass::new;
  ```

- 数组引用 `type[]::new`

  ```java
  Function<Integer, Integer[]> function = (n) -> new Integer[n];
  等于:
  Function<Integer, Integer[]> function = Integer[]::new;
  ```

  

## Stream API

`java.util.stream`对集合的操作, 类似使用 SQL 执行数据库查询

- Stream 是什么?
  - Stream 关注的是数据的运算, 面向 cpu
  - 集合是一种静态的内存数据结构, 面向内存
  
- 特点
  1. Stream 自己不会存储元素。
  2. Stream 不会改变源对象。相反，他们会返回一个持有结果的新Stream。
  3. Stream 操作是延迟执行的。这意味着他们会等到需要结果的时候才执行。

- Stream 操作的三步

  1. 创建 

     一个数据源(如数组, 集合), 获取一个流

  2. 中间操作

     处理数据

  3. 终止

     执行终止操作才执行中间操作链, 并产生结果, 结果不再被使用

- 创建 Stream

  - 通过集合

    Collection 接口被扩展，提供了两个获取流 的方法:

    ```java
    List<Employee> employees = EmployeeData.getEmployees();
    
    // default Stream<E> stream() : 返回一个顺序流
    Stream<Employee> stream = employees.stream();
    // default Stream<E> parallelStream() : 返回一个并行流
    Stream<Employee> parallelStream = employees.parallelStream();
    ```

    

  - 通过数组

    Arrays 的静态方法 stream() 可以获取数组流:

    ```java
    int[] arr = new int[] {1, 2, 3};
    // static <T> Stream<T> stream(T[] array): 返回一个流
    IntStream stream = Arrays.stream(arr);
    ```

    重载形式，能够处理对应基本类型的数组:
    `public static IntStream stream(int[] array)`
    `public static LongStream stream(long[] array)`
    `public static DoubleStream stream(double[] array)`

  - 通过 Stream 的 of()

    调用Stream类静态方法 of(), 通过显示值创建一个流。它可以接收任意数量的参数
  
    ```java
    Stream<Integer> stream = Stream.of(1, 2, 3)
    ```
  
    
  
  - 无限流
  
    使用静态方法 `Stream.iterate()` 和 `Stream.generate()`, 创建无限流
  
    ```java
    // 迭代
    public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f) 
    // 生成
    public static<T> Stream<T> generate(Supplier<T> s)
    ```
  
- 筛选与切片

  |        方法         | 描述                                                         |
  | :-----------------: | :----------------------------------------------------------- |
  | filter(Predicate p) | 接收 Lambda ， 从流中排除某些元素                            |
  |     distinct()      | 筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素 |
  | limit(long maxSize) | 截断流，使其元素不超过给定数量                               |
  |    skip(long n)     | 跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一个空流。与 limit(n) 互补 |

  

- 映射

  ![image-20200806174000822](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200806174001.png)

- 排序

  | 方法                   | 描述                               |
  | ---------------------- | ---------------------------------- |
  | sorted()               | 产生一个新流，其中按自然顺序排序   |
  | sorted(Comparator com) | 产生一个新流，其中按比较器顺序排序 |

- 终止

  - 查找/匹配

    ![image-20200807092945651](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807092946.png)

    ![image-20200807093035379](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807093035.png)

  - 规约

    | 方法                             | 描述                                                      |
    | -------------------------------- | --------------------------------------------------------- |
    | reduce(T iden, BinaryOperator b) | 可以将流中元素反复结合起来，得到一 个值。返回 T           |
    | reduce(BinaryOperator b)         | 可以将流中元素反复结合起来，得到一 个值。返回 Optional<T> |

  - 收集

    | 方法                 | 描述                                                         |
    | -------------------- | ------------------------------------------------------------ |
    | collect(Collector c) | 将流转换为其他形式。接收一个 Collector 接口的实现，用于给Stream中元素做汇总 的方法 |

    Collector 接口中方法的实现决定了如何对流执行收集的操作(如收集到 List、Set、 Map)。

    另外， Collectors 实用类提供了很多静态方法，可以方便地创建常见收集器实例， 具体方法与实例如下表:

    ![image-20200807100514100](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807100514.png)

    ![image-20200807100623742](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807100624.png)

## Optional 类

Optional<T> 类(`java.util.Optional`) 是一个容器类，它可以保存类型T的值，代表 这个值存在。或者仅仅保存null，表示这个值不存在。原来用 null 表示一个值不 存在，现在 Optional 可以更好的表达这个概念。并且可以避免空指针异常.

![image-20200807101434895](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200807101435.png)

