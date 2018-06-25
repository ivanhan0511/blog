---
layout: post
title: Work Environment with Manjaro
---

This is a record about how to configure a Linux environment for work after getting a whole new pc, NOT include macOSX.

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

#### Input method
- fcitx-sogoupinyin
  ```shell
  sudo pacman -S fcitx-im
  sudo pacman -S fcitx-configtool
  ```
- Add content below into `~/.xprofile` or `~/.extend.xprofile`
  > export GTK_IM_MODULE=fcitx
  > export QT_IM_MODULE=fcitx
  > export XMODIFIERS="@im=fcitx"

#### MultiDisplay
Actually, it is not really need multiDiskplay, because thereis no desktop in FreeBSD
and there are multiDesktop in Manjaro and macOS
- Manjaro i3wm 17.1.5
  ```shell
  xrandr --auto --output DP1 --mode 1920x1080 --right-of HDMI1
  ```


### PyCharm Pro
---
#### Installation
- PyCharm Pro
  `https://blog.csdn.net/u014044812/article/details/78727496`


#### Configuration
- 将.idea目录加入ignore清单：
  ```shell
  echo '.idea' >> .gitignore
  git rm --cached -r .idea
  git add .gitignore
  git commit -m '(gitignore commit and remove .idea)'
  git push
  ```


### VirtualBox
---

VirtualBox
it will show something like this Linux user 4.6.0-1-MANJARO #1 SMP PREEMPT Mon May 16 02:44:59 2016 x86_64 GNU/Linux
In bold is your kernel version, so install the virtualbox host modules for your kernel number replacing 46 with what your output showed from the above.
sudo pacman -S linux46-virtualbox-host-modules
Now load your virtualbox module
sudo /sbin/rcvboxdrv setup
Virtualbox should run normally now - if not, use pamac and uninstall anything related to virtualbox then just install the 'virtualbox' package and it will do the above for you if you tell it the kernel version you are using
http://idea.iteblog.com/key.php



















Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page: About]({{ site.baseurl }}/about).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# [](#header-1)Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## [](#header-2)Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
---
layout: default
title: RD and Testing Env
---

# RD and Testing Env
## Work in Manjaro, FreeBSD and macOSX



### Catalogue

- Introduction


- Basic Configuration
  - Input method
  - oh-my-zsh
  - z
  - vim
  - MultiDisplay
  - VirtualBox etc.

- Development
  - Python3
  - PostgreSQL
  - PyCharm
  - DataGrip








### Introduction

---

I have RD project both in two environments, and the resolution is as below:

#### Work Env

- Server: Ubuntu and FreeBSD in normal server
- Client: Manjaro i3wm in normal pc

#### Home Env

- Both server and client are in MacBookPro

#### Software

- Python + Django + PostgreSQL + MQTT(mosquitto)


  

  


### Basic Configuration
---
#### Basic

- Manjaro i3wm 17.0
- macOS 10.13
- FreeBSD 12.0



#### Input method

- Manjaro i3wm 17.0
  - 安装搜狗输入法及图形化配置工具
    ```shell
    sudo pacman -S fcitx-im
    sudo pacman -S fcitx-configtool
    ```
  - 在`~/.xprofile`或`~/.extend.xprofile`文件里面添加下面三行
    > export GTK_IM_MODULE=fcitx
    > export QT_IM_MODULE=fcitx
    > export XMODIFIERS="@im=fcitx"



- macOS
- FreeBSD



#### oh-my-zsh
https://github.com/robbyrussell/oh-my-zsh
相关文档http://macshuo.com/?p=676




#### z
https://github.com/rupa/z


#### MultiDisplay
Actually, it is not really need multiDiskplay, because thereis no desktop in FreeBSD 
and there are multiDesktop in Manjaro and macOS
- Manjaro i3wm 17

  ```shell
  xrandr --auto --output DP1 --mode 1920x1080 --right-of HDMI1
  ```



#### VirtualBox

VirtualBox
it will show something like this Linux user 4.6.0-1-MANJARO #1 SMP PREEMPT Mon May 16 02:44:59 2016 x86_64 GNU/Linux
In bold is your kernel version, so install the virtualbox host modules for your kernel number replacing 46 with what your output showed from the above.
sudo pacman -S linux46-virtualbox-host-modules
Now load your virtualbox module
sudo /sbin/rcvboxdrv setup
Virtualbox should run normally now - if not, use pamac and uninstall anything related to virtualbox then just install the 'virtualbox' package and it will do the above for you if you tell it the kernel version you are using
http://idea.iteblog.com/key.php

  

  


#### PostgreSQL

mariadb100-server is marked broken in FreeBSD arm 12.0
Both mysql and mariadb are **sucks**, so go into PostgreSQL
The difference between these 3 systems is the path.
As example of FreeBSD

```shell
su root
ports install postgresql10-server
pw user add postgres
chown postgres:postgres /var/db/postgres/data

su - postgres
initdb -D /var/db/postgres/data
postgres -D /var/db/postgres/data &
vi /var/db/postgres/data/pg_hba.conf
```
> host    all             all              0.0.0.0/0              md5

```shell
vi /var/db/postgres/data96/postgresql.conf
```
> listen_addresses = '\*'

Export and import database like below
```shell
pg_dump -U USERNAME DBNAME > dbexport.pgsql
#pg_dump -U USERNAME DBNAME -N topology -T spatial_ref_sys > dbexport.pgsql  # If with restricted access permissions
psql -U USERNAME DBNAME < dbexport.pgsql
```

Python __private(self)的轧压
'http://greybeard.iteye.com/blog/1355216'


- create database of postgresql
- PyCharm: python3 manage.py migrate
- python3 manage.py createsuperuser


>>> for i in enumerate('b 2:6 rwm'):
...     print(i)
...
(0, 'b')
(1, ' ')
(2, '2')
(3, ':')
(4, '6')
(5, ' ')
(6, 'r')
(7, 'w')
(8, 'm')



