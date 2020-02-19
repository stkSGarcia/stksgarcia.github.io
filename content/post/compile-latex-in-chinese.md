+++
title = "编译中文 LaTeX"
date = 2017-09-22T09:15:00+08:00
lastmod = 2020-02-19T19:46:27+08:00
tags = ["tip", "latex"]
categories = ["research"]
draft = false
toc = false
+++

之前想用中文写 LaTeX，查了几次总是忘记，在此记录。

<!--more-->

只要在文件开头加入以下代码：

```latex
% !TEX program = xelatex
\documentclass{ctexart}
```
