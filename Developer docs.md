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

# Basics

## Java



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



## Database







# Hotkeys

# Git

> Sources:
>
> - [GItHub help](https://help.github.com/en/github)

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

