---
layout: post
title: "Work Environment with Manjaro"
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
