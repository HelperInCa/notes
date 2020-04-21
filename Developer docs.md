- [Basics](#basics)
  * [Java](#java)
  * [Python3](#python3)
    + [(TBD)](#-tbd-)
      - [new way to format string](#new-way-to-format-string)
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
  * [git rm](#git rm)
    - [remove pushed files/folders from repo](#remove pushed files/folders from repo)

# Basics

## Java

[github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/Java%20basic.md)

## Python3

### (TBD)

#### new way to format string

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

[github.com/HelperInCa/](https://github.com/HelperInCa/notes/blob/master/older/hotkey.md)



# Git

> Sources:
>
> - [GItHub help](https://help.github.com/en/github)
> - [思维导图](https://www.processon.com/view/link/5e9ce3fa5653bb6efc5b3b1b) Kc91

![](https://ipic-1300911741.cos.na-siliconvalley.myqcloud.com/2020-04-19-233217.jpg)

## git init

## git status

## git add

## git commit

> git commit -am "<message>"

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
  $ git rm -r --cashed FOLDER/
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

    输入xxx.rb, 将自动用vi打开. 输入xxx.gz, 将按照tar -xzvf解压

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

  

