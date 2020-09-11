<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Basics](#basics)
  - [Java](#java)
  - [Python3](#python3)
    - [(TBD)](#tbd)
  - [Golang](#golang)
  - [Database](#database)
- [Hotkeys](#hotkeys)
- [Git](#git)
  - [git init](#git-init)
  - [git status](#git-status)
  - [git add](#git-add)
  - [git commit](#git-commit)
    - [commit message & change log](#commit-message--change-log)
  - [git log](#git-log)
  - [git push](#git-push)
  - [git pull](#git-pull)
  - [git remote](#git-remote)
  - [git rm](#git-rm)
  - [gitignore](#gitignore)
  - [alias](#alias)
- [Maven](#maven)
- [Tools](#tools)
  - [Gist](#gist)
  - [Zsh](#zsh)
- [Docker](#docker)
  - [脑图](#%E8%84%91%E5%9B%BE)
- [Bash](#bash)
- [My Alias](#my-alias)
- [Spring Boot](#spring-boot)
- [Jira](#jira)
- [Spring 5](#spring-5)
  - [IoC(Inversion of Control)](#iocinversion-of-control)
  - [Bean管理](#bean%E7%AE%A1%E7%90%86)
  - [AOP(Aspect Oriented Programming)](#aopaspect-oriented-programming)
  - [JdbcTemplate](#jdbctemplate)
  - [事务](#%E4%BA%8B%E5%8A%A1)
  - [日志框架](#%E6%97%A5%E5%BF%97%E6%A1%86%E6%9E%B6)
  - [Spring5 核心容器支持`@Nullable`, 函数式风格](#spring5-%E6%A0%B8%E5%BF%83%E5%AE%B9%E5%99%A8%E6%94%AF%E6%8C%81nullable-%E5%87%BD%E6%95%B0%E5%BC%8F%E9%A3%8E%E6%A0%BC)
  - [Spring5 支持整合 JUnit5](#spring5-%E6%94%AF%E6%8C%81%E6%95%B4%E5%90%88-junit5)
  - [Webflux](#webflux)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Basics

## Java

[notes](https://github.com/HelperInCa/notes/blob/master/modules/Java.md)

## Python3

### (TBD)

- new way to format string

```python
>>> name = "Eric"
>>> age = 74
>>> f"Hello, {name}. You are {age}."
'Hello, Eric. You are 74.'
```

## Golang

[notes](https://github.com/HelperInCa/notes/blob/master/modules/Golang.md)

## Database

[notes](https://github.com/HelperInCa/notes/blob/master/modules/Database.md)

# Hotkeys

[Collections](https://github.com/HelperInCa/notes/blob/master/modules/hotkey.md)

# Git

> Sources:
>
> - [GItHub help](https://help.github.com/en/github)
> - [脑图](http://naotu.baidu.com/file/8f3e66d234023d218379fc8ef7790fe0?token=652534011488cbfa) 

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-git%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE.png)

## git init

## git status

## git add

## git commit

> git commit -am "<message>"

### commit message & change log

> [转](https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

- 格式: 三个部分：Header，Body 和 Footer

  ```bash
  <type>(<scope>): <subject>
  // 空一行
  <body>
  // 空一行
  <footer>
  ```

  - Header(必需)

    - `type`: 说明 commit 的类别

      - feat：新功能（feature）
      - fix：修补bug
      - docs：文档（documentation）
      - style： 格式（不影响代码运行的变动）
      - refactor：重构（即不是新增功能，也不是修改bug的代码变动）
      - test：增加测试
      - chore：构建过程或辅助工具的变动

      > 如果`type`为`feat`和`fix`，则该 commit 将肯定出现在 Change log 之中。

    - `scope`: 说明 commit 影响的范围，比如数据层、控制层、视图层等等

    - `subject`: commit 目的的简短描述，不超过50个字符

      - 以动词开头，使用第一人称现在时，比如`change`，而不是`changed`或`changes`
      - 第一个字母小写
      - 结尾不加句号（`.`）

  - Body(可省略): 对本次 commit 的详细描述，可以分成多行

  - Footer(可省略): Footer 部分只用于两种情况

    - 不兼容变动

      Footer 部分以`BREAKING CHANGE`开头，后面是对变动的描述、以及变动理由和迁移方法。

    - 关闭issue

      ```bash
      Closes #234
      ```

      ```bash
      Closes #123, #245, #992
      ```

  - Revert

    如果当前 commit 用于撤销以前的 commit，则必须以`revert:`开头，后面跟着被撤销 Commit 的 Header

    ```bash
    revert: feat(pencil): add 'graphiteWidth' option
    
    This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
    ```

    Body部分的格式是固定的，必须写成`This reverts commit <hash>.`

- Commit message template

  ```bash
  # 当前项目目录下
  $ git config commit.template [filepath]
  # 全局
  $ git config --global commit.template [filepath]
  ```

  一份建议的模版

  ```bash
  # <类型>(<scope>): <主题> (最多50个字)
  
  # 解释为什么要做这些改动
  # |<----  请限制每行最多72个字   ---->|
  
  # 提供相关文章和其它资源的链接和关键字
  # 例如: Github issue #23
  
  # --- 提交 结束 ---
  # 类型值包含
  #    feat (新特性)
  #    fix (bug修复)
  #    docs (文档改动)
  #    style (格式化, 缺失分号等; 不包括生产代码变动)
  #    refactor (重构代码)
  #    test (添加缺失的测试, 重构测试, 不包括生产代码变动)
  #    chore (更新grunt任务等; 不包括生产代码变动)
  # --------------------
  # 注意
  #    主题和内容以一个空行分隔
  #    主题限制为最大50个字
  #    主题行结束不用标点
  #    主题行使用祈使名
  #    内容每行72个字
  #    内容用于解释为什么和是什么,而不是怎么做
  #    内容多行时以'-'分隔
  ```

  

- **Commitizen**

  撰写合格 Commit message 的工具

  - 安装..

    ```bash
    $ npm install -g commitizen
    ```

  - 在项目目录里，运行下面的命令，使其支持 Angular 的 Commit message 格式

    ```bash
    $ commitizen init cz-conventional-changelog --save --save-exact
    ```

  - 以后，凡是用到`git commit`命令，一律改为使用`git cz`。这时，就会出现选项，用来生成符合格式的 Commit message

    ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-051322.png)

## git log

## git push

## git pull

- refusing to merge unrelated histories

  git pull origin master --allow-unrelated-histories

## git remote

- add

  `git remote add [remote name] [remote URL]`

- rename

Use the `git remote rename` command to rename an existing remote.

```shell
$ git remote -v
# View existing remotes
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)

$ git remote rename origin destination
# Change remote name from 'origin' to 'destination'
```

- remove

Use the `git remote rm` command to remove a remote URL from your repository.

## git rm

- remove commited files/folders from repo

  ```shell
  $ git rm -r --cached FOLDER/
  $ git commit -m'delete FOLDER'
  $ git push orgin master
  ```

  update `.gitignore`

## gitignore

- 全局

  `~/.gitignore_global`

## alias

如: `st`表示`status`

```bash
$ git config --global alias.st status
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
```



# Maven

- 服务于 Java 平台的自动化构建工具

  - 构建: 三层

    1. 编译 

    2. 部署 一个 BS项目最终运行的并不是动态 Web 工程本身, 而是它编译后的结果

       ![image-20200804111750030](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804111750.png)

    3. 搭建

  - 构建中的各个环节

    1. 清理: 删除以前编译得到的字节码文件
    2. 编译
    3. 测试: 自动调用 Junit
    4. 报告
    5. 打包: 动态 web 工程打 war 包, Java 工程打 jar 包
    6. 安装: 将打包得到的文件复制到仓库
    7. 部署: 将 war 包复制到 servlet 容器指定目录

- 目录结构

  Hello
  		|---src
  		|---|---main
  		|---|---|---java
  		|---|---|---resources
  		|---|---test
  		|---|---|---java
  		|---|---|---resources
  		|---pom.xml

  为什么要约定目录结构?

  - mvn 负责自动化构建. 以编译为例, mvn 要知道 Java 源文件的位置才能自动化编译

  - 有两种方法自定义

    - 配置

      ```xml
      <param-value>classpath:spring-context.xml</param-value>
      ```

    - 遵守框架的约定

      `log4j.properties` `log4j.xml`

- Maven 命令

  ![image-20200804142937006](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804142939.png)

- POM

  - Project Object Model 
  - pom.xml 是 mvn 工程核心配置文件

- 坐标

  使用如下三个向量在 Maven 的仓库中确定唯一的 Maven 工程。 

  1. groupId: 公司或组织的域名倒序+当前项目名称 
  2. artifactId: 当前项目的模块名称
  3. version: 当前模块的版本

- 仓库

  本地 远程 中央

- 依赖

  - `mvn install`

  - 范围

    ![image-20200804151332828](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804151333.png)

    - compile

      ![image-20200804151402453](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804151402.png)

    - test

      ![image-20200804151419827](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804151420.png)

    - provided

      ![image-20200804151458645](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804151458.png)

      ![image-20200804152915550](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804152915.png)

  - 传递

    - 优点: 不必在每个 module 中重复声明, 在最下面的工程中依赖一次
    - 注意: 非 compile 范围的依赖不能传递

  - 排除

    比如不稳定的 jar 包, 不希望引入当前工程

  - 原则

    - 解决 module 之间 jar 包冲突

    - 验证路径最短优先

      验证路径相同时先声明(dependency 标签顺序)优先

  - 统一管理版本

    1. 使用 Properties 标签内使用自定义标签统一声明版本号

       ```xml
       <properties><hu.spring.version>4.0.0.RELEASE</hu.spring.version></properties>
       ```

       

    2. 在需要统一版本的位置, 使用`${自定义标签名}`引用声明的版本号

       ```XML
       <version>${hu.spring.version}</version>
       ```

    > 需要统一声明再引用的地方都可以使用properties 标签配合自定义标签的方法

  - 继承

    由于 test 范围依赖不能传递, 如何统一管理版本(如 Junit)?

    将 Junit 依赖统一提取到父工程, 子工程中声明 junit 依赖时不指定版本.

    1. 创建一个 mvn 工程作为父工程, 打包方式为 pom

    2. 子工程中声明对父工程的引用, 删除子工程坐标中与父工程重复的内容

       ![image-20200804171644261](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804171645.png)

    3. 在父工程中统一管理依赖版本

       ![image-20200804172053145](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804172053.png)

    4. 删除子工程中依赖版本号部分

    5. 配置继承后, 要先安装父工程再执行安装命令

  - 聚合
    - 情景: 一键安装各个模块
    
    1. 在聚合工程中配置各模块
    
       ![image-20200804172715798](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200804172716.png)
    
    2. 在聚合工程的 pom.xml上右键run as maven install
    
    

- 生命周期

  不论现在要执行哪一个阶段, 都是从**最初**阶段开始.

# Tools

## Gist

- create a private Gist and paste the Markdown
- `command` + `c` the file on Gist and `command` + `v` on Medium

> cons:
>
> - not support HTML well

## Zsh

- Usages

  - 补全

    按下`tab`显示所有选项, 再按一次`tab`, 即进入选择模式, 之后按`tab`切下一个, 按`shift`+`tab`切上一个, `ctrl`+`f/b/n/p`前后左右切换

  - 目录名简写

    比如我们要进入到 `~/workspace/src/dict`，我们只需要输入每个目录的首字母就行，然后再`TAB`键补全

  - kill

    ```shell
    kill emacs
    # 按下 tab, 变成
    kill 59683
    ```

  - alias

    不仅支持普通alias, 还支持针对文件类型的, 如:

    ```shell
    alias -s tgz='tar -xzvf'
    alias -s rb=vi
    ```

    输入xxx.gz, 将按照tar -xzvf解压. 输入xxx.rb, 将自动用vi打开. 

  - jump

    输入d, 列出访问过的所有目录, 再按提示的数字即可进入相应目录

    ```shell
    ~
    > d
    0				~
    1				~/Applications
    
    > 1
    ~/Applications
    ```

  - 重复上一条命令

    ```shell
    r
    ```

    

- Plugins
  - [z](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/z)
    Assume that you have previously visited directory `~/.oh-my-zsh/plugins`

    ```shell
    /usr/bin$ z plug  # Even 'z p' might suffice
    ~/.oh-my-zsh/plugins$
    ```

  - [autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

  - [vscode](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/vscode)
    `vs`

  - [syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)



# Docker

## 脑图

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-09-071113.png)

> [脑图网盘](https://pan.baidu.com/s/1DF_ms43e5Qvvrfr2mdcfAg) 提取码: 9e7f
>
> [中文文档](https://yeasy.gitbook.io/docker_practice/)

- Docker 容器后台运行时, 必须要有一个前台进程, 否则会自动停止

# Bash

- [参考](https://wangdoc.com/bash/index.html)

# My Alias

- ~/.zshrc

  - `jpnb` = `jupyter notebook`

  - `pip` = `pip3`

  - `proxy `  terminal走sock5

    `unproxy`  关闭 

    > 查看当前ip: `$curl cip.cc` or `$curl ip.cn`

  - `rm`实现 "回收站"功能
  
  - `gz`=`tar -xzvf`
    `tgz`=`tar -xzvf`
  `zip`=`unzip`
    `bz2`=`tar -xjvf`

  - `toc` MD生成目录
  
    > 文件名不能有空格!
    
  - `ch`清空zsh历史记录

# Spring Boot

[Spring Boot](https://github.com/HelperInCa/notes/blob/master/modules/SpringBoot.md)

# Jira

# Spring 5

![Spring5模块](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200907155338.bmp)

- Pros:

  - Lightweight
  - opensource
## IoC(Inversion of Control) 

控制反转

  - non invasive: no need to implement any interface or inherit any class from Spring to your classes, so whenever you want to change from Spring to your classes, then you do not need to change your class

  - end to end development: Spring supports all aspects of developments

  - Dependency Injection (DI) 

    tight couple -> loose couple 

  

- IoC container

  The container gets its instructions on what objects to instantiate, configure, and assemble by reading configuration metadata. The configuration metadata is represented in XML, Java annotations, or Java code.

  - DI -> reflection: 允许程序在运行的时候动态的生成对象、执行对象的方法、改变对象的属性，spring就是通过反射来实现注入的。

  ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-054653.jpg)

  - IoC 容器底层是对象工厂

    Spring提供2种实现方式:

    ![20200727094444](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200727094444.png)

## Bean管理

  - Singleton: default

  - Prototype

  - 什么是Bean管理

    - Spring 创建对象
    - Spring 注入属性

   - Bean管理的两种方式

     - 配置文件(XML)

       - 创建对象

         ![20200727110444](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200727110444.png)

       - DI(Dependency Injection) 依赖注入, 就是注入属性

         > DI vs. IoC: DI 是 IoC 的具体实现方式

         - setter

           ![20200727112243](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200727112243.png)

         - 有参构造器

           ![image-20200727112348507](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200727112348.png)

         - p名称空间注入(简化setter)

         - 注入其他类型属性

           - null

             ```xml
             <property name="address">
             	<null/>
             </property>
             ```

           - 属性值包含特殊符号

             ```xml
             <!--例如<南京>
             	1. 转义 &lt; &gt;
             	2. 写入CDATA
             -->
             <property name="address">
             	<value><![CDATA[<南京>]]></value>
             </property>
             ```

         - 注入外部Bean

           <img src="https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200727165511.png" alt="20200727165511" style="zoom:150%;" />
           
         - 注入内部bean

           ![image-20200728161010240](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728161010.png)

           ![image-20200728161353468](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728161353.png)

         - 级联赋值

           1. ![image-20200728164008182](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728164008.png)

           2. ![image-20200728164307470](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728164307.png)

              ```xml
              <bean id="emp" class="com.atguigu.spring5.bean.Emp">
              	<!--设置两个普通属性-->
                  <property name="ename" value="lucy"></property>
                  <property name="gender" value="女"></property>
              	<!--级联赋值-->
                  <property name="dept" ref="dept"></property>
              	<property name="dept.dname" value="技术部"></property>
              </bean>
              <bean id="dept" class="com.atguigu.spring5.bean.Dept">
                  <property name="dname" value="财务部"></property>
              </bean>
              ```

         - 注入集合属性

           属性: array, List, Map, Set

           1. 创建类，定义数组、list、map、set 类型属性，生成对应 set 方法

           2. 配置文件

              ```xml
              <bean id="stu" class="com.atguigu.spring5.collectiontype.Stu">
              	<!--array属性注入-->
                  <property name="courses">
                  	<array>
                      	<value>Java</value>
                          <value>MySQL</value>
                      </array>
                  </property>
                  <!--list 类型属性注入-->
                  <property name="list">
                  	<list>
                      	<value>Jack</value>
                          <value>Rose</value>
                      </list>
                  </property>
                  <!--map 类型属性注入-->
                  <property name="maps">
                  	<map>
                      	<entry key="JAVA" value="java"></entry>
                          <entry key="PHP" value="php"></entry>
                      </map>
                  </property>
                  <!--set 类型属性注入-->
                  <property name="sets">
                  	<set>
                      	<value>Redis</value>
                          <value>Google</value>
                      </set>
                  </property>
              </bean>
              ```

           3. 集合里面设置对象类型值

              ![20200728200521](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728200521.png)

           4. 把集合注入部分提取出来

              1. XML中引入命名空间 util

                 ![image-20200728201753847](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200728201754.png)

              2. 使用 util 标签完成集合类型属性注入

                 ```xml
                 <!--1 提取 list 集合类型属性注入-->
                 <util:list id="bookList">
                 	<value>书1</value>
                     <value>书2</value>
                     <value>书3</value>
                 </util:list>
                 <!--2 提取 list 集合类型属性注入使用-->
                 <bean id="book" class="com.atguigu.spring5.collectiontype.Book">
                 	<property name="list" ref="bookList"></property>
                 </bean>
                 ```

         - Factory Bean

           1. 普通Bean: 配置文件中定义Bean类型就是返回类型

           2. Factory Bean: 配置文件中定义Bean类型可以和返回类型不一样

              1. 创建类, 让类作为Factory Bean, 实现接口FactoryBean

              2. 在要实现的方法中定义返回的Bean类型

              ![image-20200729100300413](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729100300.png)

         - Bean作用域

           - Spring中 可以设置bean实例为单实例还是多实例, *默认单实例*

           - 如何设置单实例/多实例

             1. 配置文件bean标签里属性 scope 用于设置单例还是多例
             2. scope: 
                - singleton 默认
                - prototype

             3. singleton 和 prototype 区别
                 第一 singleton单实例，prototype多实例
                 第二 设置 scope 值是 singleton 时候，加载 spring 配置文件时候就会创建单实例对象;

                设置 scope 值是 prototype 时候，不是在加载 spring 配置文件时候创建 对象，在调用 getBean 方法时候创建多实例对象

             ![image-20200729103410317](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729103410.png)

         - Bean生命周期(7步)

           1. 通过构造器创建 bean 实例(无参数构造)
           2. 为 bean 的属性设置值和对其他 bean 引用(调用 set 方法)
           3. 把 bean 实例传递 bean 后置处理器的方法 postProcessBeforeInitialization
           4. 调用 bean 的初始化的方法(需要进行配置初始化的方法)
           5. 把 bean 实例传递 bean 后置处理器的方法 postProcessAfterInitialization 
           6. bean 可以使用了(对象获取到了)
           7. 当容器关闭时候，调用 bean 的销毁的方法(需要进行配置销毁的方法)

           ```java
           public class Orders {
               // 无参构造
               public Orders {
                   System.out.println("第一步 执行无参数构造创建 bean 实例");
               }
               private String oname;
           	public void setOname(String oname) {
           		this.oname = oname;
           		System.out.println("第二步 调用 set 方法设置属性值"); 
               }
               // 创建执行的初始化的方法
           	public void initMethod() {
                   System.out.println("第三步 执行初始化的方法");
               }
               //创建执行的销毁的方法
           	public void destroyMethod() { 
                   System.out.println("第五步 执行销毁的方法");
           	}
           }
           ```

           

           ![image-20200729113951271](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729113951.png)

           ![image-20200729113904874](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729113905.png)

         - XML自动装配(常用注解方式实现此功能)

           根据指定装配规则(属性名称或者属性类型)，Spring 自动将匹配的属性值进行注入

           - 根据属性名称自动注入

             ```xml
             <bean id="emp" class="com.atguigu.spring5.autowire.Emp" autowire="byName">
             	<!--<property name="dept" ref="dept"></property>-->
             </bean>
             <bean id="dept" class="com.atguigu.spring5.autowire.Dept"></bean>
             ```

           - 根据属性类型自动注入

             ```xml
             <bean id="emp" class="com.atguigu.spring5.autowire.Emp" autowire="byType"> 
                 <!--<property name="dept" ref="dept"></property>-->
             </bean>
             <bean id="dept" class="com.atguigu.spring5.autowire.Dept"></bean>
             ```

         - XML外部属性文件

           > 直接配置数据库
           >
           > ![image-20200729152954625](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729152954.png)

           1. 创建外部属性文件，properties 格式文件，写数据库信息

              ![image-20200729153122868](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729153123.png)

           2. 把外部 properties 属性文件引入到 spring 配置文件中

              引入 context 命名空间

              ![image-20200729153704267](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729153704.png)

     - Annotation

       - 注解是什么

         1. 注解是代码特殊标记，格式:@注解名称(属性名称=属性值, 属性名称=属性值..) 
         2. 注解在类/方法/属性上面
         3. 目的:简化 xml 配置

       - 四个注解

         1. `@Component`

         2. `@Service`

         3. `@Controller`

         4. `@Repository`

          四个注解功能是一样的，都可以用来创建 bean 实例
         
       - 注解 创建对象

         1. 引入依赖

            `spring-aop-5.2.8.RELEASE.jar`

         2. 开启组件扫描

            ```xml
            <!--
            a. 如果扫描多个包，多个包使用逗号隔开 b. 扫描包上层目录
            -->
            <context:component-scan base-package="com.atguigu"></context:component-scan>
            ```

         3. 创建类，在类上面添加创建对象注解

            ```java
            //在注解里面 value 属性值可以省略不写， 
            //默认值是类名称，首字母小写 
            //UserService -- userService
            @Component(value = "userService") //<bean id="userService" class=".."/> 
            public class UserService {
            	public void add() { 
                	System.out.println("service add.......");
            	} 
            }
            ```

         - 开启组件扫描配置细节

           ![image-20200729171043241](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200729171043.png)

       - 注解 注入属性

         1. `@AutoWired` 根据属性类型进行自动装配

            - 把 service 和 dao 对象创建，在 service 和 dao 类添加创建对象注解

            - 在 service 注入 dao 对象，在 service 类添加 dao 类型属性，在属性上面使用注解

            ```java
            @Service
            public class UserService { 
                //添加注入属性注解
                //定义 dao 类型属性 
                //不需要添加 set 方法     
            	@Autowired
                private UserDao userDao;
            	
                public void add() { 
                    System.out.println("service add.......");
                    userDao.add();
            	} 
            }
            ```

         2. `@Qualifier` 根据名称进行注入

            *要和`@AutoWired`组合使用*

            ```java
            @Autowired //根据类型进行注入
            @Qualifier(value = "userDaoImpl1") //根据名称进行注入 
            private UserDao userDao;
            ```

            

         3. `@Resource` 可以根据类型或名称注入

            ```java
            //@Resource //根据类型进行注入
            @Resource(name = "userDaoImpl1") //根据名称进行注入 
            private UserDao userDao;
            ```

            > `@Resource` 是`javax.annotation.Resource`, 不是Spring中的, 推荐使用`@AutoWired` `@Qualifier`

         4. `@Value` 普通类型注入

            ```java
            @Value(value = "abc") 
            private String name;
            ```

       - 完全注解开发

         1. 创建配置类，替代 xml 配置文件

         ```java
         @Configuration //作为配置类，替代xml配置文件 @ComponentScan(basePackages = {"com.atguigu"}) 
         public class SpringConfig {
         }
         ```

         2. 编写测试类

         ```java
         @Test
         public void testService2() { 
             //加载配置类
         	ApplicationContext context
         = new AnnotationConfigApplicationContext(SpringConfig.class);
         	UserService userService = context.getBean("userService", UserService.class);
         	System.out.println(userService);
         	userService.add();
         }  
         ```

         

## AOP(Aspect Oriented Programming) 
面向切面编程: 对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率.

通俗描述: 不通过修改源代码方式, 在主干功能里添加新功能

- 动态代理

  - 有接口时, 使用 JDK 动态代理

    *创建接口实现类代理对象，增强类的方法*

    ![image-20200730134350329](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730134350.png)

  - 没有接口时, 使用 CGLIB 动态代理

    *创建子类的代理对象，增强类的方法*

    ![image-20200730111817011](/Users/qing/Library/Application%20Support/typora-user-images/image-20200730111817011.png)

- JDK 动态代理

  - 原理: 使用 Proxy 类里面的方法创建代理对象

    `java.lang.reflect.Proxy`

    ```java
    public static Object newProxyInstance(ClassLoader loader, Class<?>[] interfaces, InvocationHandler h)
    返回指定接口的代理类的实例, 该接口将方法调用分派给指定的调用处理程序
    ```

    三个参数:

    - 类加载器 
    - 增强方法所在的类，这个类实现的接口，支持多个接口 
    - 实现接口`InvocationHandler`，创建代理对象，写增强的部分

  - JDK动态代理底层代码

    1. 创建接口，定义方法

       ```java
       public interface UserDao {
       	public int add(int a,int b); 
           public String update(String id);
       }
       ```

       

    2. 创建接口实现类，实现方法

       ```java
       public class UserDaoImpl implements UserDao { 
           @Override
           public int add(int a, int b) {
               return a+b;
       	}
       	@Override
           public String update(String id) {
               return id;
       	} 
       }
       ```

       

    3. 使用 Proxy 类创建接口代理对象

       ```java
       public class JDKProxy{
           public static void main(String[] args) {
               //创建接口实现类代理对象
       		Class[] interfaces = {UserDao.class};
               UserDaoImpl userDao = new UserDaoImpl();
       		UserDao dao =(UserDao)Proxy.newProxyInstance(JDKProxy.class.getClassLoader(), interfaces, new UserDaoProxy(userDao));
               int result = dao.add(1, 2);
       		System.out.println("result:"+result);
           }
       }
       
       //创建代理对象代码
       class UserDaoProxy implements InvocationHandler { 
           // 传进来代理对象
           // 有参数构造传递
       	private Object obj;
       	public UserDaoProxy(Object obj) { 
               this.obj = obj;
       	}
       	//增强的逻辑
           @Override
           public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
               //方法之前
               System.out.println("方法之前执行...."+method.getName()+" :传递的参 数..."+ Arrays.toString(args));
               //被增强的方法执行
               Object res = method.invoke(obj, args); 
               //方法之后 
               System.out.println("方法之后执行...."+obj); 
               return res;
           }
       }
       ```

- 术语

  - 切面 Aspect: 把通知用到切入点的过程
  - 连接点 Join Point: 类中哪些方法可以被增强的方法, 这些方法称为连接点
  - 切入点Point cut: 实际被增强的方法
  - 通知(增强) Advice: 实际增强的逻辑部分
    - 前置 @Before
    - 返回 @AfterReturning 返回后才通知, 所以有异常时不通知
    - 环绕 @Around
    - 异常 @AfterThrowing
    - 最终 @After

- 准备

  1. Spring 框架一般都是基于 AspectJ 实现 AOP 操作
      AspectJ 不是 Spring 组成部分，是独立 AOP 框架，一般把 AspectJ 和 Spirng 框架一起使用.

  2. 实现AOP

     - 基于注解✔️
     - 基于 XML

  3. 引入依赖

     ![image-20200730155036008](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730155036.png)

  4. 切入点表达式

     1. 作用: 对哪个类里面的哪个方法进行增强

     2. 语法: `execution([权限修饰符] [返回类型(可省略] [类全路径].[方法名称]([参数列表]) )`

        e.g. 

        1. 对 `com.abc.dao.BookDao` 类里面的 add() 进行增强

           ```java
           execution(* com.abc.dao.BookDao.add(..))
           ```

           

        2. 对 `com.abc.dao` 包里面所有类，类里面所有方法进行增强

           ```java
           execution(* com.abc.dao.*.*(..))
           ```

           

- AspectJ 注解

  1. 创建类，在类里面定义方法

     ```java
     public class User {
         public void add() {
         	System.out.println("add......."); 
         }
     }
     ```

  2. 创建增强类

     ```java
     public class UserProxy {
     	//前置通知
         public void before() {
     		System.out.println("before......"); 
         }
     }
     ```

  3. 通知的配置

     1. 在配置文件中, 开启注解扫描

        ![image-20200730165825076](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730165825.png)

     2. 使用注解创建 User 和 UserProxy 对象,

        在增强类上面添加注解 `@Aspect`

        ![image-20200730170015464](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730170015.png)

        ![image-20200730170047740](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730170048.png)

     3. 在配置文件中开启生成代理对象

        ```xml
        <!-- 开启 Aspect 生成代理对象-->
        <aop:aspectj-autoproxy></aop:aspectj-autoproxy>
        ```

        

  4. 配置不同类型的通知

     在增强类的里面，在作为通知方法上面添加通知类型注解，使用切入点表达式配置

     ```java
     @Component
     @Aspect
     public class UserProxy {
         // 前置通知
         @Before(value = "execution(* com.atguigu.spring5.aopanno.User.add(..))") 
         public void before() {
     		System.out.println("before........."); 
         }
         // 其他通知类似
     }
     
     ```

  5. 抽取相同切入点

     ```java
     @Pointcut(value = "execution(* com.atguigu.spring5.aopanno.User.add(..))")
     public void pointdemo() {
     }
     
     // 调用@Pointcut
     @Before(value = "pointdemo()") 
     public void before() {
     	System.out.println("before........."); 
     }
     @After(value = "pointdemo()")
     public void after() {
         ...
     }
     ```

  6. 设置增强类优先级 (有多个增强类对同一个方法进行增强)

     在增强类上面添加注解 `@Order(数字类型值)`，数字类型值*越小*优先级*越高*

     ```java
     @Component
     @Aspect
     @Order(1)
     public class PersonProxy
     ```

     

  7. 完全注解开发

     创建配置类

        ```java
  @Configuration
  @ComponentScan(basePackages = {"com.atguigu"}) @EnableAspectJAutoProxy(proxyTargetClass = true) 
  public class ConfigAop
        ```

  

- AspectJ 配置文件

  1、创建两个类，增强类和被增强类，创建方法 

  2、在 spring 配置文件中创建两个类对象

  ```xml
  <!--创建对象-->
  <bean id="book" class="com.atguigu.spring5.aopxml.Book"></bean>
  <bean id="bookProxy" class="com.atguigu.spring5.aopxml.BookProxy"></bean>
  ```

  

  3、在 spring 配置文件中配置切入点
  
  ```xml
    <!--配置 aop 增强-->
    <aop:config> 
        <!--切入点-->
  	  <aop:pointcut id="p" expression="execution(* com.atguigu.spring5.aopxml.Book.buy(..))"/>
  	  <!--配置切面-->
  	  <aop:aspect ref="bookProxy"> 
            <!--增强作用在具体的方法上-->
  		  <aop:before method="before" pointcut-ref="p"/>
  	  </aop:aspect>
    </aop:config>
  ```

## JdbcTemplate

Spring 框架对 JDBC 进行封装，使用 JdbcTemplate 方便实现对数据库操作

- 准备工作:

1. 引入 jar 包

![image-20200730175142491](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200730175143.png)

2. 在 spring 配置文件配置数据库连接池

   ```xml
   <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" destroy-method="close">
   	<property name="url" value="jdbc:mysql:///user_db" />
   	<property name="username" value="root" />
       <property name="password" value="root" />
       <property name="driverClassName" value="com.mysql.jdbc.Driver" />
   </bean>
   ```

   

3. 配置 JdbcTemplate 对象，注入 dataSource

   ```xml
   <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate"> 
       <!--注入 dataSource-->
   	<property name="dataSource" ref="dataSource"></property>
   </bean>
   ```

   

4. 创建 service 类，创建 dao 类，在 dao 注入 jdbcTemplate 对象

   - 配置文件

     ```xml
     <context:component-scan base-package="com.atguigu"></context:component-scan>
     ```

   - Service

     ```java
     @Service
     public class BookService { 
         //注入 dao
     	@Autowired
         private BookDao bookDao;
     }
     ```

   - Dao

     ```java
     @Repository
     public class BookDaoImpl implements BookDao { 
         //注入 JdbcTemplate
     	@Autowired
     	private JdbcTemplate jdbcTemplate;
     }
     ```

- 操作数据库(添加)

    1. 实体类entities

    2. service, dao

        1. service 增加`add()`方法

        2. 在dao进行数据库添加操作

        3. 调用JdbcTemplate 对象里面 update 方法实现添加操作 `int update(String sql, Object... args)`

            > 参数:
            >
            > 1. sql语句 
            > 2. 设置 sql语句值

            ```java
            @Repository
            public class BookDaoImpl implements BookDao {
                //注入 JdbcTemplate
            	@Autowired
                private JdbcTemplate jdbcTemplate; 
                //添加的方法
                @Override
                public void add(Book book) {
                    // 创建 sql 语句
                    String sql = "insert into t_book values(?,?,?)";
                    // 调用方法实现
                    Object[] args = {book.getUserId(), book.getUsername(),
                    book.getUstatus()};
                    int updatedRows = jdbcTemplate.update(sql,args);
                    System.out.println(updatedRows);
                }
            }
            ```

            

- 操作数据库(修改 删除)

    ```java
    // 修改
    @Override
    public void updateBook(Book book) {
        String sql = "update t_book set username=?,ustatus=? where user_id=?"; 
        Object[] args = {book.getUsername(), book.getUstatus(),book.getUserId()}; 
        int update = jdbcTemplate.update(sql, args);
        System.out.println(update);
    }
    // 删除
    @Override
    public void delete(String id) {
    	String sql = "delete from t_book where user_id=?"; 
        int update = jdbcTemplate.update(sql, id); 
        System.out.println(update);
    }
    ```

    

- 操作数据库(查询返回某个值)

    `<T> T queryForObject(String sql, Class<T> requiredType)` 

    ```java
    // 查询记录数
    @override
    public int selectCount() {
        String sql = "select count(*) from t_book";
    	Integer count = jdbcTemplate.queryForObject(sql, Integer.class); 
        return count;
    }
    ```

    

- 操作数据库(查询返回对象)

    `<T> T queryForObject(String sql, RowMapper<T> rowMapper, Object... args)`

    > 参数:
    >
    > 1. sql
    >
    > 2. 针对返回的不同类型值，使用RowMappe接口里面实现类完成
    >
    >     数据封装
    >
    > 3. sql语句值

    ```java
    // 查询图书详情
    @Override
    public Book findBookInfo(String id) {
        String sql = "select * from t_book where user_id=?"; 
        //调用方法
        Book book = jdbcTemplate.queryForObject(sql, new BeanPropertyRowMapper<Book>(Book.class), id); 
        return book;
    }
    ```

    

- 操作数据库(查询返回集合)

    `<T> List<T> query(String sql, RowMapper<T> rowMapper, Object[] args)`

    ```java
    // 查询图书列表
    @Override
    public List<Book> findAllBook() {
        String sql = "select * from t_book";
        // 调用方法
        List<Book> bookList = jdbcTemplate.query(sql, new BeanPropertyRowMapper<Book>(Book.class)); 
        return bookList;
    }
    ```

    

- 操作数据库(批量)

    `int[] batchUpdate(String sql, List<Object[]> batchArgs)`

    ```java
    // 批量添加
    @Override
    public void batchAddBook(List<Object[]> batchArgs) { 
        String sql = "insert into t_book values(?,?,?)"; 
        int[] ints = jdbcTemplate.batchUpdate(sql, batchArgs);
        System.out.println(Arrays.toString(ints));
    }
    ```

## 事务

- 事务是数据库操作最基本单元，逻辑上的一组操作，要么都成功，如果有一个失败所有操作都失败.

- 事务四个特性(**ACID**) 

    (1) 原子性
    (2) 一致性
    (3) 隔离性
    (4) 持久性

- Spring 事务管理

    - 事务添加到 JavaEE三层结构(Web, Service, Dao)里的 Service

    - Spring事务管理操作(底层是 AOP): 编程式事务管理, 声明式事务管理

    - 声明式事务管理

        - 基于注解
        - 基于xml

    - API

        ![image-20200908202553834](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200908202554.png)

- 注解声明式

    1. 配置事务管理器

        ```xml
        <!--创建事务管理器--> 
        <bean id="transactionManager"
        class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        	<!--注入数据源-->
        	<property name="dataSource" ref="dataSource"></property>
        </bean>
        ```

    2. 开启事务注解

        1. 引入命名空间 tx

            <img src="https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200909104149.png" alt="image-20200909104148895" style="zoom:50%;" />

        2. 开启事务注解

            ```xml
            <tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>
            ```

    3. 在 Service 类上面(或者 Service 类里面方法上面)添加事务注解`@Transactional`

        ```java
        @Service
        @Transactional
        public class UserService
        ```

    - 参数配置

        - propagation 传播行为

            | 事务传播行为类型 | 说明                                                         |
            | ---------------- | ------------------------------------------------------------ |
            | **REQUIRED**     | 如果当前没有事务，就新建一个事务，如果已经存在一个事务中，加入到这个事务中。这是默认的. |
            | **REQUIRES_NEW** | 新建事务，如果当前存在事务，把当前事务挂起。                 |
            | SUPPORTS         | 支持当前事务，如果当前没有事务，就以非事务方式执行。         |
            | MANDATORY        | 使用当前的事务，如果当前没有事务，就抛出异常                 |
            | NOT_SUPPORTED    | 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。   |
            | NEVER            | 以非事务方式执行，如果当前存在事务，则抛出异常。             |
            | NESTED           | 如果当前存在事务，则在嵌套事务内执行。如果当前没有事务，则执行与PROPAGATION_REQUIRED类似的操作。 |

            

        - isolation 隔离级别

            - 三个读问题: 脏读, 不可重复读, 幻读

                1. 脏读: 一个未提交事务读取到另一个未提交事务的数据
                2. 不可重复读: 一个未提交事务读取到另一个提交事务修改的数据
                3. 幻读: 一个未提交事务读取到另一个提交事务添加的数据

            - 解决方案

                ![事务隔离级别](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200909111707.bmp)

                > MySQL 默认: 可重复读

        - timeout 超时时间

            - 事务需要在一定时间内进行提交，如果不提交进行回滚 
            - 默认值是 -1 ，设置时间以秒单位进行计算

        - readOnly 是否只读

            - 默认值是 false. 设置为 true 后,只能查询

        - rollbackFor 回滚

            - 设置出现哪些异常进行事务回滚

        - noRollbackFor 不回滚

            - 设置出现哪些异常不进行事务回滚

## 日志框架

- Spring 5 移除 Log4jConfigListener, 已整合 Log4j2
1. 引入 jar 包

2. 创建 log4j2.xml 配置文件

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!--日志级别以及优先级排序: OFF < FATAL < ERROR < WARN < INFO < DEBUG < TRACE < ALL -->
    <!--Configuration后面的status用于设置log4j2自身内部的信息输出，可以不设置，当设置成trace时，可以看到log4j2内部各种详细输出-->
    <configuration status="INFO">
        <!--先定义所有的appender-->
        <appenders>
            <!--输出日志信息到控制台-->
            <console name="Console" target="SYSTEM_OUT">
                <!--控制日志输出的格式-->
                <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
        </console>
        </appenders>
        <!--然后定义logger，只有定义了logger并引入的appender，appender才会生效-->
        <!--root：用于指定项目的根日志，如果没有单独指定Logger，则会使用root作为默认的日志输出-->
        <loggers>
            <root level="info">
                <appender-ref ref="Console"/>
            </root>
        </loggers>
    </configuration>
    ```
    
    

## Spring5 核心容器支持`@Nullable`, 函数式风格

`@Nullable` 可以使用在方法, 属性, 参数上面，表示方法返回值, 属性值, 参数值可以为空.

## Spring5 支持整合 JUnit5

## Webflux

异步非阻塞框架

> 异步和同步针对调用者，调用者发送请求，如果等着对方回应之后才去做其他事情就是同步，如果发送请求之后不等着对方回应就去做其他事情就是异步
>
> 阻塞和非阻塞针对被调用者，被调用者受到请求之后，做完请求任务之后才给出反馈就是阻塞，受到请求之后马上给出反馈然后再去做事情就是非阻塞

![1 SpringMVC和Webflux比较](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200909162616.bmp)







- ~~SSH(Struts, Spring, Hibernate)~~ -> SSM（Spring+SpringMVC+MyBatis）