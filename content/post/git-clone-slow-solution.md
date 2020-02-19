+++
title = "Git Clone 下载速度慢的解决方法"
date = 2018-04-30T20:09:00+08:00
lastmod = 2020-02-19T19:46:25+08:00
tags = ["tip", "git"]
categories = ["programming", "linux"]
draft = false
toc = false
+++

在国内 Git clone 仓库奇慢无比，通过以下配置可以提升下载速度。

```shell
git config --global http.postBuffer 524288000
```
