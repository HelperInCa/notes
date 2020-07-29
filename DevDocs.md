<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Basics](#basics)
  - [Java](#java)
  - [Python3](#python3)
    - [(TBD)](#tbd)
  - [Golang](#golang)
  - [Database](#database)
  - [运算符的优先级](#%E8%BF%90%E7%AE%97%E7%AC%A6%E7%9A%84%E4%BC%98%E5%85%88%E7%BA%A7)
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
- [Tools](#tools)
  - [Gist](#gist)
  - [Zsh](#zsh)
- [Docker](#docker)
  - [脑图](#%E8%84%91%E5%9B%BE)
- [Bash](#bash)
- [My Alias](#my-alias)
- [Spring Boot](#spring-boot)
- [Jira](#jira)
- [Spring](#spring)
  - [IoC(Inversion of Control) 控制反转](#iocinversion-of-control-%E6%8E%A7%E5%88%B6%E5%8F%8D%E8%BD%AC)
  - [Bean管理](#bean%E7%AE%A1%E7%90%86)

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

## 运算符的优先级

> [refer](https://www.cnblogs.com/pinlantu/p/9853493.html)

若没有圆括号加以约束，那么对于数值变量来说，优先级顺序依次为：+正号、-负号 **＞** 乘号*、除号/、取余数符号% **＞** 加号+、减号- **＞** 大于号、等号、小于号、不等号 **＞** 各种赋值符号；对于布尔变量来说，优先级顺序依次为：逻辑非 **＞** 等号、不等号 **＞** 逻辑与、或、异或 **＞** 各种赋值符号。

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

[NoteTODO]()

# Jira

# Spring

- Pros:

  - Lightweight
  - opensource
## IoC(Inversion of Control) 控制反转

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

     - XML

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

         

- **AOP**(Aspect Oriented Programming) 面向切面编程

  *what where when*

  - Aspect: classes like TimeRecordingAspect, LogAspect, etc
  - Pointcut: Regular Expression
  - Advice: @Before, @AfterReturning, @Around 

- SSH(Struts, Spring, Hibernate)