---
title: Org mode导出中文PDF
categories:
  - Tips
tags:
  - LaTeX
abbrlink: 1a927102
date: 2019-01-29 01:32:32
---

只要在文件开头加入以下代码：

```org
#+LATEX_COMPILER: xelatex
#+LATEX_HEADER: \usepackage{xeCJK}
```
