+++
title = "编译中文 LaTeX"
author = ["Samuel Garcia"]
date = 2017-09-22T09:15:00+08:00
lastmod = 2020-06-05T00:52:19+08:00
tags = ["tip", "latex"]
categories = ["research"]
draft = false
+++

之前想用中文写 LaTeX，查了几次总是忘记，在此记录。

<!--more-->

只要在文件开头加入以下代码：

```tex
% !TEX program = xelatex
\documentclass{ctexart}
```
