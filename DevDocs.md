<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Basics](#basics)
  - [k8s](#k8s)
  - [Java](#java)
  - [Kotlin TODO](#kotlin-todo)
  - [Python3](#python3)
    - [(TBD)](#tbd)
  - [Golang](#golang)
  - [Database](#database)
- [Todo](#todo)
- [Hotkeys](#hotkeys)
- [Git](#git)
  - [常用命令](#%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4)
  - [git init](#git-init)
    - [git clone](#git-clone)
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
  - [本机alias](#%E6%9C%AC%E6%9C%BAalias)
- [Maven](#maven)
- [Tools](#tools)
  - [Gist](#gist)
  - [Zsh](#zsh)
  - [Vim](#vim)
  - [ntpd](#ntpd)
- [Docker](#docker)
  - [脑图](#%E8%84%91%E5%9B%BE)
- [Bash](#bash)
- [My Alias](#my-alias)
- [Spring Boot](#spring-boot)
- [线上问题排查](#%E7%BA%BF%E4%B8%8A%E9%97%AE%E9%A2%98%E6%8E%92%E6%9F%A5)
- [Jira](#jira)
- [Spring5](#spring5)
- [Spring Cloud](#spring-cloud)
- [Misc](#misc)
  - [Gorm](#gorm)
  - [多个入参: 重载构造器 / JavaBeans / Builder](#%E5%A4%9A%E4%B8%AA%E5%85%A5%E5%8F%82-%E9%87%8D%E8%BD%BD%E6%9E%84%E9%80%A0%E5%99%A8--javabeans--builder)
  - [Java 中 Object 转 String 的几种方法](#java-%E4%B8%AD-object-%E8%BD%AC-string-%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E6%B3%95)
  - [Swagger](#swagger)
  - [Spring validation框架](#spring-validation%E6%A1%86%E6%9E%B6)
  - [Jackson](#jackson)
- [单元测试](#%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95)
  - [Junit](#junit)
    - [测试依赖组件(DOC)](#%E6%B5%8B%E8%AF%95%E4%BE%9D%E8%B5%96%E7%BB%84%E4%BB%B6doc)
    - [测试替身(Test Double)](#%E6%B5%8B%E8%AF%95%E6%9B%BF%E8%BA%ABtest-double)
    - [Test fixture](#test-fixture)
    - [测试套件](#%E6%B5%8B%E8%AF%95%E5%A5%97%E4%BB%B6)
    - [测试异常](#%E6%B5%8B%E8%AF%95%E5%BC%82%E5%B8%B8)
  - [Mockito](#mockito)
- [Linux 工具](#linux-%E5%B7%A5%E5%85%B7)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Basics

## k8s

[notes](https://github.com/HelperInCa/notes/blob/master/modules/k8s.md)

## Java

[notes](https://github.com/HelperInCa/notes/blob/master/modules/Java.md)

## Kotlin TODO

[note](https://github.com/HelperInCa/notes/blob/master/modules/Kotlin.md)

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

# Todo

- Redis 入门

    - [ ] [1](https://mp.weixin.qq.com/s/-3fcK4WspGk6SEsaVrdx8A)

    - [ ] [2](https://mp.weixin.qq.com/s/7ct-mvSIaT3o4-tsMaKRWA)

- Golang

    - [ ] [编程思想](https://mp.weixin.qq.com/s/llmE9QpnrvA02AtvfHtqJQ)

    - [x] [高性能编程](https://mp.weixin.qq.com/s/Lv2XTD-SPnxT2vnPNeREbg)

    - [ ] [并发编程](https://mp.weixin.qq.com/s/V0krCjWrndzz71cVOPBxdg)

- Linux

    - [ ] [Linux IO 的一些基本原理](https://mp.weixin.qq.com/s/diKfeu1-Lr4ZA5Ky_66TZg)

# Hotkeys

[Collections](https://github.com/HelperInCa/notes/blob/master/modules/hotkey.md)

# Git

> Sources:
>
> - [GItHub help](https://help.github.com/en/github)
> - [脑图](http://naotu.baidu.com/file/8f3e66d234023d218379fc8ef7790fe0?token=652534011488cbfa) 

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-14-git%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE.png)

## 常用命令

- 回滚

    ![image-20200927175807654](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200927175807.png)
    
- 本地配置信息(公司的应**单独**配置)

    ```shell
    $ git config --local user.name xxx
    $ git config --local user.email xxx@xxx.com
    $ git config commit.template [filepath]
    ```
    
    git push origin HEAD:refs/for/{branchname} **我们采用这种方式提交代码，表示将本地分支修改提交到gerrit上，自动生成patch，此时会在gerrit上生成review request**

## git init

### git clone

- 拉取指定分支

    ```shell
    git clone -b [分支名] [clone URL]
    ```

    

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

  ```shell
  vim ~/.gitignore_global
  git config --global core.excludesfile ~/.gitignore_global
  ```

## 本机alias

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

       ![image-20200804111750030](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201126135506.png)

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

  ![image-20200804142937006](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201126135455.png)

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

## Vim

`A`命令模式: 从行尾插入

`I`命令模式: 从行首插入

## ntpd

[ntpd](http://xstarcd.github.io/wiki/sysadmin/ntpd.html)

# Docker

## 脑图

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201126135433.png)

> [脑图网盘](https://pan.baidu.com/s/1DF_ms43e5Qvvrfr2mdcfAg) 提取码: 9e7f
>
> [中文文档](https://yeasy.gitbook.io/docker_practice/)

- Docker 容器后台运行时, 必须要有一个前台进程, 否则会自动停止

- Docker v1.13之后, 支持prune命令，快速删除已退出的容器

    ```shell
    docker container prune
    ```

- 本地镜像导出/导入

    ```shell
    docker images
    docker save myimage:latest | gzip > myimage_latest.tgz
    docker load -i xxx.tgz
    ```

- 重命名 image

    ```shell
    docker tag olderImageName:oldVersion newImagesName:newVersion
    docker rmi olderImageName:oldVersion
    ```

- `docker system` 管理 docker

    - `docker system df` show disk usage

        ![image-20211012100400860](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20211012100401.png)

    - `docker builder prune` clean build cache

        Docker 18.09 引入了 BuildKit ，提升了构建过程的性能、安全、存储管理等能力。

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

# 线上问题排查

[来源](https://mp.weixin.qq.com/s/tG1kOGtAJzHc37XGlsfAPQ) 

# Jira

# Spring5

[Spring5](https://github.com/HelperInCa/notes/blob/master/modules/Spring.md)

# Spring Cloud



# Misc

## Gorm

Golang ORM

- `Next()` 之后最好手动 `close()` 

    [refer](https://learnku.com/articles/39382)

    rows.Next () 在获取到最后一条记录之后，会调用 rows.Close () 将连接放回连接池或交给其他等待的请求方，所以不需要手动调用 rows.Close ()，

    而出问题的 demo 中，由于 rows.Next () 没有执行到最后一条记录处，也没有调用 rows.Close ()

- [错误处理](https://gorm.io/zh_CN/docs/error_handling.html)

    1. 在调用任何 [Finisher 方法](https://gorm.io/zh_CN/docs/method_chaining.html#finisher_method) (``Create`, `First`, `Find`, `Take`, `Save`, `Update`, `Delete`, `Scan`, `Row`, `Rows`...)后，都进行错误检查

    2. `ErrRecordNotFound`

        ```go
        // 检查错误是否为 
        RecordNotFounderr := db.First(&user, 100).Error
        errors.Is(err, gorm.ErrRecordNotFound)
        ```

## 多个入参: 重载构造器 / JavaBeans / Builder

[参考](https://www.jianshu.com/p/5b6bdf298727)

- Builder 优点: 

    如果类的构造器或者静态工厂中具有多个参数，设计这种类时，Builder模式就是不错的选择，特别是当大多数参数都是可选的时候。
    与重载构造器相比，builder模式的客户端更易与阅读和编写.
    与JavaBeans相比，线程安全.

- 缺点: 

    创建对象就必须创建Builder, 有开销.

    比重载构造器模式更加的冗长，因此它会在参数多的时候使用。但如果知道，我们可能会在设计之后还要添加参数，所以已开始就用Builder比较好。

## Java 中 Object 转 String 的几种方法

**1.object.toString()方法**

  这种方法要注意的是object不能为null,否则会报NullPointException，

**2.String.valueOf(object)方法**

  这种方法不必担心object为null的问题，若为null，会将其转换为"null"字符串，而不是null。这一点要特别注意。"null"和null不是一个概念。

**3.“”+object方法**

  这种方法也不必担心object为null的问题。但若object为null,会返回"null"字符串，和String.valueOf(object)一样。

**4.(String)(object)方法**

  这种方法也不必担心object为null的问题。但是，object要是能转换为String的对象。若Object object = 1,再(String)1，会报类转换异常。

## Swagger

`@ApiParam`用于swagger提供API文档，文档中生成的注释内容

## Spring validation框架

[总结](https://blog.csdn.net/u012373815/article/details/72049796) 

[@Valid vs @Validated](https://blog.csdn.net/qq_27680317/article/details/79970590) 

`@Validated`只能用在类、方法和参数上，而`@Valid`可用于方法、字段、构造器和参数上, 且能嵌套验证

> `spring validation`是对`hibernate validator`的二次封装
>
> hibernate validator 使用: [refer](https://www.jianshu.com/p/0bfe2318814f)  [getting starter](https://docs.jboss.org/hibernate/validator/7.0/reference/en-US/html_single/#validator-gettingstarted)  

## Jackson

[refer](https://developer.ibm.com/zh/articles/jackson-advanced-application/)

1. 注解方式

2. ObjectMapper

    - 可配置序列化/反序列化过程

        `objectMapper.configure(DeserializationFeature.XXX, true)` 

    - Jackson反序列时，将LinkedHashMap转成对象convertValue`(): map -> 自定义类型

    - `TypeFactory.constructParametricType()`

3. 将部分字段解析为日期格式

4. 自定义序列化/反序列化

# 单元测试

在单元测试中, 我们需要保证被测系统是独立的(SUT 没有任何的 DOC), 即当被测系统通过测试时, 那么它在任何环境下都是能够正常工作的. **编写单元测试时, 仅仅需要关注单个类就可以了.** 而不需要关注例如数据库服务, Web 服务等组件.

## Junit

### 测试依赖组件(DOC)

被测系统所依赖的组件, 例如进程 UserService 的单元测试时, UserService 会依赖 UserDao, 因此 UserDao 就是 DOC.

### 测试替身(Test Double)

一个实际的系统会依赖多个外部对象, 但是在进行单元测试时, 我们会用一些功能较为简单的并且其行为和实际对象类似的假对象来作为 SUT 的依赖对象, 以此来降低单元测试的复杂性和可实现性. 在这里, 这些假对象就被称为 **测试替身**

测试替身有如下 5 种类型:

- Test stub, 为 SUT 提供数据的假对象.
    我们举一个例子来展示什么是 Test stub.

假设我们的一个模块需要从 HTTP 接口中获取商品价格数据, 这个获取数据的接口被封装为 getPrice 方法. 在对这个模块进行测试时, 我们显然不太可能专门开一个 HTTP 服务器来提供此接口, 而是提供一个带有 getPrice 方法的假对象, 从这个假对象中获取数据.
在这个例子中, 提供数据的假对象就叫做 Test stub.

- Fake object
    实现了简单功能的一个假对象. Fake object 和 Test stub 的主要区别就是 Test stub 侧重于用于提供数据的假对象, 而 Fake object 没有这层含义.

使用 Fake object 的最主要的原因就是在测试时某些组件不可用或运行速度太慢, 因而使用 Fake object 来代替它们.

- Mock object
    用于模拟实际的对象, 并且能够校验对这个 Mock object 的方法调用是否符合预期.

实际上, Mock object 是 Test stub 或 Fake object 一种, 但是 Mock object 有 Test stub/Fake object 没有的特性, Mock object 可以很灵活地配置所调用的方法所产生的行为, 并且它可以追踪方法调用, 例如一个 Mock Object 方法调用时传递了哪些参数, 方法调用了几次等.

- Dummy object: 在测试中并不使用的, 但是为了测试代码能够正常编译/运行而添加的对象. 例如我们调用一个 Test Double 对象的一个方法, 这个方法需要传递几个参数, 但是其中某个参数无论是什么值都不会影响测试的结果, 那么这个参数就是一个 Dummy object.
    Dummy object 可以是一个空引用, 一个空对象或者是一个常量等.

简单的说, Dummy object 就是那些没有使用到的, 仅仅是为了填充参数列表的对象.

- Test Spy
    可以包装一个真实的 Java 对象, 并返回一个包装后的新对象. 若没有特别配置的话, 对这个新对象的所有方法调用, 都会委派给实际的 Java 对象.

mock 和 spy 的区别是: mock 是无中生有地生出一个完全虚拟的对象, 它的所有方法都是虚拟的; 而 spy 是在现有类的基础上包装了一个对象, 即如果我们没有重写 spy 的方法, 那么这些方法的实现其实都是调用的被包装的对象的方法.

### Test fixture

运行测试程序所需要的先决条件(precondition). 即对被测对象进行测试时锁需要的一切东西. 

这个 **东西** 不单单指的是数据, 同时包括对被测对象的配置, 被测对象所需要的依赖对象等.

在 JUnit4, 

`@Before` 在每个测试方法运行前都会被调用, `@After` 在每个测试方法运行后都会被调用.

因为 @Before 和 @After 会在每个测试方法前后都会被调用, 而有时我们仅仅需要在测试前进行一次初始化, 这样的情况下, 可以使用`@BeforeClass` 和`@AfterClass` 注解.

### 测试套件

通过`@RunWith` 和`@SuiteClass` 两个注解, 我们可以创建一个测试套件`RunAllTest`, 批量运行测试类.

```java
@RunWith(Suite.class)
@SuiteClasses({
        CountTest.class,
        TestFixture.class,
        AssertTest.class,
        TestRunSequence.class,
})
public class RunAllTest {

}
```

### 测试异常

```java
public class MyClass {
	// 被测试方法
    public static int divide(int a, int b) {
    	if (b != 0) {
    		return a/b;
    	} else throw new IllegalArgumentException("b 不能为 0");    
    }
}
```

```java
public class MyTest {
    @Rule
    public ExpectedException ee = ExpectedException.none();
	
    @Test
    public void test() throws Exception {
        ee.expect(IllegalArgumentException.class);
        ee.expectMessage("b 不能为 0");
        MyClass.divide(1, 0);
    }
}
```

被测试方法写在 expectedEx.expectXxx() 方法**后面**!

## Mockito

# Linux 工具

- ```shell
    # journalctl 日志用量
    journalctl --disk-usage
    # 磁盘用量
    df -h [目录]
    ```

- strace

    跟踪进程中系统调用

    [refer](https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/strace.html)

    ```shell
    sudo strace -p $pid
    ```

- nc

    监听端口

    ```shell
    # 安装nc
    sudo yum -y install nc
    # 监听 tcp 端口(比如 12345)
    nc -lv 12345
    # 向 tcp 12345 端口发消息
    nc localhost 12345 # OR 使用 Telnet
    
    # 监听 udp 端口(比如 12345)
    nc -lvu 12345
    # 向 udp 12345 端口发消息
    nc -uv localhost 12345
    ```

- tar

    ```shell
    tar czvf [target.tgz] [file1] [file2]
    tar xzvf [source.tgz] 解压到当前目录
    ```

    

- du & df

    ```shell
    du -h --max-depth=0 [mydir] mydir占用磁盘大小,不向下递归下属目录
    
    df -h 查看系统的磁盘使用情况
    ```

    ![20211112173332](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20211112173332.jpg)

- 后台执行

    [refer](https://blog.csdn.net/liuyanfeier/article/details/62422742)

    - `&` 后台执行

    ```shell
    # 所有的标准输出和错误输出都将被重定向到out.log
    command  >  out.log  2>&1  &
    ```

    - `nohup`(no hang up)

        `&`实现后台执行, 但是一但把当前控制台关掉(退出帐户时)，作业就会停止运行

        ```shell
        nohup command > out.log 2>&1 &
        ```

    - `jobs`

        查看当前有多少在后台运行的命令。
        jobs -l选项可显示所有任务的PID，jobs的状态可以是running, stopped, Terminated。但是如果任务被终止了（kill），shell 从当前的shell环境已知的列表中删除任务的进程标识。

    - 2>&1解析
        `command >out.file 2>&1 &`

        - command>out.file是将command的输出重定向到out.file文件，即输出内容不打印到屏幕上，而是输出到out.file文件中。
        - 2>&1 是将标准出错重定向到标准输出，这里的标准输出已经重定向到了out.file文件，即将标准出错也输出到out.file文件中。最后一个&， 是让该命令在后台执行。
            试想2>1代表什么，2与>结合代表错误重定向，而1则代表错误重定向到一个文件1，而不代表标准输出；换成2>&1，&与1结合就代表标准输出了，就变成错误重定向到标准输出.

- netstat

    命令行网络工具

    [refer](https://www.jianshu.com/p/b866f3f6e46e)

    - 正在监听的某一tcp端口

        `netstat -tlnp |grep [$your port]`
