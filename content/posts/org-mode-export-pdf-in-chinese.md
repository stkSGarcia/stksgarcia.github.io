+++
title = "Org mode 导出中文 PDF"
author = ["Samuel Garcia"]
date = 2019-01-29T01:32:00+08:00
lastmod = 2020-06-05T00:52:20+08:00
tags = ["org-mode", "latex", "emacs"]
categories = ["emacs"]
draft = false
+++

只要在文件开头加入以下代码

<!--more-->

```org
#+LATEX_COMPILER: xelatex
#+LATEX_HEADER: \usepackage{xeCJK}
```
