<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Software Architecture](#software-architecture)
- [Design pattern](#design-pattern)
  - [单例 (Singleton)](#%E5%8D%95%E4%BE%8B-singleton)
  - [模板方法(TemplateMethod)](#%E6%A8%A1%E6%9D%BF%E6%96%B9%E6%B3%95templatemethod)
  - [装饰器(Decorator)](#%E8%A3%85%E9%A5%B0%E5%99%A8decorator)
- [Computer network](#computer-network)
  - [网络体系](#%E7%BD%91%E7%BB%9C%E4%BD%93%E7%B3%BB)
  - [IP地址(TODO)](#ip%E5%9C%B0%E5%9D%80todo)
  - [子网掩码及网络划分(TODO)](#%E5%AD%90%E7%BD%91%E6%8E%A9%E7%A0%81%E5%8F%8A%E7%BD%91%E7%BB%9C%E5%88%92%E5%88%86todo)
  - [ARP/RARP协议](#arprarp%E5%8D%8F%E8%AE%AE)
  - [路由选择协议](#%E8%B7%AF%E7%94%B1%E9%80%89%E6%8B%A9%E5%8D%8F%E8%AE%AE)
  - [TCP/IP(TODO)](#tcpiptodo)
  - [UDP](#udp)
  - [NAT协议](#nat%E5%8D%8F%E8%AE%AE)
  - [DHCP协议](#dhcp%E5%8D%8F%E8%AE%AE)
  - [HTTP(TODO)](#httptodo)
  - [SSL/TSL](#ssltsl)
  - [RESTful(Representational State Transfer)](#restfulrepresentational-state-transfer)
  - [举例](#%E4%B8%BE%E4%BE%8B)
- [容错/高可用/灾备](#%E5%AE%B9%E9%94%99%E9%AB%98%E5%8F%AF%E7%94%A8%E7%81%BE%E5%A4%87)
- [CAP定理](#cap%E5%AE%9A%E7%90%86)
- [Important flow charts](#important-flow-charts)
  - [spring 生命周期](#spring-%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
  - [TCP 三次握手四次挥手](#tcp-%E4%B8%89%E6%AC%A1%E6%8F%A1%E6%89%8B%E5%9B%9B%E6%AC%A1%E6%8C%A5%E6%89%8B)
      - [三次握手：](#%E4%B8%89%E6%AC%A1%E6%8F%A1%E6%89%8B)
      - [四次挥手：](#%E5%9B%9B%E6%AC%A1%E6%8C%A5%E6%89%8B)
  - [线程池执行流程图](#%E7%BA%BF%E7%A8%8B%E6%B1%A0%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B%E5%9B%BE)
      - [执行流程](#%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B)
      - [JDK提供了四种拒绝策略处理类](#jdk%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9B%9B%E7%A7%8D%E6%8B%92%E7%BB%9D%E7%AD%96%E7%95%A5%E5%A4%84%E7%90%86%E7%B1%BB)
  - [JVM内存结构](#jvm%E5%86%85%E5%AD%98%E7%BB%93%E6%9E%84)
      - [程序计数器（PC 寄存器）](#%E7%A8%8B%E5%BA%8F%E8%AE%A1%E6%95%B0%E5%99%A8pc-%E5%AF%84%E5%AD%98%E5%99%A8)
      - [Java虚拟机栈](#java%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%A0%88)
      - [本地方法栈](#%E6%9C%AC%E5%9C%B0%E6%96%B9%E6%B3%95%E6%A0%88)
      - [Java堆](#java%E5%A0%86)
      - [方法区](#%E6%96%B9%E6%B3%95%E5%8C%BA)
  - [Java内存模型](#java%E5%86%85%E5%AD%98%E6%A8%A1%E5%9E%8B)
  - [springMVC执行流程图](#springmvc%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B%E5%9B%BE)
  - [JDBC执行流程](#jdbc%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B)
      - [JDBC执行流程：](#jdbc%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B)
  - [spring cloud组件架构](#spring-cloud%E7%BB%84%E4%BB%B6%E6%9E%B6%E6%9E%84)
  - [dubbo  调用](#dubbo--%E8%B0%83%E7%94%A8)
- [Agile Development](#agile-development)
  - [迭代开发（Iterative development)](#%E8%BF%AD%E4%BB%A3%E5%BC%80%E5%8F%91iterative-development)
  - [增量开发 (Incremental development)](#%E5%A2%9E%E9%87%8F%E5%BC%80%E5%8F%91-incremental-development)
  - [敏捷开发的好处(Pros of agile development)](#%E6%95%8F%E6%8D%B7%E5%BC%80%E5%8F%91%E7%9A%84%E5%A5%BD%E5%A4%84pros-of-agile-development)
    - [早期交付](#%E6%97%A9%E6%9C%9F%E4%BA%A4%E4%BB%98)
    - [降低风险](#%E9%99%8D%E4%BD%8E%E9%A3%8E%E9%99%A9)
  - [如何进行每一次迭代 (How to agile develop)](#%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8C%E6%AF%8F%E4%B8%80%E6%AC%A1%E8%BF%AD%E4%BB%A3-how-to-agile-develop)
- [Code Review](#code-review)
- [Linux](#linux)
  - [What's Linux](#whats-linux)
  - [参考](#%E5%8F%82%E8%80%83)
  - [Basic](#basic)
  - [Unix vs. Linux](#unix-vs-linux)
  - [相关](#%E7%9B%B8%E5%85%B3)
    - [inode](#inode)
- [Data Structure & Algorithm](#data-structure--algorithm)
  - [队列](#%E9%98%9F%E5%88%97)
  - [链表](#%E9%93%BE%E8%A1%A8)
  - [栈](#%E6%A0%88)
  - [递归](#%E9%80%92%E5%BD%92)
  - [排序](#%E6%8E%92%E5%BA%8F)
  - [树](#%E6%A0%91)
  - [图](#%E5%9B%BE)
  - [常用算法](#%E5%B8%B8%E7%94%A8%E7%AE%97%E6%B3%95)
    - [二分查找(非递归)](#%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE%E9%9D%9E%E9%80%92%E5%BD%92)
    - [分治](#%E5%88%86%E6%B2%BB)
    - [动态规划](#%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92)
    - [KMP](#kmp)
    - [贪心](#%E8%B4%AA%E5%BF%83)
    - [普里姆](#%E6%99%AE%E9%87%8C%E5%A7%86)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Software Architecture

> [参考](http://www.ruanyifeng.com/blog/2016/09/software-architecture.html)

- 分层(layered architecture)

  - 分成若干水平层，每层都有清晰的角色和分工，不用知道其他层的细节。层与层之间通过接口通信

  - 最常见的四层结构:

    表现层（presentation）：用户界面，负责视觉和用户互动
    业务层（business）：实现业务逻辑
    持久层（persistence）：提供数据，SQL 语句就放在这一层
    数据库（database） ：保存数据

    有的软件在业务层和持久层之间，加了一个服务层（service），提供不同业务逻辑需要的一些通用接口。

  - 优:

    - 结构简单，容易理解和开发
    - 不同技能的程序员可以分工，负责不同的层，天然适合大多数软件公司的组织架构
    - 每一层都可以独立测试，其他层的接口通过模拟解决

  - 劣: 

    - 一旦环境变化，需要代码调整或增加功能时，通常比较麻烦和费时
    - 部署较麻烦，即使只改一个小地方，往往需要整个软件重新部署，不容易做持续发布
    - 软件升级时，可能需要整个服务暂停
    - 扩展性差。用户请求大量增加时，必须依次扩展每一层，由于每一层内部是耦合的，扩展会很困难

- 事件驱动(event-driven architecture)

  - 通过事件进行通信

    ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-16-060333.jpg)

  - 事件队列（event queue）：接收事件的入口

    分发器（event mediator）：将不同的事件分发到不同的业务逻辑单元

    事件通道（event channel）：分发器与处理器之间的联系渠道

    事件处理器（event processor）：实现业务逻辑，处理完成后会发出事件，触发下一步操作

  - 对于简单的项目，事件队列、分发器和事件通道，可以合为一体，整个软件就分成事件代理和事件处理器两部分。

  - 优:

    - 分布式的异步架构，事件处理器之间高度解耦，软件的扩展性好
    - 适用性广，各种类型的项目都可以用
    - 性能较好，因为事件的异步本质，软件不易产生堵塞
    - 事件处理器可以独立地加载和卸载，容易部署

  - 劣:

    - 涉及异步编程（要考虑远程通信、失去响应等情况），开发相对复杂
    - 难以支持原子性操作，因为事件通过会涉及多个处理器，难回滚
    - 分布式和异步特性导致这个架构较难测试

- 微核（microkernel architecture）/插件架构（plug-in architecture）

  - 软件的内核相对较小，主要功能和业务逻辑都通过插件实现。
  - 内核通常只包含系统运行的最小功能。插件则是互相独立的，插件之间的通信，应该减少到最低，避免出现互相依赖的问题。
  - 优:
    - 良好的功能延伸性（extensibility），需要什么功能，开发一个插件即可
    - 功能之间是隔离的，插件可以独立的加载和卸载，使得它比较容易部署，
    - 可定制性高，适应不同的开发需要
    - 可以渐进式地开发，逐步增加功能
  - 劣: 
    - 扩展性（scalability）差，内核通常是一个独立单元，不容易做成分布式
    - 开发难度相对较高，因为涉及到插件与内核的通信，以及内部的插件登记机制

- 微服务（microservices architecture）

  - 是服务导向架构（service-oriented architecture，缩写 SOA）的升级. 每一个服务就是一个独立的部署单元（separately deployed unit）。这些单元都是分布式的，互相解耦，通过远程通信协议（比如REST、SOAP）联系。
  - 三种实现模式
    - RESTful API 模式：服务通过 API 提供，云服务就属于这一类
    - RESTful 应用模式：服务通过传统的网络协议或者应用协议提供，背后通常是一个多功能的应用程序，常见于企业内部
    - 集中消息模式：采用消息代理（message broker），可以实现消息队列、负载均衡、统一日志和异常处理，缺点是会出现单点失败，消息代理可能要做成集群
  - 优
    - 扩展性好，各个服务之间低耦合
    - 容易部署，软件从单一可部署单元，被拆成了多个服务，每个服务都是可部署单元
    - 容易开发，每个组件都可以进行持续集成式的开发，可以做到实时部署，不间断地升级
    - 易于测试，可以单独测试每一个服务
  - 劣
    - 由于强调互相独立和低耦合，服务可能会拆分得很细。这导致系统依赖大量的微服务，变得很凌乱和笨重，性能也会不佳。
    - 一旦服务之间需要通信（即一个服务要用到另一个服务），整个架构就会变得复杂。典型的例子就是一些通用的 Utility 类，一种解决方案是把它们拷贝到每一个服务中去，用冗余换取架构的简单性。
    - 分布式的本质使得这种架构很难实现原子性操作，交易回滚会比较困难。

- 云 (cloud architecture）

  - 主要解决扩展性和并发的问题，是最容易扩展的架构.

    高扩展性，主要原因是没使用中央数据库，而是把数据都复制到内存中，变成可复制的内存数据单元。然后，业务处理能力封装成一个个处理单元（prcessing unit）。访问量增加，就新建处理单元；访问量减少，就关闭处理单元。由于没有中央数据库，所以扩展性的最大瓶颈消失了。由于每个处理单元的数据都在内存里，最好要进行数据持久化。

    ![img](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-16-061923.png)

  - 两部分：处理单元（processing unit）和虚拟中间件（virtualized middleware）。

    - 处理单元：实现业务逻辑
    - 虚拟中间件：负责通信、保持sessions、数据复制、分布式处理、处理单元的部署
      - 消息中间件（Messaging Grid）：管理用户请求和session，当一个请求进来以后，决定分配给哪一个处理单元。
      - 数据中间件（Data Grid）：将数据复制到每一个处理单元，即数据同步。保证某个处理单元都得到同样的数据。
      - 处理中间件（Processing Grid）：可选，如果一个请求涉及不同类型的处理单元，该中间件负责协调处理单元
      - 部署中间件（Deployment Manager）：负责处理单元的启动和关闭，监控负载和响应时间，当负载增加，就新启动处理单元，负载减少，就关闭处理单元。

  - 优

    - 高负载，高扩展性
    - 动态部署

  - 劣

    - 实现复杂，成本较高
    - 主要适合网站类应用，不合适大量数据吞吐的大型数据库应用
    - 较难测试

# Design pattern

[refer](https://refactoringguru.cn/design-patterns/catalog)

图文并茂讲设计模式!

## 单例 (Singleton)

- 某个类只能存在一个对象实例, 并且该类只提供一个取得其对象实例的方法

  ```java
  // 饿汉式
  class Singleton {
      // 1.私有化构造器
  	private Singleton() {}
  
  	// 3.此实例也必须静态化
  	private static Singleton single = new Singleton();
      // 2.提供公共的静态的方法，返回当前类的对象 
      public static Singleton getInstance() {
      	return single; 
  	}
  }
  
  // 懒汉式
  class Singleton {
      // 1.私有化构造器
      private Singleton() {}
      
      // 3.此实例也必须静态化
      private static Singleton single;
      // 2.提供公共的静态的方法，返回当前类的对象 
      public static Singleton getInstance() {
          if(single == null) {
          	single = new Singleton();
          }
          return single; 
      }
  }
  // 这里的懒汉式还存在线程安全问题，可修复
  ```

- 优点

  由于单例模式只生成一个实例，**减少了系统性能开销**，当一个对象的产生需要比较多的资源时，如读取配置、产生其他依赖对象时，则可以通过在应用启动时直接产生一个单例对象，然后永久驻留内存的方式来解决。如 `java.lang.Runtime`的实现

- 应用

  - 网站的**计数器**，一般也是单例模式实现，否则难以同步。

  - 应用程序的**日志**应用，一般都使用单例模式实现，这一般是由于共享的日志

    文件一直处于打开状态，因为只能有一个实例去操作，否则内容不好追加。

  - **数据库连接池**的设计一般也是采用单例模式，因为数据库连接是一种数据库资源。

  - 项目中，**读取配置文件的类**，一般也只有一个对象。没有必要每次使用配置文件数据，都生成一个对象去读取。

  - Application 也是单例的典型应用

  - Windows的Task Manager (**任务管理器**)就是很典型的单例模式

  - Windows的Recycle Bin (**回收站**)也是典型的单例应用。在整个系统运行过程中，回收站一直维护着仅有的一个实例。

## 模板方法(TemplateMethod)

- 解决的问题:

  当功能内部一部分实现是确定的，一部分实现是不确定的。这时可以把不确定的部分暴露出去，让子类去实现。

  换句话说，在软件开发中实现一个算法时，整体步骤很固定、通用， 这些步骤已经在父类中写好了。但是某些部分易变，易变部分可以抽象出来，供不同子类实现。

  ```java
  abstract class Template {
      public final void getTime() {
          long start = System.currentTimeMillis();
          code();
          long end = System.currentTimeMillis();
          System.out.println("执行时间是:" + (end - start));
  	}
  	public abstract void code(); 
  }
  
  class SubTemplate extends Template { 
      public void code() {
  		for (int i = 0; i < 10000; i++) {
              System.out.println(i);
          }
      }
  }
  ```

- 应用

  - 数据库访问的封装
  - Junit单元测试
  - JavaWeb的Servlet中关于doGet/doPost方法调用  
  - Hibernate中模板程序
  - Spring中JDBCTemlate、HibernateTemplate等

## 装饰器(Decorator)

**装饰模式**是一种结构型设计模式，允许你通过将对象放入包含行为的特殊封装对象中来为原对象绑定新的行为。

![image-20201215163032675](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201215163032.png)

- 应用场景:

    1. 无需修改代码的情况下即可使用对象，且希望**在运行时**为对象新增额外的行为
    2. 继承难以实现或不可行(比如`final`限制了扩展)

- 优缺点

    优: 

    -  无需创建新子类即可扩展对象的行为。
    -  可以在运行时添加或删除对象的功能。
    -  可以用多个装饰封装对象来组合几种行为。
    -  *单一职责原则*。 可以将实现了许多不同行为的一个大类拆分为多个较小的类。

    缺:

    -  在封装器栈中删除特定封装器困难。
    -  实现行为不受装饰栈顺序影响的装饰困难。
    -  各层的初始化配置代码看上去可能会很糟糕。

# Computer network

> [参考1](https://juejin.im/post/5ad7e6c35188252ebd06acfa)
>
> [refer2](https://www.cnblogs.com/maybe2030/p/4781555.html)

## 网络体系

- `OSI`体系结构：概念清楚 & 理念完整，但复杂 & 不实用

  ![20200628UiIt6f](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628UiIt6f.jpg)

- `TCP` / `IP`体系结构：含了一系列构成互联网基础的网络协议，是`Internet`的核心协议 & 被广泛应用于局域网 和 广域网

  ![20200628bIxx6C](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628bIxx6C.jpg)

- 五层体系结构：融合了`OSI` 与 `TCP` / `IP`的体系结构，目的是为了学习 & 讲解计算机原理

补充:

1. 物理层（Physical Layer）

   - 重要设备: 中继器（Repeater，也叫放大器), 集线器

2. 数据链路层（Data Link Layer）

   - 主要的协议：以太网协议(链路层与物理层之间)

   - 重要设备：网桥, 交换机

3. 网络层（Network Layer）

   - 基本数据单位: 数据报(Datagram)
   - 重要设备：路由器

4. 传输层（Transport Layer）

   - 重要设备：网关

## IP地址(TODO)

- iP地址分为IPv4和IPv6两种。IPv4采用32位地址，类似`101.202.99.12`，而IPv6采用128位地址，类似`2001:0DA8:100A:0000:0000:1020:F2F3:1428`。

- IP地址又分为公网IP地址和内网IP地址。公网IP地址可以直接被访问，内网IP地址只能在内网访问。

    有一个特殊的IP地址，称之为本机地址，它总是`127.0.0.1`。

- IPv4地址实际上是一个32位整数。例如：

```asciiarmor
106717964 = 0x65ca630c
          = 65  ca  63 0c
          = 101.202.99.12
```

- 如果两台计算机位于同一个网络，那么他们之间可以直接通信，因为他们的IP地址前段是相同的，也就是**网络号是相同**的。网络号是IP地址通过子网掩码过滤后得到的。例如：

    某台计算机的IP是`101.202.99.2`，子网掩码是`255.255.255.0`，那么计算该计算机的网络号是：

```
IP = 101.202.99.2
Mask = 255.255.255.0
Network = IP & Mask = 101.202.99.0
```

每台计算机都需要正确配置IP地址和子网掩码，根据这两个就可以计算网络号，如果两台计算机计算出的网络号相同，说明两台计算机在同一个网络，可以直接通信。

如果两台计算机计算出的网络号不同，那么两台计算机不在同一个网络，不能直接通信，它们之间必须通过路由器或者交换机这样的网络设备间接通信，我们把这种设备称为网关。

- 网关的作用就是连接多个网络，负责把来自一个网络的数据包发到另一个网络，这个过程叫路由。

    所以，一台计算机的一个网卡会有3个关键配置：

    - IP地址，例如：`10.0.2.15`
    - 子网掩码，例如：`255.255.255.0`
    - 网关的IP地址，例如：`10.0.2.2` 

## 子网掩码及网络划分(TODO)

计算子网掩码时，注意IP地址中的保留地址，即“ 0”地址和广播地址，它们是指主机地址或网络地址全为“ 0”或“ 1”时的IP地址，它们代表着本网络地址和广播地址，一般是不能被计算在内的。

## ARP/RARP协议

- 地址解析协议，即ARP（Address Resolution Protocol），是根据IP地址获取物理地址的一个TCP/IP协议。
- ARP命令可用于查询本机ARP缓存中IP地址和MAC地址的对应关系、添加或删除静态对应关系等。
- 逆地址解析协议，即RARP，功能和ARP协议相对，其将局域网中某个主机的物理地址转换为IP地址，

## 路由选择协议
  - RIP协议 ：底层是贝尔曼福特算法，它选择路由的度量标准（metric)是跳数，最大跳数是15跳，如果大于15跳，它就会丢弃数据包。
  - OSPF协议 ：Open Shortest Path First开放式最短路径优先，底层是迪杰斯特拉算法，是链路状态路由选择协议，它选择路由的度量标准是带宽，延迟。
## TCP/IP(TODO)

> [refer](https://www.jianshu.com/p/65605622234b)

- 由网络层的IP协议和传输层的TCP(Transmission Control Protocol)协议组成。
- 总结: TCP负责发现传输的问题，一有问题就发出信号，要求重新传输，直到所有数据安全正确地传输到目的地。而IP是给因特网的每一台联网设备规定一个地址。
- 基于TCP的应用层协议
  FTP（文件传输协议）、Telnet（远程登录协议）、SMTP（简单邮件传输协议）、POP3（和SMTP相对，用于接收邮件）、HTTP协议等
- TCP报文首部格式
  ![20200628fSRSfz](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628fSRSfz.jpg)
- TCP的三次握手, 四次挥手
  ![image-20190803095209464](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051332.jpg)
- 三次握手
1. 第一次握手：建立连接。客户端发送连接请求报文段，将SYN位置为1，Sequence Number为x；然后，客户端进入SYN_SEND状态，等待服务器的确认；

2. 第二次握手：服务器收到SYN报文段。服务器收到客户端的SYN报文段，需要对这个SYN报文段进行确认，设置Acknowledgment Number为x+1(Sequence Number+1)；同时，自己自己还要发送SYN请求信息，将SYN位置为1，Sequence Number为y；服务器端将上述所有信息放到一个报文段（即SYN+ACK报文段）中，一并发送给客户端，此时服务器进入SYN_RECV状态；

3. 第三次握手：客户端收到服务器的SYN+ACK报文段。然后将Acknowledgment Number设置为y+1，向服务器发送ACK报文段，这个报文段发送完毕以后，客户端和服务器端都进入ESTABLISHED状态，完成TCP三次握手。
    完成了三次握手，客户端和服务器端就可以开始传送数据。

  - 四次分手

  当数据传送完毕，要断开TCP连接。那对于TCP的断开连接，就有“四次分手”。

4. 第一次分手：主机1（可以使客户端，也可以是服务器端），设置Sequence Number和Acknowledgment Number，向主机2发送一个FIN报文段；此时，主机1进入FIN_WAIT_1状态；这表示主机1没有数据要发送给主机2了；

5. 第二次分手：主机2收到了主机1发送的FIN报文段，向主机1回一个ACK报文段，Acknowledgment Number为Sequence Number加1；主机1进入FIN_WAIT_2状态；主机2告诉主机1，我“同意”你的关闭请求；

6. 第三次分手：主机2向主机1发送FIN报文段，请求关闭连接，同时主机2进入LAST_ACK状态；

7. 第四次分手：主机1收到主机2发送的FIN报文段，向主机2发送ACK报文段，然后主机1进入TIME_WAIT状态；主机2收到主机1的ACK报文段以后，就关闭连接；此时，主机1等待2MSL后依然没有收到回复，则证明Server端已正常关闭，那好，主机1也可以关闭连接了。
  - 为什么要三次挥手？
    在只有两次“握手”的情形下，假设Client想跟Server建立连接，但是却因为中途连接请求的数据报丢失了，故Client端不得不重新发送一遍；这个时候Server端仅收到一个连接请求，因此可以正常的建立连接。但是，有时候Client端重新发送请求不是因为数据报丢失了，而是有可能数据传输过程因为网络并发量很大在某结点被阻塞了，这种情形下Server端将先后收到2次请求，并持续等待两个Client请求向他发送数据...问题就在这里，Cient端实际上只有一次请求，而Server端却有2个响应，极端的情况可能由于Client端多次重新发送请求数据而导致Server端最后建立了N多个响应在等待，因而造成极大的资源浪费！所以，“三次握手”很有必要！
    
  - 为什么要四次挥手？
    试想一下，假如现在你是客户端你想断开跟Server的所有连接该怎么做？第一步，你自己先停止向Server端发送数据，并等待Server的回复。但事情还没有完，虽然你自身不往Server发送数据了，但是因为你们之前已经建立好平等的连接了，所以此时他也有主动权向你发送数据；故Server端还得终止主动向你发送数据，并等待你的确认。其实，就是保证双方的一个合约的完整执行！
    
  - 为什么要等待 2MSL?

    MSL：报文段最大生存时间，它是任何报文段被丢弃前在网络内的最长时间。
    原因有二：

    - 保证TCP协议的全双工连接能够可靠关闭
    - 保证这次连接的重复数据段从网络中消失

    第一点：如果主机1直接CLOSED了，那么由于IP协议的不可靠性或者是其它网络原因，导致主机2没有收到主机1最后回复的ACK。那么主机2就会在超时之后继续发送FIN，此时由于主机1已经CLOSED了，就找不到与重发的FIN对应的连接。所以，主机1不是直接进入CLOSED，而是要保持TIME_WAIT，当再次收到FIN的时候，能够保证对方收到ACK，最后正确的关闭连接。

    第二点：如果主机1直接CLOSED，然后又再向主机2发起一个新连接，我们不能保证这个新连接与刚关闭的连接的端口号是不同的。也就是说有可能新连接和老连接的端口号是相同的。一般来说不会发生什么问题，但是还是有特殊情况出现：假设新连接和已经关闭的老连接端口号是一样的，如果前一次连接的某些数据仍然滞留在网络中，这些延迟数据在建立新连接之后才到达主机2，由于新连接和老连接的端口号是一样的，TCP协议就认为那个延迟的数据是属于新连接的，这样就和真正的新连接的数据包发生混淆了。所以TCP连接还要在TIME_WAIT状态等待2倍MSL，这样可以保证本次连接的所有数据都从网络中消失。

- 流量控制

    让发送方的发送速率不要太快，要让接收方来得及接收.

    **滑动窗口机制**可以很方便地在TCP连接上实现对**发送方**的流量控制.

    ![TCP](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201221160918.dat)

- 拥塞控制

    - 与 流量控制 区别

    | 类型     | 范围   | 对象                      | 实际措施             |
    | -------- | ------ | ------------------------- | -------------------- |
    | 拥塞控制 | 全局   | 整个通信网络(主机&路由器) | 防止过多数据涌入网络 |
    | 流量控制 | 端对端 | 发送端                    | 降低发送端发送速率   |

    - 慢开始 & 拥塞避免

        发送方维持一个拥塞窗口 cwnd ( congestion window )的状态变量。拥塞窗口的大小取决于网络的拥塞程度，并且动态地在变化。发送方让自己的发送窗口等于拥塞窗口。

        ![20201221170447](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201221170447.jpg)

    - 快重传 & 快恢复

        快重传算法首先要求接收方每收到一个失序的报文段后就立即发出重复确认（为的是使发送方及早知道有报文段没有到达对方）

        发送方只要一连收到**三个重复确认**就应当立即重传对方尚未收到的报文段，而不必继续等待设置的重传计时器到期。

        ![20201221171226](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201221171226.jpg)

## UDP

- 用户数据报协议 User Datagram Protocol
  ![20200628gtr1ef](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628gtr1ef.jpg)

  优点: 速度快; 

  缺点: 消息易丢失

- 基于`UDP`的应用层协议

  域名转换：`DNS`协议, 文件传输：`FTP`协议, 网络管理：`SNMP`协议, 远程文件服务器：`NFS`协议

- TCP, UDP 比较

  ![20200628zE4PeL](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628zE4PeL.jpg)
## NAT协议
  NAT网络地址转换(Network Address Translation)属接入广域网(WAN)技术，是一种将私有（保留）地址转化为合法IP地址的转换技术，它被广泛应用于各种类型Internet接入方式和各种类型的网络中。原因很简单，NAT不仅完美地解决了lP地址不足的问题，而且还能够有效地避免来自网络外部的攻击，隐藏并保护网络内部的计算机。
## DHCP协议
  DHCP动态主机设置协议（Dynamic Host Configuration Protocol）是一个局域网的网络协议，使用UDP协议工作，主要有两个用途：给内部网络或网络服务供应商自动分配IP地址，给用户或者内部网络管理员作为对所有计算机作中央管理的手段。
## HTTP(TODO)

> [refer](https://www.jianshu.com/p/a6d086a3997d)

![20200628oUQ3h7](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628oUQ3h7.jpg)
- HTTP 协议包括哪些请求？
  GET：请求读取由URL所标志的信息。
  POST：给服务器添加信息（如注释）。
  PUT：在给定的URL下存储一个文档。
  DELETE：删除给定的URL所标志的资源。
- HTTP 中， POST 与 GET 的区别
1. Get是从服务器上获取数据，Post是向服务器传送数据。
2. Get是把参数数据队列加到提交表单的Action属性所指向的URL中，值和表单内各个字段一一对应，在URL中可以看到。
3. Get传送的数据量小，不能大于2KB；Post传送的数据量较大，一般被默认为不受限制。
4. 根据HTTP规范，GET用于信息获取，而且应该是安全的和幂等的。
   - 所谓 安全的 意味着该操作用于获取信息而非修改信息。换句话说，GET请求一般不应产生副作用。就是说，它仅仅是获取资源信息，就像数据库查询一样，不会修改，增加数据，不会影响资源的状态。
   - *幂等* 意味着对同一URL的多个请求应该返回同样的结果。

## SSL/TSL

[refer](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html) [refer2](http://www.ruanyifeng.com/blog/2014/02/ssl_tls.html)

SSL/TLS协议的基本过程是这样的：

（1） 客户端向服务器端索要并验证公钥。

（2） 双方协商生成"对话密钥"。

（3） 双方采用"对话密钥"进行加密通信。

前两步称为"握手"(handshake)

详细过程:

![img](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201221094942.png)

第一步，Client(以下简写为 C)给出协议版本号、一个客户端生成的随机数（Client random），以及客户端支持的加密方法。

第二步，Server(以下简写为 S)确认双方使用的加密方法，并给出数字证书、以及一个服务器生成的随机数（Server random）。

第三步，C确认数字证书有效，然后生成一个新的随机数（Premaster secret），并使用数字证书中的公钥，加密这个随机数，发给S。

第四步，S使用自己的私钥，获取C发来的随机数（即Premaster secret）。

第五步，C和S根据约定的加密方法，使用前面的三个随机数，生成"对话密钥"（session key），用来加密接下来的整个对话过程。

## RESTful(Representational State Transfer)

> [refer](https://www.ruanyifeng.com/blog/2011/09/restful.html)

- Resource 资源: 信息实体,uri

- Representation 表现层: eg: 文本可以用txt, HTML, XML格式表现

- State Transfer 状态转化: HTTP协议中 GET用来获取资源，POST用来新建资源（也可以用于更新资源），PUT用来更新资源，DELETE用来删除资源

- [设计细节](https://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html)

## 举例
在浏览器中输入 www.baidu.com  后执行的全部过程
1）客户端浏览器通过DNS解析到 www.baidu.com 的IP地址220.181.38.148，通过这个IP地址找到客户端到服务器的路径。客户端浏览器发起一个HTTP会话到220.181.38.148，然后通过TCP进行封装数据包，输入到网络层。

　　2）在客户端的传输层，把HTTP会话请求分成报文段，添加源和目的端口，如服务器使用80端口监听客户端的请求，客户端由系统随机选择一个端口如5000，与服务器进行交换，服务器把相应的请求返回给客户端的5000端口。然后使用IP层的IP地址查找目的端。

　　3）客户端的网络层不用关系应用层或者传输层的东西，主要做的是通过查找路由表确定如何到达服务器，期间可能经过多个路由器，这些都是由路由器来完成的工作，不作过多的描述，无非就是通过查找路由表决定通过那个路径到达服务器。

　　4）客户端的链路层，包通过链路层发送到路由器，通过邻居协议查找给定IP地址的MAC地址，然后发送ARP请求查找目的地址，如果得到回应后就可以使用ARP的请求应答交换的IP数据包现在就可以传输了，然后发送IP数据包到达服务器的地址。
　　![20200628mkCSAo](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200628mkCSAo.jpg)




# 容错/高可用/灾备

- 容错：发生故障时，如何让系统继续运行。

- 高可用：系统中断时，如何尽快恢复。

- 灾备：系统毁灭时，如何抢救数据。


>  [参考](http://www.ruanyifeng.com/blog/2019/11/fault-tolerance.html)

# CAP定理

[reference](http://www.ruanyifeng.com/blog/2018/07/cap.html)

![img](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20210129152817.jpg)

- Consistency 一致性
- Availability 可用性
- Partition tolerance 分区容错性



- **P**

    大多数分布式系统都分布在多个子网络。每个子网络就叫做一个区（partition）。分区容错的意思是，区间通信可能失败. 

    一般来说，分区容错无法避免，因此可以认为 CAP 的 P 总是成立。CAP 定理告诉我们，剩下的 C 和 A 无法同时做到。

- **C**

    一致性是因为多个数据拷贝下并发读写才有的问题

    对于一致性，可以分为从客户端和服务端两个不同的视角。

    - 客户端

    从客户端来看，一致性主要指的是多并发访问时更新过的数据如何获取的问题。

    - 服务端

    从服务端来看，则是更新如何分布到整个系统，以保证数据最终一致。

    

    对于一致性，可以分为强/弱/最终一致性三类

    从客户端角度，多进程并发访问时，更新过的数据在不同进程如何获取的不同策略，决定了不同的一致性。

    - 强一致性

    对于关系型数据库，要求更新过的数据能被后续的访问都能看到，这是强一致性。

    - 弱一致性

    如果能容忍后续的部分或者全部访问不到，则是弱一致性。

    - 最终一致性

    如果经过一段时间后要求能访问到更新后的数据，则是最终一致性。

- **A**

    只要收到用户的请求，服务器就必须给出回应

- CAP权衡
    通过CAP理论，我们知道无法同时满足一致性、可用性和分区容错性这三个特性，那要舍弃哪个呢？

    >  CP without A：如果不要求A（可用），相当于每个请求都需要在Server之间强一致，而P（分区）会导致同步时间无限延长，如此CP也是可以保证的。很多传统的数据库分布式事务都属于这种模式。
    > AP wihtout C：要高可用并允许分区，则需放弃一致性。一旦分区发生，节点之间可能会失去联系，为了高可用，每个节点只能用本地数据提供服务，而这样会导致全局数据的不一致性。现在众多的NoSQL都属于此类。

对于多数大型互联网应用的场景，主机众多、部署分散，而且现在的集群规模越来越大，所以节点故障、网络故障是常态，而且要保证服务可用性达到N个9，即保证P和A，舍弃C（退而求其次保证最终一致性）。虽然某些地方会影响客户体验，但没达到造成用户流程的严重程度。

对于涉及到钱财这样不能有一丝让步的场景，C必须保证。网络发生故障宁可停止服务或者只读不写，这是保证CP，舍弃A。

# Important flow charts

> [Resource](https://juejin.im/post/5d214639e51d4550bf1ae8df)

## spring 生命周期

![image-20190803092851803](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-11-080800.jpg)

- 首先容器启动后，对bean进行初始化
- 按照bean的定义，注入属性
- 检测该对象是否实现了xxxAware接口，并将相关的xxxAware实例注入给bean，如BeanNameAware等
- 以上步骤，bean对象已正确构造，通过实现BeanPostProcessor接口，可以再进行一些自定义方法处理。如:postProcessBeforeInitialzation
- BeanPostProcessor的前置处理完成后，可以实现postConstruct，afterPropertiesSet,init-method等方法，
  增加我们自定义的逻辑，
- 通过实现BeanPostProcessor接口，进行postProcessAfterInitialzation后置处理
- 接着Bean准备好被使用啦。
- 容器关闭后，如果Bean实现了DisposableBean接口，则会回调该接口的destroy()方法
- 通过给destroy-method指定函数，就可以在bean销毁前执行指定的逻



## TCP 三次握手四次挥手

![image-20190803095051188](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051334.jpg)

#### 三次握手：

- 第一次握手(SYN=1, seq=x)，发送完毕后，客户端进入 SYN_SEND 状态
- 第二次握手(SYN=1, ACK=1, seq=y, ACKnum=x+1)， 发送完毕后，服务器端进入 SYN_RCVD 状态。
- 第三次握手(ACK=1，ACKnum=y+1)，发送完毕后，客户端进入 ESTABLISHED 状态，当服务器端接收到这个包时，也进入 ESTABLISHED 状态，TCP 握手，即可以开始数据传输。

#### 四次挥手：

- 第一次挥手(FIN=1，seq=a)，发送完毕后，客户端进入 FIN_WAIT_1 状态
- 第二次挥手(ACK=1，ACKnum=a+1)，发送完毕后，服务器端进入 CLOSE_WAIT 状态，客户端接收到这个确认包之后，进入 FIN_WAIT_2 状态
- 第三次挥手(FIN=1，seq=b)，发送完毕后，服务器端进入 LAST_ACK 状态，等待来自客户端的最后一个ACK。
- 第四次挥手(ACK=1，ACKnum=b+1)，客户端接收到来自服务器端的关闭请求，发送一个确认包，并进入 TIME_WAIT状态，等待了某个固定时间（两个最大段生命周期，2MSL，2 Maximum Segment Lifetime）之后，没有收到服务器端的 ACK ，认为服务器端已经正常关闭连接，于是自己也关闭连接，进入 CLOSED 状态。服务器端接收到这个确认包之后，关闭连接，进入 CLOSED 状态。

## 线程池执行流程图

线程池：一种线程使用模式。线程过多会带来调度开销，进而影响缓存局部性和整体性能。而线程池维护着多个线程，等待着监督管理者分配可并发执行的任务，这避免了在处理短时间任务时创建与销毁线程的代价。线程池执行流程是每个开发必备的。

![image-20190803095248211](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051341.jpg)

#### 执行流程

- 提交一个任务，线程池里存活的核心线程数小于线程数corePoolSize时，线程池会创建一个核心线程去处理提交的任务。
- 如果线程池核心线程数已满，即线程数已经等于corePoolSize，一个新提交的任务，会被放进任务队列workQueue排队等待执行。
- 当线程池里面存活的线程数已经等于corePoolSize了,并且任务队列workQueue也满，判断线程数是否达到maximumPoolSize，即最大线程数是否已满，如果没到达，创建一个非核心线程执行提交的任务。
- 如果当前的线程数达到了maximumPoolSize，还有新的任务过来的话，直接采用拒绝策略处理。

#### JDK提供了四种拒绝策略处理类

- AbortPolicy(抛出一个异常，默认的)
- DiscardPolicy(直接丢弃任务)
- DiscardOldestPolicy（丢弃队列里最老的任务，将当前这个任务继续提交给线程池）
- CallerRunsPolicy（交给线程池调用所在的线程进行处理)

## JVM内存结构

![image-20190803095341342](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051353.jpg)

#### 程序计数器（PC 寄存器）

程序计数器是一块较小的内存空间，可以看作当前线程所执行的字节码的行号指示器。在虚拟机的模型里，字节码解释器工作时就是通过改变这个计数器的值来选取下一条需要执行的字节码指令，分支、循环、异常处理、线程恢复等基础功能都需要依赖计数器完成。

#### Java虚拟机栈

- 与程序计数器一样，Java虚拟机栈也是线程私有的，它的生命周期与线程相同
- 每个方法被执行的时候都会创建一个"栈帧",用于存储局部变量表(包括参数)、操作数栈、动态链接、方法出口等信息。每个方法被调用到执行完的过程，就对应着一个栈帧在虚拟机栈中从入栈到出栈的过程。
- 局部变量表存放各种基本数据类型boolean、byte、char、short等

#### 本地方法栈

与虚拟机栈基本类似，区别在于虚拟机栈为虚拟机执行的java方法服务，而本地方法栈则是为Native方法服务。

#### Java堆

- GC堆是java虚拟机所管理的内存中最大的一块内存区域，也是被各个线程共享的内存区域，在JVM启动时创建。
- 其大小通过-Xms(最小值)和-Xmx(最大值)参数设置，-Xms为JVM启动时申请的最小内存，-Xmx为JVM可申请的最大内存。
- 由于现在收集器都是采用分代收集算法，堆被划分为新生代和老年代。新生代由S0和S1构成，可通过-Xmn参数来指定新生代的大小。
- 所有对象实例以及数组都在堆上分配。
- Class文件中除了有类的版本、字段、方法、接口等描述信息外，还有一项信息是常量池，用于存放编译器生成的各种符号引用，这部分内容将在类加载后放到方法区的运行时常量池中。

#### 方法区

- 也称”永久代” ，它用于存储虚拟机加载的类信息、常量、静态变量、是各个线程共享的内存区域。可以通过-XX:PermSize 和 -XX:MaxPermSize 参数限制方法区的大小。
- 运行时常量池：是方法区的一部分，其中的主要内容来自于JVM对Class的加载。
- Class文件中除了有类的版本、字段、方法、接口等描述信息外，还有一项信息是常量池，用于存放编译器生成的各种符号引用，这部分内容将在类加载后放到方法区的运行时常量池中。

## Java内存模型

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051401.jpg)

Java的多线程之间是通过共享内存进行通信的，在通信过程中会存在一系列如可见性、原子性、顺序性等问题，而JMM就是围绕着多线程通信以及与其相关的一系列特性而建立的模型。JMM定义了一些语法集，这些语法集映射到Java语言中就是volatile、synchronized等关键字。有兴趣可以看看我的另外一篇笔记：[www.jianshu.com/p/3c1691aed…](https://link.juejin.im?target=https%3A%2F%2Fwww.jianshu.com%2Fp%2F3c1691aed1a5)

Java内存模型规定了所有的变量都存储在主内存中，每条线程还有自己的工作内存，线程的工作内存中保存了该线程中是用到的变量的主内存副本拷贝，线程对变量的所有操作都必须在工作内存中进行，而不能直接读写主内存。不同的线程之间也无法直接访问对方工作内存中的变量，线程间变量的传递均需要自己的工作内存和主存之间进行数据同步进行。

## springMVC执行流程图

![image-20190803095423420](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-11-080754.jpg)

User向服务器发送request,前端控制Servelt DispatcherServlet捕获;

DispatcherServlet对请求URL进行解析，调用HandlerMapping获得该Handler配置的所有相关的对象，最后以HandlerExecutionChain对象的形式返回.

DispatcherServlet 根据获得的Handler，选择一个合适的HandlerAdapter.

提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)

Handler执行完成后，返回一个ModelAndView对象到DispatcherServlet

根据返回的ModelAndView，选择一个适合的ViewResolver

ViewResolver 结合Model和View，来渲染视图

将渲染结果返回给客户端。

## JDBC执行流程

![image-20190803144141579](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051404.jpg)

#### JDBC执行流程：

- 连接数据源
- 为数据库传递查询和更新指令
- 处理数据库响应并返回的结果



## spring cloud组件架构

Spring Cloud是一个基于Spring Boot实现的云原生应用开发工具，它为基于JVM的云原生应用开发中涉及的配置管理、服务发现、熔断器、智能路由、微代理、控制总线、分布式会话和集群状态管理等操作提供了一种简单的开发方式。

![image-20190803095629224](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-11-075848.jpg)

Eureka 负责服务的注册与发现。

Hystrix 负责监控服务之间的调用情况，起到熔断,降级作用。

Spring Cloud Config 提供了统一的配置中心服务。

所有对外的请求和服务，我们都通过Zuul来进行转发，起到 API 网关的作用

最后我们使用 Sleuth+Zipkin 将所有的请求数据记录下来，方便我们进行后续分析。

Spring Cloud Ribbon是基于Netflix Ribbon实现的一套客户端负载均衡的工具。 它是一个基于HTTP和TCP的客户端负载均衡器。

Feign是一个声明式的Web Service客户端，它的目的就是让Web Service调用更加简单。



## dubbo  调用

Dubbo是一个分布式服务框架，致力于提供高性能和透明化的远程服务调用方案，这容易和负载均衡弄混，负载均衡是对外提供一个公共地址，请求过来时通过轮询、随机等，路由到不同server。

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051409.jpg)

# Agile Development

[Resource](http://www.ruanyifeng.com/blog/2019/03/agile-development.html)

## 迭代开发（Iterative development)

**迭代开发将一个大任务，分解成多次连续的开发，本质就是逐步改进。**

> 开发者先快速发布一个有效但不完美的最简版本，然后不断迭代。每一次迭代都包含规划、设计、编码、测试、评估五个步骤，不断改进产品，添加新功能。通过频繁的发布，以及跟踪对前一次迭代的反馈，最终接近较完善的产品形态。

## 增量开发 (Incremental development)

**软件的每个版本，都会新增一个用户可以感知的完整功能。也就是说，按照新增功能来划分迭代。**

> 举例来说，房产公司开发一个10栋楼的小区。如果采用增量开发的模式，该公司第一个迭代就是交付一号楼，第二个迭代交付二号楼......每个迭代都是完成一栋完整的楼。

## 敏捷开发的好处(Pros of agile development)

### 早期交付

**早期交付，从而大大降低成本。**

> 还是以房产公司为例，如果按照传统的"瀑布开发模式"(**Waterfall model**)，先挖10栋楼的地基、再盖骨架、然后架设屋顶，每个阶段都等到前一个阶段完成后开始，可能需要两年才能一次性交付10栋楼。也就是说，如果不考虑预售，该项目必须等到两年后才能回款。
>
> 敏捷开发是六个月后交付一号楼，后面每两个月交付一栋楼。因此，半年就能回款10%，后面每个月都会有现金流，资金压力就大大减轻了。

### 降低风险

**及时了解市场需求，降低产品不适用的风险。**

由于敏捷开发可以不断试错，找出对业务最重要的功能，然后通过迭代，调整软件方向。相比传统方式，大大增加了产品成功的可能性。如果市场需求不确定，或者你对该领域不熟悉，那么敏捷开发几乎是唯一可行的应对方式。

> 对于软件项目来说，先有一个原型产品，了解市场的接受程度，往往是项目成功的关键。有一本书叫做《梦断代码》，副标题就是"20+个程序员，三年时间，4732个bug，100+万美元，最后失败的故事"，这就是没有采用敏捷开发的结果。相反的，Instagram 最初是一个地理位置打卡 App，后来发现用户不怎么在乎地理位置，更喜欢上传照片，就改做照片上传软件，结果成了独角兽。

## 如何进行每一次迭代 (How to agile develop)

**每次迭代都是一个完整的软件开发周期，必须按照软件工程的方法论，进行正规的流程管理。**

具体来说，每次迭代都必须依次完成以下五个步骤。

1. 需求分析（requirements analysis）
2. 设计（design）
3. 编码（coding）
4. 测试（testing）
5. 部署和评估（deployment / evaluation）

每个迭代大约持续2~6周。

# Code Review

> [refer](https://mp.weixin.qq.com/s/c3RApB8a98tWahgC9mahJg)

- 代码变坏的原因

  - 重复的代码

  - 过早的优化

  - 之前有效的决策不再有效

    如: 第一版代码是没有太大的问题的, 当某一函数加入更多逻辑时, 会出现: 读者忘了前面讲的什么, 需要来回看

  - 不苛求合理性

    '两种写法都 ok，你随便挑一种吧'，'我这样也没什么吧'

    不一开始就进入最合理的状态，在后续协作中，其他同学很可能犯错！

  - 总是面向对象/总喜欢封装

  - 根本没有设计

- Model 设计

  首先去看前人的思考，再用上自己的通识能力，去进一步思考。

- 原则: 

  - Keep It Simple, Stupid

    ![img](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200617640.png)

    ![20200617n7erq9](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200617n7erq9.jpg)

  - 组合

    插件化. 各种不同的组合，它简单，却又满足了各种需求. 至少在后端开发中比OOP好.

  - 吝啬

    除非确无它法, 不要编写庞大的程序.

    应该最关注核心 struct 定义，构建起一个完备的模型，核心 interface，明确抽象 model 对外部的依赖，明确抽象 model 对外提供的能力。其他代码，就是要用最简单的代码实现模型内部细节。

  - 透明

    合理的函数上下级层次，同一层次的代码才会出现在同一个函数里;

    完备的文档需要出现在离代码最近的地方，让人'知道这里复杂的逻辑有文档'
    
  - 通俗

    接口设计避免标新立异
  
  - 缄默
  
    无效信息不要抛出
  
  - 补救
  
    出现异常时，马上退出并给出足够错误信息
  
- 针对Golang的细则(其他语言略有不同)

  - 代码格式规范，严格执行
  - 文件绝不能超过 800 行，超过，思考怎么拆文件
  - 函数对决不能超过 80 行，超过，思考怎么拆函数，思考函数分组，层次
  - 代码嵌套层次不能超过 4 层，超过了就得改。多想想能不能 early return。
  - 从目录、package、文件、struct、function 一层层下来 ，信息不能冗余。比如 file.FileProperty 这种定义。只有每个'定语'只出现在一个位置，才为'做好逻辑、定义分组/分层'提供了可能性。
  - 用多级目录来组织代码所承载的信息，即使某一些中间目录只有一个子目录。
  - 随着代码的扩展，老的代码违反了一些设计原则，应该立即原地局部重构，维持住代码质量不滑坡。比如:拆文件；拆函数；用 Session 来保存一个复杂的流程型函数的所有信息；重新调整目录结构。
  - 基于上一点考虑，应该尽量让项目的代码有一定的组织、层次关系。我个人的当前实践是除了特别通用的代码，都放在一个 git 里。特别通用、修改少的代码，逐渐独立出 git，作为子 git 连接到当前项目 git，让 goland 的 Refactor 特性、各种 Refactor 工具能帮助我们快速、安全局部重构。
  - 自己的项目代码，应该有一个内生的层级和逻辑关系。平铺展开不利于代码复用的。怎么复用、怎么组织复用，肯定会变成'人生难题'。T4-T7 的同学根本无力解决这种难题。
  - 如果被 review 的代码虽然简短，但是你看了一眼却发现不咋懂，那就一定有问题。自己看不出来，就找高级别的同学交流。这是你和被review 代码的同学成长的时刻。
  - 日志要少打。要打日志就要把关键索引信息带上。必要的日志必须打。
  - 有疑问就立即问，不要怕问错。让代码作者给出解释。不要怕问出低级问题。
  - 请积极使用 trpc。总是要和老板站在一起！只有和老板达成的对于代码质量建设的共识，才能在团队里更好地做好代码质量建设。



  


# Linux

## What's Linux

- Multi-user, multitasking operating system. 
- Free, Open-source, stable. 
- It can be used as the master control program in workstations and servers.
- Hundreds of commercial applications are available

## 参考

[脑图](http://naotu.baidu.com/file/60297df091db66fdfd9a653902f86272?token=c83591fd896d0c46)

[笔记](https://github.com/HelperInCa/Linux-note-follow-Hanshunping)

## Basic

- 目录结构

  > 一切皆文件

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-03-074702.jpg)

- 开机/重启前 应先执行`sync`, 把内存数据写入磁盘

- rwx权限详解

  ![image-20200509205615660](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-10-035616.png)

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-10-034527.png)

- Shell

## Unix vs. Linux

| **Basis of Difference** | **Linux**                                                    | **Unix**                                                     |
| :---------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Cost**                | Linux is freely distributed, downloaded through magazines, Books, website, etc. There are paid versions also available for Linux. | Different flavors of Unix have different pricing depending upon the type of vendor. |
| **Development**         | Linux is Open Source, and thousands of programmer collaborate online and contribute to its development. | Unix systems have different versions. These versions are primarily developed by AT&T as well as other commercial vendors. |
| **User**                | Everyone. From home users to developers and computer enthusiasts alike. | The UNIX can be used in internet servers, workstations, and PCs. |
| **Text made interface** | BASH is the Linux default shell. It offers support for multiple command interpreters. | Originally made to work in Bourne Shell. However, it is now compatible with many others software. |
| **GUI**                 | Linux provides two GUIs,viz., KDE and Gnome. Though there are many alternatives such as Mate, LXDE, Xfce, etc. | Common Desktop Environment and also has Gnome.               |
| **Viruses**             | Linux has had about 60-100 viruses listed to date which are currently not spreading. | There are between 80 to 120 viruses reported till date in Unix. |
| **Threat detection**    | Threat detection and solution is very fast because Linux is mainly community driven. So, if any Linux user posts any kind of threat, a team of qualified developers starts working to resolve this threat. | Unix users require longer wait time, to get the proper bug fixing patch. |
| **Architectures**       | Initially developed for Intel's x86 hardware processors. It is available for over twenty different types of CPU which also includes an ARM. | It is available on PA-RISC and Itanium machines.             |
| **Usage**               | Linux OS can be installed on various types of devices like mobile, tablet computers. | The UNIX operating system is used for internet servers, workstations & PCs. |
| **Best feature**        | Kernel update without reboot                                 | Feta ZFS - next generation filesystem DTrace - dynamic Kernel Tracing |
| **Versions**            | Different Versions of Linux are Redhat, Ubuntu, OpenSuse, Solaris, etc. | Different Versions of Unix are HP-UX, AIS, BSD, etc.         |
| **Supported file type** | The Filesystems supported by file type like xfs, nfs, cramfsm ext 1 to 4, ufs, devpts, NTFS. | The Filesystems supported by file types are zfs, hfx, GPS, xfs, vxfs. |
| **Portability**         | Linux is portable and is booted from a USB Stick             | Unix is not portable                                         |
| **Source Code**         | The source is available to the general public                | The source code is not available to anyone.                  |

## 相关

### inode

[Source](https://www.ruanyifeng.com/blog/2011/12/inode.html)

# Data Structure & Algorithm

> [总结](https://mp.weixin.qq.com/s/Z6zISNEZDRqRJn5YpNpl_A)

## 队列

- 实现: 数组, 链表

- FIFO

- 数组模拟环形队列

  - ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-04-27-055719.png)

  - 思路:

    - front: 指向队列的第一个元素

    - rear: 指向队列的最后一个元素的后一个位置. 空出一个空间

    - 队列满: 

      ```java
      (rear + 1) % maxSize == front
      ```

    - 队列有效容量:

      ```java
      (rear + maxSize - front) % maxSize
      ```



## 链表

- ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-04-28-184635.png)
  - 链式存储
  - 每个节点包含 data 域， next 域:指向下一个节点.
  - 链表的各个节点不一定是连续存储.
  - 链表分带头节点的和没有头节点的
- 双向链表
- 环形单向链表(Josephus problem)

## 栈

- FILO

- 实现: 数组, 链表

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-03-014414.png)

  - 思路:
    1. 定义top表示栈顶,初始化-1;
    2. 入栈: top++; stack[top] = data;
    3. 出栈: int value = stack[top]; top--, return value;

- 前缀, 中缀, 后缀表达式(逆波兰)

  - 后缀: 

    例如: (3+4)×5-6 对应的后缀表达式就是 3 4 + 5 × 6 - , 针对后缀表达式求值步骤如下:

    1. 从左至右扫描，将 3 和 4 压入堆栈;
    2. 遇到+运算符，因此弹出 4 和 3(4 为栈顶元素，3 为次顶元素)，计算出 3+4 的值，得 7，再将 7 入栈; 
    3. 将 5 入栈;
    4. 接下来是×运算符，因此弹出 5 和 7，计算出 7×5=35，将 35 入栈;
    5. 将 6 入栈;
    6. 最后是-运算符，计算出 35-6 的值，即 29，由此得出最终结果

  - 中缀转后缀:

  1. 初始化两个栈:运算符栈 s1 和储存中间结果的栈 s2; 
  2. 从左至右扫描中缀表达式;
    3. 遇到操作数时，将其压 s2;
  4. 遇到运算符时，比较其与 s1 栈顶运算符的优先级:
    
     1. 如果 s1 为空，或栈顶运算符为左括号“(”，则直接将此运算符入栈; 
     
     2. 否则，若优先级比栈顶运算符的高，也将运算符压入 s1;
     
     3. 否则，将 s1 栈顶的运算符弹出并压入到 s2 中，再次转到(4-1)与 s1中新的栈顶运算符相比较;
    5. 遇到括号时:
          1. 如果是左括号“(”，则直接压入 s1
        2.  如果是右括号“)”，则依次弹出 s1 栈顶的运算符，并压入 s2，直到遇到左括号为止，此时将这一对括号丢弃 

    6. 重复步骤 2 至 5，直到表达式的最右边
    7. 将 s1 中剩余的运算符依次弹出并压入 s2
    8. 依次弹出 s2 中的元素并输出，结果的逆序即为中缀表达式对应的后缀表达式
## 递归  
- 规则: 
  1. 执行一个方法时，就创建一个新的受保护的栈空间
  2. 方法的局部变量是独立的，不会相互影响. 如果方法中使用的是引用类型变量(比如数组)，就会共享该引用类型的数据.
  3. 递归必须向**退出递归的条件**逼近，否则就是无限递归,出现StackOverflowError
  4. 当一个方法执行完毕，或者遇到return，就将**结果返回给调用者**，同时当方法执行完毕或返回时, 该方法也就执行完毕

## 排序

- 冒泡

  - 优化: 在某趟排序中没有发生一次交换, 可以提前结束排序.

- 选择

  第一次从待排序的数据元素中选出最小（或最大）的一个元素，存放在序列的起始位置，然后再从剩余的未排序元素中寻找到最小（大）元素，然后放到已排序的序列的末尾。以此类推，直到全部待排序的数据元素的个数为零。

- 插入

  把 n 个待排序的元素看成为一个有序表和一个无序表，开始时有序表中只包含一个元素，无序表中包含有 n-1 个元素，排序过程中每次从无序表中取出第一个元素，把它的排序码依次与有序表元素的排序码进行比较，将它插入到有序表中的适当位置，使之成为新的有序表。

- 希尔(缩小增量)
  - 直接插入排序问题: 当需要插入的数是较小的数时，后移的次数明显增多
  -  把记录按下标的一定增量分组，对每组使用直接插入排序算法排序;随着增量逐渐减少，每组包含的数越来越多，当增量减至 1 时，整个队列恰被分成一组，算法便终止

- 快排
  - 分治
  - 通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以**递归**进行，以此达到整个数据变成有序序列

## 树

优点: 查询, 修改效率高

- 前,中,后序

  根据当前节点的遍历位置判断

- 遍历 查找 删除

- 线索化二叉树

  - 添加了直接指向节点的前驱和后继的指针
  - 线性遍历: 无需递归, 提高效率
  
- 哈夫曼树
  
- 二叉排序树 BST

- 平衡二叉树 (AVL tree) 

  左旋转 右旋转 双旋转

  ![20200701Zf9nSD](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200701Zf9nSD.png)

- 多叉排序树

  在二叉树中，每个节点有数据项，最多有两个子节点。如果允许每个节点可以有更多的数据项和更多的子节点， 就是多叉树(multiway tree).

  多叉树通过重新组织节点，减少树的高度, 减少构建时间

  - B 树

    ![20200701RV8GDt](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200701RV8GDt.png)

    1. 如图B树通过重新组织节点，降低了树的高度.
    2. 文件系统及数据库系统的设计者利用了磁盘预读原理，将一个节点的大小设为等于一个页(页得大小通常为4k)，这样每个节点只需要一次 I/O 就可以完全载入
    3. 将树的度M设置为1024，在600亿个元素中最多只需要4次I/O操作就可以读取到想要的元素,B树(B+)广泛应用于文件存储系统以及数据库系统中

    - B树, B+树, B*树

      B 即 Balanced，平衡的意思。

      - B树

        ![20200701ImKmRE](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200701ImKmRE.png)

        1. B 树的阶:节点的最多子节点个数。比如 2-3 树的阶是 3，2-3-4 树的阶是 4
        2. B树的搜索，从根结点开始，对结点内的关键字(有序)序列进行二分查找，如果命中则结束，否则进入查询关键字所属范围的子结点;重复，直到所对应的儿子指针为空，或已经是叶子结点
        3. 关键字集合分布在整颗树中, 即叶子节点和非叶子节点都存放数据.
        4. 搜索有可能在非叶子结点结束
        5. 其搜索性能等价于在关键字全集内做一次二分查找

      - B+树

        B+树是 B 树的变体

        ![20200701115501](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200701115501.png)

        1. B+树的搜索与 B 树基本相同，区别是 B+树只有达到叶子结点才命中(B 树可以在非叶子结点命中)，其性能也等价于在关键字全集做一次二分查找

        2. 所有关键字都出现在叶子结点的链表中(即数据只能在叶子节点【也叫稠密索引】)，且链表中的关键字(数据)是有序的。

        3. 非叶子结点相当于是叶子结点的索引(稀疏索引)，叶子结点相当于是存储(关键字)数据的数据层

        4. 更适合文件索引系统

           B 树和 B+树各有自己的应用场景，不能说 B+树完全比 B 树好

      - B*树

        B*树是 B+树的变体，在 B+树的非根和非叶子结点再增加指向兄弟的指针。

        ![20200701120117](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200701120117.png)

        B\*树定义了非叶子结点关键字个数至少为(2/3)*M，即块的最低使用率为 2/3，而 B+树的块的最低使用率为的1/2。B\*树空间使用率更高

    - 2-3 树(最简单的B树)

      1. 2-3 树的所有叶子节点都在同一层.(只要是 B 树都满足这个条件)
      2. 有两个子节点的节点叫二节点，二节点要么没有子节点，要么有两个子节点.
      3. 有三个子节点的节点叫三节点，三节点要么没有子节点，要么有三个子节点.  
      4. 2-3 树是由二节点和三节点构成的树。

      - 插入规则:

        当按照规则插入一个数到某个节点时，不满足要求时，就需要拆，先向上拆，如果上层满，则拆本层，拆后仍然需要满足上面条件。

        ![202007017so4fk](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/202007017so4fk.png)

## 图

表示**多对多**关系

- 表示方法

  - 邻接矩阵(二维数组)

    ![image-20200804225037260](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804225037.png)

  - 邻接表(数组+链表)

    ![image-20200804225130304](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804225130.png)

    - 邻接矩阵需要为每个顶点都分配n个边的空间，有很多边都是不存在,会造成空间的一定损失. 

    - 邻接表的实现只关心存在的边，不关心不存在的边。因此没有空间浪费，邻接表由数组+链表组成

- 深度优先 dfs/广度优先 bfs

## 常用算法

### 二分查找(非递归)

- 升序数组 O(log n)

### 分治

分治法在每一层递归上都有三个步骤:

1. 分解:将原问题分解为若干个规模较小，相互独立，与原问题形式相同的子问题 
2. 解决:若子问题规模较小而容易被解决则直接解，否则递归地解各个子问题
3. 合并:将各个子问题的解合并为原问题的解

- 应用: 汉诺塔

### 动态规划

- 动态规划(DynamicProgramming)算法的核心思想是:将**大问题划分为小问题**进行解决，一步步获取最优解的处理算法
- 与分治法不同的是，适合于用动态规划求解的问题，经分解得到子问题往往**不是互相独立**的。 ( 即下一个子阶段的求解是建立在上一个子阶段的解的基础上，进行进一步的求解 )

### KMP

- KMP 是一个解决模式串在文本串是否出现过，如果出现过，最早出现的位置的经典算法.

- 利用之前判断过信息，通过一个 next 数组，保存模式串中前后最长公共子序列的长度，每次回溯时，通过 next 数组找到，前面匹配过的位置，省去了大量的计算时间

- 算法

    - [图解](https://www.cnblogs.com/ZuoAndFutureGirl/p/9028287.html) 

    - 移动位数 = 已匹配字符数 - 对应的部分匹配值

        部分匹配值: 字符串前缀和后缀的最大共有长度

### 贪心

- 贪婪算法(贪心)是指在对问题进行求解时，在**每一步**选择中都采取最优的选择，从而希望能够导致结果是最优的算法
- 贪婪算法所得到的结果不一定是最优的结果(有时候会是最优解)，但是都是**相对近似**最优解的结果

### 普里姆

解决最小生成树问题.

最小生成树 *minimum spanning tree (MST)*: 一副连通加权无向图中一棵权值最小的生成树. 

在包含n个顶点的连通图中, 找出只有n-1条边包含所有n个顶点的连通子图. 也就是极小连通子图.

