<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Software Architecture](#software-architecture)
- [Design pattern](#design-pattern)
- [Computer network](#computer-network)
  - [RESTful:](#restful)
  - [HTTP](#http)
      - [三次握手](#%E4%B8%89%E6%AC%A1%E6%8F%A1%E6%89%8B)
      - [四次分手](#%E5%9B%9B%E6%AC%A1%E5%88%86%E6%89%8B)
- [容错/高可用/灾备](#%E5%AE%B9%E9%94%99%E9%AB%98%E5%8F%AF%E7%94%A8%E7%81%BE%E5%A4%87)
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



# Computer network

> [参考](https://juejin.im/post/5ad7e6c35188252ebd06acfa#heading-24)

## RESTful:

- (Resource): 信息实体,uri
- Representation: 形式 eg: 文本可以用txt, HTML, XML
- State Transfer: 表现层转化

## HTTP

![image-20181106021059323](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051327.png)

#### 三次握手

![image-20190803095209464](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051332.jpg)

1. 第一次握手：建立连接。客户端发送连接请求报文段，将SYN位置为1，Sequence Number为x；然后，客户端进入SYN_SEND状态，等待服务器的确认；
2. 第二次握手：服务器收到SYN报文段。服务器收到客户端的SYN报文段，需要对这个SYN报文段进行确认，设置Acknowledgment Number为x+1(Sequence Number+1)；同时，自己自己还要发送SYN请求信息，将SYN位置为1，Sequence Number为y；服务器端将上述所有信息放到一个报文段（即SYN+ACK报文段）中，一并发送给客户端，此时服务器进入SYN_RECV状态；
3. 第三次握手：客户端收到服务器的SYN+ACK报文段。然后将Acknowledgment Number设置为y+1，向服务器发送ACK报文段，这个报文段发送完毕以后，客户端和服务器端都进入ESTABLISHED状态，完成TCP三次握手。
   完成了三次握手，客户端和服务器端就可以开始传送数据。以上就是TCP三次握手的总体介绍。

#### 四次分手

当客户端和服务器通过三次握手建立了TCP连接以后，当数据传送完毕，要断开TCP连接的啊。那对于TCP的断开连接，就有“四次分手”。

1. 第一次分手：主机1（可以使客户端，也可以是服务器端），设置Sequence Number和Acknowledgment Number，向主机2发送一个FIN报文段；此时，主机1进入FIN_WAIT_1状态；这表示主机1没有数据要发送给主机2了；
2. 第二次分手：主机2收到了主机1发送的FIN报文段，向主机1回一个ACK报文段，Acknowledgment Number为Sequence Number加1；主机1进入FIN_WAIT_2状态；主机2告诉主机1，我“同意”你的关闭请求；
3. 第三次分手：主机2向主机1发送FIN报文段，请求关闭连接，同时主机2进入LAST_ACK状态；
4. 第四次分手：主机1收到主机2发送的FIN报文段，向主机2发送ACK报文段，然后主机1进入TIME_WAIT状态；主机2收到主机1的ACK报文段以后，就关闭连接；此时，主机1等待2MSL后依然没有收到回复，则证明Server端已正常关闭，那好，主机1也可以关闭连接了。



# 容错/高可用/灾备

- 容错：发生故障时，如何让系统继续运行。

- 高可用：系统中断时，如何尽快恢复。

- 灾备：系统毁灭时，如何抢救数据。

  

>  Resourses
>
> - [容错，高可用和灾备](http://www.ruanyifeng.com/blog/2019/11/fault-tolerance.html)



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

