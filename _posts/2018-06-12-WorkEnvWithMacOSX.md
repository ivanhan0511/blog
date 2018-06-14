---
layout: post
title: Work Environment with macOSX
---

This is a record about how to configure a macOSX environment for work after getting a whole new Macintosh

### Basic configuration
---

#### SSH Key
- Generate SSH key if needed
  ```shell
  ssh-keygen -t rsa -b 4096
  ```


#### Shell
- Change `bash` to `zsh`, without `sudo`. If it is after `sudo`, it changed shell of root user, not current user.
  ```shell
  chsh -s $(which zsh)
  ```

- Install oh-my-zsh
  ```shell
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```

- Install `z`, follow the steps in README
  ```shell
  git clone git@github.com:rupa/z.git
  ```

#### Vim
- Get ready a `.vimrc`
  # TODO: make a share link.


### PyCharm Pro
---
#### Installation
- PyCharm Pro
  `https://blog.csdn.net/u014044812/article/details/78727496`


#### Configuration
将.idea目录加入ignore清单：
$ echo '.idea' >> .gitignore
2
从git中删除idea：
$ git rm —cached -r .idea
3
将.gitignore文件加入git：
$ git add .gitignore
4
Commit gitignore文件，将.idea从源代码仓库中删除：
$ git commit -m '(gitignore commit and remove .idea)'
5
Push到服务器：
 $ git push
