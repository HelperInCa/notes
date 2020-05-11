- [Basics](#basics)
  * [Java](#java)
  * [Python3](#python3)
    + [(TBD)](#-tbd-)
  * [Golang](#golang)
  * [Database](#database)
- [Hotkeys](#hotkeys)
- [Git](#git)
  * [git init](#git-init)
  * [git status](#git-status)
  * [git add](#git-add)
  * [git commit](#git-commit)
  * [git log](#git-log)
  * [git push](#git-push)
  * [git pull](#git-pull)
  * [git remote](#git-remote)
    + [rename](#rename)
    + [remove](#remove)
  * [git rm](#git-rm)
    - [remove pushed files/folders from repo](#remove-pushed-files/folders-from-repo)
- [Tools](#Tools)
  - [import Markdown to Medium](#import-Markdown-to-Medium)
  - [Zsh](#Zsh)
  - [Plugins](#Plugins)
- [Docker](#Docker)

# Basics

## Java

[github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/Java%20basic.md)

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

[github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/Golang%20basics.md)

## Database

[github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/Database.md)



# Hotkeys

- [github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/hotkey.md)
- [cheetsheets including languages, tools, libraries](https://github.com/skywind3000/awesome-cheatsheets)



# Git

> Sources:
>
> - [GItHub help](https://help.github.com/en/github)
> - [脑图](http://naotu.baidu.com/file/8f3e66d234023d218379fc8ef7790fe0?token=652534011488cbfa) 

![](https://ipic-1300911741.cos.na-siliconvalley.myqcloud.com/2020-04-19-233217.jpg)

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

- Commitizen

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

    ![](https://raw.githubusercontent.com/commitizen/cz-cli/master/meta/screenshots/add-commit.png)

## git log

## git push

## git pull

- refusing to merge unrelated histories

  git pull origin master --allow-unrelated-histories

## git remote

### rename

Use the `git remote rename` command to rename an existing remote.

```shell
$ git remote -v
# View existing remotes
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)

$ git remote rename origin destination
# Change remote name from 'origin' to 'destination'
```

### remove

Use the `git remote rm` command to remove a remote URL from your repository.

## git rm

- remove commited files/folders from repo

  ```shell
  $ git rm -r --cached FOLDER/
  $ git commit -m'delete FOLDER'
  $ git push orgin master
  ```

  update `.gitignore`



# Tools

## import Markdown to Medium

- create a private Gist and paste the Markdown
- `command` + `c` the file on GIst and `command` + `v` on Medium

> cons:
>
> - not support HTML

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

## Plugins

- [trash](https://github.com/ali-rantakari/trash)

  allow `rm` to move files to .Trash/ and have the "put back" feature

# Docker

## 脑图

![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/2020-05-09-071113.png)

> [脑图网盘](https://pan.baidu.com/s/1DF_ms43e5Qvvrfr2mdcfAg) 提取码: 9e7f
>
> [中文文档](https://yeasy.gitbook.io/docker_practice/)

- Docker 容器后台运行时, 必须要有一个前台进程, 否则会自动停止

