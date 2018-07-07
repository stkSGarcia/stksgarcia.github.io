---
title: 从Jekyll到Hexo
categories:
  - Misc
tags:
  - Blog
abbrlink: a3785f97
date: 2018-03-02 00:20:42
---


我之前一个版本的博客也是托管在GitHub的静态博客，使用的是[Jekyll](https://www.jekyll.com.cn/)。但是它提供的主题不是很符合我的口味，所以就去网上找了许多模板，最终使用了Hux的模板（[主页](http://huangxuan.me/) | [项目](https://github.com/Huxpro/huxpro.github.io)）。虽然样式挺美观且简洁，但是可扩展性不强，更新起来麻烦。如果要使用的话需要自己改很多文件。于是最终放弃了Jekyll转到了Hexo阵营。

Hexo是基于Node.js的博客框架，在Windows下只需要安装Node.js就可以写博客了，而不像Jekyll需要安装Ruby和其他依赖，另外Ruby对Windows也不友好。Hexo的开源贡献者有一大部分是国人，所以有中文文档（文档写的有点简略啊）。最主要的是[Next主题](http://theme-next.iissnan.com/)好看，容易配置和更新。

<!-- more -->

# 写作

Hexo和Jekyll都是使用Markdown进行写作的，但是Hexo有一些特殊的语法，详细请参考[Hexo官方文档](https://hexo.io/zh-cn/docs/)。

## 引用块

在文章中插入引言，可包含作者、来源和标题。

**别名:** quote

```
{% blockquote [author[, source]] [link] [source_link_title] %}
content
{% endblockquote %}
```

**样例**

```
{% quote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endquote %}
```

{% quote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endquote %}

## 代码块

在文章中插入代码。

**别名:** code

```
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```

**样例**

```
{% code _.compact lang:javascript http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcode %}
```

{% code _.compact lang:javascript http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcode %}

另一种形式的代码块，不同的是它使用三个反引号来包裹。

\`\`\` [language] [title] [url] [link text] code snippet \`\`\`

## Image

在文章中插入指定大小的图片。

```
{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```

## Link

在文章中插入链接，并自动给外部链接添加 target="_blank" 属性。

```
{% link text url [external] [title] %}

```

## 引用文章

引用其他文章的链接。

```
{% post_path slug %}
{% post_link slug [title] %}

```

## 引用资源

引用文章的资源。

```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```
