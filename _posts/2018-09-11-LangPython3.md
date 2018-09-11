---
layout: post
title: Python3
---


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
