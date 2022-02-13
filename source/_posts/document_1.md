---
title: Apha 文档：基本操作（二）
date: 2022-02-13
updated: 2022-02-13
---
{% blocktip "blue" "fas fa-info" %}
当前文档版本为 `v0.0.3 build 3.100`
请留意所使用的 Apha 版本是否匹配。如需请查阅旧版文档。
{% endblocktip %}
{% blocktip "blue" "fas fa-info" %}
1. 所有尖括号`<>`及其内容均需要替换为所需的参数或字符串。
2. 下文`主题配置文件`即为`主题根目录`中的`_config.yml`或`根目录`中的`_config.apha.yml`；
  `Hexo 配置文件`即为`根目录`中的`_config.yml`。
{% endblocktip %}
# 文章与页面
## 创建
若要创建一篇文章，可运行以下指令。创建的文章存放在`/source/_posts/`中。
```bash
hexo new post <fileName>
```
若要创建一个页面，可运行以下指令。创建的页面存放在`/source/<fileName>/`中。
```bash
hexo new page <fileName>
```
# Front-matter
填写于文章或页面的`.md`文件开头。
## 文章
文章的 Front-matter 支持以下参数。

|参数名        |示例参数                          |作用                         |
|----------------|-------------------------------|-----------------------------|
|title|`Apha 文档：基本操作（二）`             |标题           |
|date          |`2022-02-13`、`2021-12-02 18:41:15`           |创建时间            |
| updated | 参数同上 | 更新时间 |
| description | `这是 Apha 文档的第二部分`| 描述|
| keywords | `Apha` 或 `Apha,Hexo,文档`| 关键词 |
|tags          |`- tag1`<br>`- tag2`<br>`- tag3`<br>……|标签|
| categories | `- cate1`<br>`-cate2`<br>或<br>`- [cate1, cate2]`<br>关于分类的详细信息请查看 <a href="https://hexo.io/zh-cn/docs/front-matter#%E5%88%86%E7%B1%BB%E5%92%8C%E6%A0%87%E7%AD%BE">分类和标签</a> | 分类|
|cover| `/imgs/hello.webp`或`https://jonnys.top/mainColor.png`| 封面|
| photo | `- /imgs/hello.webp`<br>`https://jonnys.top/mainColor.png` | 文章图册 |
| copyright | 关闭：`false`、开启：`true`、自定义内容：`<content>` | 版权信息 |
| lisence | 具体查看 <a>链接待补充</a> | 许可证 |
| author | `Jonny` | 作者 |
| author_link | `jonnys.top` | 作者链接 |
| origin_link | `/document_1` | 原始链接 |
| comments | 关闭：`false`、开启：`true`| 评论 |
| toc | 关闭：`false`、开启：`true`| 目录 |
| link | `jonnys.top` | 链接 |
| indexing | 关闭：`false`、开启：`true`| 被搜索 |

## 页面
页面的 Front-matter 支持以下参数。
|参数名        |示例参数                          |作用                         |
|----------------|-------------------------------|-----------------------------|
|title|`Apha 文档：基本操作（二）`             |标题           |
|date          |`2022-02-13`、`2021-12-02 18:41:15`           |创建时间            |
| layout | 具体查看下方 <a href="/document_1/#页面样式">页面样式</a> | 页面样式 |
| updated | 参数同上 | 更新时间 |
| description | `这是 Apha 文档的第二部分`| 描述|
| keywords | `Apha` 或 `Apha,Hexo,文档`| 关键词 |
|cover| `/imgs/hello.webp`或`https://jonnys.top/mainColor.png`| 封面|
| comments | 关闭：`false`、开启：`true`| 评论 |
| toc | 关闭：`false`、开启：`true`| 目录 |

### 页面样式
Apha 提供了以下页面样式：
|layout        | 说明                          |
|----------------|-------------------------------|
|category|分类页             |
|tag          |标签页           |
| link | 友情链接 |

另外，主页、归档以及具体的子分类、子标签页面由 Hexo 自动生成。