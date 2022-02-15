---
title: Apha 文档：页面（二）
date: 2022-02-13
updated: 2022-02-15
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
# 归档、分类、标签页
归档页面 [/archives/](/archives/) 是由 Hexo 自动生成的，Apha 允许通过以下选项自定义归档页面。

```yml 主题配置文件
# 归档
archive:
  # 归档页展示（你可以将归档、归类、标签全部集中到这个页面来显示，你可以自定义展示顺序，最少需要展示一项）
  show:
    - archive
    - tag
    - category
  # 显示数量
  show_count: false
  # 显示总数
  show_total: false
  # 按月份
  monthly: false
  # 日期格式（默认：YYYY MMMM）
  format:
  # 封面图
  cover: 
```
{% fold 效果演示 %}
![cover: /img.webp](/imgs/doc2_0.png "cover: /img.webp")
![没有配置 cover](/imgs/doc2_1.png "没有配置 cover")
{% endfold %}

如果要将归类和标签在不同的页面显示，需要先创建页面：
```bash
hexo new page <fileName>
```
然后修改相应页面的 Front-matter：
```markdown /source/tags/index.md
---
layout: tag
---
```
```markdown /source/categories/index.md
---
layout: category
---
```
通过修改`主题配置文件`来修改这两个页面。
```yml 主题配置文件
# 分类
category:
  # 显示数量
  show_count: false
  # 显示总数
  show_total: false
  # 将内容渲染到分类之后
  after_content: true
# 标签
tag:
  # 显示数量
  show_count: false
  # 显示总数
  show_total: false
  # 将内容渲染到标签之后
  after_content: true
```

{% fold 效果演示 %}
![after_content: true](/imgs/doc2_2.png "after_content: true")
![after_content: false](/imgs/doc2_3.png "after_content: false")
{% endfold %}

# 友情链接页
首先创建一个页面，然后修改其 Front-matter：
```markdown /source/link/index.md
---
layout: link
---
```
接着，在 `/source/` 中找到或创建 `_data` 文件夹。改文件夹用于存放数据文件。
然后在 `_data` 文件夹中创建 `link.yml` 文件用于存放友情链接。格式如下：
```yml /source/_data/link.yml
- group: <组名称\标题 选填>
  description: <组描述\副标题 选填>
  color: <标题颜色 选填>
  icon: <标题图标 选填>
  icon_color: <图标颜色 选填>
  links:
    - name: <名字 必填>
      link: <链接 必填>
      avatar: <头像链接 选填>
      description: <描述 选填>
      color: <颜色 选填>
```
{% fold 效果演示 %}
```yml /source/_data/link.yml
```
[示例](/link/)
{% endfold %}