---
title: Windows下使用Powershell批量重命名文件
categories:
  - Tips
tags:
  - Windows
  - Powershell
  - Tips
abbrlink: ee56f706
date: 2018-03-18 18:47:16
---

当我们下载了一部电视剧或是动漫时，通常文件名非常长，会包含视频的分辨率、字幕组等信息，但是我们通常只会关心这是第几集。。。

于是就开始寻找Windows下批量重命名的方法。虽然Windows下的命令行没有Linux下方便，但是还是提供了必备的功能。

以下就是通过Powershell实现批量正则重命名文件。

```shell
Get-ChildItem *.mp4 | Rename-Item -NewName { $_.name -replace '.*Vol\.([0-9]{1}).*', 'Video_$1.mp4' }
```

其中管道前是列出所有mp4文件。`Rename-Item`的一般形式是`Rename-Item -Path <String> -NewName <String>`。大括号内是通过正则替换字符串。

另外`Get-ChildItem`的别名是`ls`，`Rename-Item`的别名是`rni`。
