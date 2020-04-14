---
title: Hexo设置网站链接格式
date: 2020-04-14 20:59:54
id: doc2
tags:
  - Hexo
  - 链接
categories:
  - Hexo
description: 更改Hexo部署后的文章链接格式
cover: https://s1.ax1x.com/2020/04/14/Jpr0ld.jpg
top_img: https://s1.ax1x.com/2020/04/14/JpNgBD.jpg
---


Hexo默认状态下自动生成的文章链接会将中文汉字编码改变，导致网页链接很常且不美观。

类似如下链接`https://yang66995.cn/2020/02/25/PDF%E8%BD%AC%E5%9B%BE%E7%89%87/`。

Hexo可以将链接设置成固定格式的永久链接.

类似如下`https://yang66995.cn/posts/20200225doc1.html`

------

首先在项目的Hexo配置文件中找到根目录下的`_config.yml`,找到`permalink:`，设置为如下：

```yml
permalink: posts/:year:month:day:id.html
```

其中的变量的顺序就是生成网页后的网页链接顺序，变量可以自行替换，变量说明如下表格：

|   **变 量**   |           **描 述**            |
| :-----------: | :----------------------------: |
|    `:year`    |    文章的发表年份（4 位数）    |
|   `:month`    |    文章的发表月份（2 位数）    |
|  `:i_month`   | 文章的发表月份（去掉开头的零） |
|    `:day`     |    文章的发表日期 (2 位数)     |
|   `:i_day`    | 文章的发表日期（去掉开头的零） |
|    `:hour`    |   文章发表时的小时 (2 位数)    |
|   `:minute`   |   文章发表时的分钟 (2 位数)    |
|   `:title`    |            文件名称            |
| `:post_title` |            文章标题            |
|     `:id`     |            文章 ID             |
|  `:category`  |              分类              |

添加`id:`属性

在项目文件路径中找到`…\scaffolds\post.md`,添加一个`id:`属性，例如`id: doc1`，后续每次新增文章都会在文章开头自动添加id值，也可留空，生成文章后手动添加。

```yml
---
title: {{ title }}
date: {{ date }}
id: doc1
tags:
categories:
cover:
top_img:
---
```
此时重新渲染生成网页，网页链接就会变成类似如下`https://yang66995.cn/posts/20200225doc1.html`格式。

`posts/20200225doc1.html`对应`posts/:year:month:day:id.html`

类似的还可以自行设计如下，可以对参数进行随意组合

|           **参数**           |       **效果**       |
| :--------------------------: | :------------------: |
| `:year/:month/:day/:id.html` | 2020/02/25/doc1.html |
| `:year-:month-:day-:id.html` | 2020-02-25-doc1.html |
|   `:month:day:title.html`    |  0225PDF转图片.html  |

{% note info %}
如果使用上述的日期加`id:`的生成方式，当同一天有多篇文章时，需要将每篇文章的`id:`值改成不同的。
{% endnote %}
