---
title: Linux下清空Page cache
categories:
  - Coding
  - Linux
tags:
  - Linux
abbrlink: 87ebabf0
date: 2018-11-08 00:19:49
---


```shell
sync; echo 1 > /proc/sys/vm/drop_caches
```

<!-- more -->

**sync命令:**

Linux sync命令用于数据同步，sync命令是在关闭Linux系统时使用的。

Linux系统中欲写入硬盘的资料有的时候会了效率起见，会写到filesystem buffer中，这个buffer是一块记忆体空间，如果欲写入硬盘的资料存于此buffer 中，而系统又突然断电的话，那么资料就会流失了，sync指令会将存于buffer中的资料强制写入硬盘中。

**/proc/sys/vm/drop_caches:**

- To free pagecache, use:

  `echo 1 > /proc/sys/vm/drop_caches`

- To free dentries and inodes, use:

  `echo 2 > /proc/sys/vm/drop_caches`

- To free pagecache, dentries and inodes, use:

  `echo 3 >/proc/sys/vm/drop_caches`
