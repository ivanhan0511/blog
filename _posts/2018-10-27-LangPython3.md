---
layout: post
title: Python3
---


Here are some short posts about Python3 skills.

And maybe add them into gitbook later.


## Python __private(self)的轧压
---
'http://greybeard.iteye.com/blog/1355216'


## Publish your own Python package to PyPI
---
- Register to `https://pypi.org` and `https://test.pypi.org`
- Copy package structure in `kennethreitz/setup.py` on Github
- Don't forget `pip install twine`
- cmd
  ```shell
  python setup.py sdist
  twine upload dist/*
  ```
- Maybe you need `~/.pypirc`


## tornado
一个普通的tornado web服务器通常由四大组件组成。

    ioloop实例，它是全局的tornado事件循环，是服务器的引擎核心，示例中tornado.ioloop.IOLoop.current()就是默认的tornado ioloop实例。
    app实例，它代表着一个完成的后端app，它会挂接一个服务端套接字端口对外提供服务。一个ioloop实例里面可以有多个app实例，示例中只有1个，实际上可以允许多个，不过一般几乎不会使用多个。
    handler类，它代表着业务逻辑，我们进行服务端开发时就是编写一堆一堆的handler用来服务客户端请求。
    路由表，它将指定的url规则和handler挂接起来，形成一个路由映射表。当请求到来时，根据请求的访问url查询路由映射表来找到相应的业务handler。

    这四大组件的关系是，一个ioloop包含多个app(管理多个服务端口)，一个app包含一个路由表，一个路由表包含多个handler。ioloop是服务的引擎核心，它是发动机，负责接收和响应客户端请求，负责驱动业务handler的运行，负责服务器内部定时任务的执行。
    当一个请求到来时，ioloop读取这个请求解包成一个http请求对象，找到该套接字上对应app的路由表，通过请求对象的url查询路由表中挂接的handler，然后执行handler。handler方法执行后一般会返回一个对象，ioloop负责将对象包装成http响应对象序列化发送给客户端。
    同一个ioloop实例运行在一个单线程环境下。
