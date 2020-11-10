<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Basics](#basics)
  - [Java](#java)
  - [Kotlin TODO](#kotlin-todo)
  - [Python3](#python3)
    - [(TBD)](#tbd)
  - [Golang](#golang)
  - [Database](#database)
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
- [Docker](#docker)
  - [脑图](#%E8%84%91%E5%9B%BE)
- [Bash](#bash)
- [My Alias](#my-alias)
- [Spring Boot](#spring-boot)
- [线上问题排查](#%E7%BA%BF%E4%B8%8A%E9%97%AE%E9%A2%98%E6%8E%92%E6%9F%A5)
- [Jira](#jira)
- [Spring5](#spring5)
- [Spring Cloud](#spring-cloud)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Basics

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
    $ git config --local user.name xxx@xxx.com
    $ git config commit.template [filepath]
    ```

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

## Vim

`A`命令模式: 从行尾插入

`I`命令模式: 从行首插入

# Docker

## 脑图

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-09-071113.png)

> [脑图网盘](https://pan.baidu.com/s/1DF_ms43e5Qvvrfr2mdcfAg) 提取码: 9e7f
>
> [中文文档](https://yeasy.gitbook.io/docker_practice/)

- Docker 容器后台运行时, 必须要有一个前台进程, 否则会自动停止

- Docker 1.13之后, 支持prune命令，快速删除已退出的容器

    ```shell
    $ docker container prune
    ```

    

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

