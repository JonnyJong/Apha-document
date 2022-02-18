---
title: Apha 文档：配置主题（三）
date: 2022-02-15
updated: 2022-02-18
---
{% blocktip "blue" "fas fa-info" %}
当前文档版本为 `v0.0.3 build 3.101`
请留意所使用的 Apha 版本是否匹配。如需请查阅旧版文档。
{% endblocktip %}
{% blocktip "blue" "fas fa-info" %}
1. 所有尖括号`<>`及其内容均需要替换为所需的参数或字符串。
2. 下文`主题配置文件`即为`主题根目录`中的`_config.yml`或`根目录`中的`_config.apha.yml`；
  `Hexo 配置文件`即为`根目录`中的`_config.yml`。
{% endblocktip %}
# 信息
站点的基本信息，以下是填写示例。
```yml 主题配置文件
info:
  big_title: default
  subtitle: hello world
  favicon: '/favicon.png'
  avatar: '/avatar.png'
  social_link:
    - fab fa-github, https://github.com/JonnyJong, Github
  site_begin: 2020-08-10 07:00:00
```
{% blocktip "red" "fas fa-exclamation" %}
`social_link:` 中每一项的每个参数应使用 `, ` 隔开。注意，是英文逗号加空格。
{% endblocktip %}

# 导航栏
## 添加组件
所有的组件遵循以下格式填写。
```yml 主题配置文件
navbar:
  pc_nav_items:
     <type>, <head value>, <mark>: <value>
  mbl_nav_items:
    <type>, <head value>, <mark>: <value>
  side_nav_items:
    <type>, <head value>, <mark>: <value>
```
具体可填写的数值，参考下表。
|参数名        |作用                          |
|----------------|-------------------------------|
|type          |组件类型           |
|head value          |头部参数           |
|mark          |标记           |
|value          |参数           |

其中，`pc_nav_items` 中设置的组件将显示在 PC 端的`横向导航栏`中；`mbl_nav_items` 中设置的组件将显示在手机端的`横向导航栏`中；`side_nav_items` 中设置的组件将显示在`侧边导航栏`中。

需要留意的是，Apha 是通过屏幕尺寸来区分设备的。手机的屏幕较小，应当将大多数组件放在`侧边导航栏`而不是`导航栏`中。

### type
`type 参数`用于选择不同的组件，以下是可选的组件列表。
|参数        |说明                          |
|----------------|-------------------------------|
|side_nav_btn|侧边导航栏按钮             |
|site          |站点图标、站点名           |
|img          |图片           |
|text          |文本           |
|act_statistics          |归档、归类、标签统计           |
|hr          |分割线           |
|flexbox          |弹性空间           |
|search          |搜索           |
|menu          |菜单项           |

#### side_nav_btn
用于开启`侧边导航栏`。
推荐的写法是：
```yml 主题配置文件
navbar:
  items:
    side_nav_btn:
  mbl_item_on_navbar:
    side_nav_btn:
```
这样，侧边导航栏按钮将不会在 PC 端显示，仅在手机端显示，且`侧边导航栏`中也会有一个关闭按钮。当然，也可以点击`侧边导航栏`外部区域关闭`侧边导航栏`。

#### menu
menu 类型是唯一一个需要填写 `head value 参数` 的类型。
此外，在菜单中还可以使用 hr 创建一条分割线。
以下是参数的写法。
```yml 主题配置文件
# 普通的菜单项
menu, <名称 选填>, <图标 选填>, <链接 选填>:
# 有子菜单的菜单项
menu, <名称 选填>, <图标 选填>, <链接 选填>:
  <名称 选填>: <链接 选填>, <图标 选填>
```
以下是示例的写法。
```yml 主题配置文件
# 普通的菜单项
menu, 主页, fas fa-home, /:
# 有子菜单的菜单项
menu, 文章, fa fa-graduation-cap:
  标签: /tags/, fa fa-tags
  归类: /categories/, fa fa-archive
  归档: /archives/, fa fa-folder-open
```

#### site
用于显示站点图标、站点名和提供转跳到站点主页的按钮。
有 3 个可选参数，如下。

```yml 主题配置文件
site: <图标链接>, <站点名>, <链接>
```

|图标链接 的参数        |说明                          |
|----------------|-------------------------------|
| <留空> |默认，即没有图标             |
|favicon|使用 info 中填写的 favicon             |
|avatar          |使用 info 中填写的 avatar           |
|<其他链接>          | 使用填写的链接            |

<p></p>

|站点名 的参数        |说明                          |
|----------------|-------------------------------|
| <留空> |默认，即使用 Hexo 配置文件中的 title             |
|none|没有站点名             |
|<其他字符串>          | 使用填写的字符串            |

<p></p>

|链接 的参数        |说明                          |
|----------------|-------------------------------|
| <留空> |默认，即使用 Hexo 配置文件中的 url            |
|none|没有链接             |
|<其他链接>          | 使用填写的链接            |

以下是示例。
```yml 主题配置文件
site:
site, 0: " , none, none"
site, 1: "favicon, ,  "
site, 2: avatar, Apha, /
```

#### img
创建一个可带有链接的图片组件。
有 1 个必填参数和 1 个可选参数，如下。
```yml 主题配置文件
img: <图片链接>, <链接>
```

以下是示例。
```yml 主题配置文件
img: /avatar.png
img, 0: /avatar.png, /
```

#### text
创建一个可带有链接的文本组件。
有 1 个必填参数和 1 个可选参数，如下。
```yml 主题配置文件
text: <文本>, <链接>
```

以下是示例。
```yml 主题配置文件
text: hello world!
text, 0: hello world!, /
```

#### search
创建一个用于搜索的按钮或输入框。
有 1 个必填参数，如下。
```yml 主题配置文件
# 搜索按钮
search: button
# 输入框
search, 0: input
```

#### act_statistics
用于同时显示归档、归类和标签的统计。
有 3 个可选参数，如下。
```yml 主题配置文件
act_statistics:
  # 归档页链接（默认 /archives/）
  archive:
  # 归类页链接（默认 /categories/）
  categorie:
  # 标签页链接（默认 /tags/）
  tag:
```

#### 其余无参数组件
以下组件没有参数，直接使用即可。
|type        |说明                          |
|----------------|-------------------------------|
|hr          |分割线           |
|flexbox          |弹性空间           |

### mark

`mark 参数`用于使各个键值名不重复，标记允许填写各种合法的字符，如：所有字母、数字、中文字符、英文逗号、空格、下划线。
主题中所有 `mark 参数` 均同理。
{% blocktip "red" "fas fa-times" %}
这种写法将会报错，因为第 3 行和第 4 行键值名重复了；第 5 行和第 6 行的键值名也重复了。
```yml 主题配置文件
navbar:
  items:
    text: "hello"
    text: "hello"
    search, 0: "icon"
    search, 0: "input"
```
{% endblocktip %}
{% blocktip "green" "fas fa-check" %}
这种写法是正确的。
```yml 主题配置文件
navbar:
  items:
    text: "hello"
    text， 1: "hello"
    search, 0: "icon"
    search, 1: "input"
```
{% endblocktip %}

## 配置导航栏
通过以下选项自定义导航栏。
```yml 主题配置文件
# 导航栏
navbar:
  # 不透明度（较低的背景模糊度建议使用较高的不透明度，较低的不透明度建议使用较高的背景模糊度。默认 0.8）
  opacity: ''
  # 背景模糊度（单位：px。建议不要使用过高的数值，这可能会导致卡顿。设置 0 可关闭。）
    # 一般情况下，Firefox 浏览器中 backdrop-filter 有限制
  blur: 
  # 背景饱和度（单位：%。基础值：100%。推荐随模糊度增加而增加。）
  saturate:
  # 导航栏圆角（none、default、value；无、默认、数值。建议使用 px 而不是 %，使用 % 会导致变为椭圆）
  border_radius:
```
### 横向导航栏
可通过以下选项自定义横向导航栏。
```yml 主题配置文件
# 导航栏
navbar:
  # 导航栏高度（默认 60px）
  height: 
  # 导航栏外部宽度（默认 100%）
  outer_width:
  # 导航栏外部最大宽度 （默认 100%）
  outer_max_width:
  # 导航栏内部宽度 （默认 90%）
  inner_width: 
  # 导航栏内部最大宽度 （默认为页面主体最大宽度。推荐值：100%）
  inner_max_width: 
  # 导航栏与顶部距离（top 和 bottom 建议只设置其中一个）
  top: none
  # 导航栏与底部距离
  bottom: none
  # 自动收起
  auto_folding: false

  # 元素间距（默认 0px）
  item_distance: 
  # 元素内横向间距（默认 8px）
  item_inside_distance: 

  # 二级菜单圆角（默认 6px）
  sub_menu_border_radius:
```

其中，`导航栏内部最大宽度` 

#### 在线体验
<style>
  .docShow1{
    position: absolute;
    z-index: 0;
    transition: .1s;
    left: 50%;
    transform: translate(-50%, 0);
  }
  .docShow1 .navbar_inner{
    transition: .1s;
  }
</style>
{% blocktip " " " " %}

在下方输入数值查看效果。单位：`%`、`px`、`vw`。 
在这个体验中，关于宽度的值部分可以将 `vw` 等同于 `%`。此外，拖动展示框右下角可以调整尺寸。

部分选项无法在这个体验中展示。

border_radius 导航栏圆角（none、default、value；无、默认、数值。建议使用 px 而不是 %，使用 % 会导致变为椭圆）
<input type="input" oninput="document.querySelector('.docShow1').style.borderRadius=this.value;">

height 导航栏高度（默认 60px）
<input type="input" oninput="document.querySelector('.docShow1').style.height=this.value;">

top 导航栏与顶部距离（top 和 bottom 建议只设置其中一个）
<input type="input" oninput="document.querySelector('.docShow1').style.top=this.value;">

bottom 导航栏与底部距离
<input type="input" oninput="document.querySelector('.docShow1').style.bottom=this.value;">

outer_width 导航栏外部宽度（默认 100%）
<input type="input" oninput="document.querySelector('.docShow1').style.width=this.value;">

outer_max_width 导航栏外部最大宽度（默认 100%）
<input type="input" oninput="document.querySelector('.docShow1').style.maxWidth=this.value;">

inner_width 导航栏内部宽度（默认 90%）
<input type="input" oninput="document.querySelector('.docShow1 .navbar_inner').style.width=this.value;">

inner_max_width 导航栏内部最大宽度（默认 1400px）
<input type="input" oninput="document.querySelector('.docShow1 .navbar_inner').style.maxWidth=this.value;">

<div style="border: 1px solid var(--text-color-r);margin:16px 0;resize:both;overflow:auto;max-width:100%;max-height:100vh;position:relative;min-height:60px;">
<nav class="navbar docShow1">
<div class="navbar_inner"><div class="nav_item_outer"><a class="side_nav_btn"><div class="nav_item_inner"><i class="fas fa-bars fa-fw"></i></div></a></div><div class="nav_item_outer flexbox"></div><div class="nav_item_outer site_info"><a><div class="nav_item_inner"><span class="site_title">Apha 演示</span></div></a></div><div class="nav_item_outer flexbox"></div><div class="nav_item_outer"><div class="fakeA"><div class="nav_item_inner"><i class="fa fa-search fa-fw"></i><span>搜索</span></div></div></div></div>
</nav></div>

试试下面的值。

{% blocktip_1 " " " " %}
```yml
border_radius: 14px
top: 14px
outer_width: calc(100% - 28px)
```
{% endblocktip_1 %}

{% blocktip_1 " " " " %}
```yml
border_radius: 1000px
bottom: 20px
outer_width: max-content
inner_width: max-content
```
{% endblocktip_1 %}

{% endblocktip %}

### 侧边导航栏
```yml 主题配置文件
# 导航栏
navbar:
  # 手机端菜单位置（left、right；默认 left）
  mbl_menu: 
  # 手机端菜单宽度（单位：px vw，默认自动）
  mbl_outer_width: 
  # 手机端菜单按钮高度
  mbl_item_height:
  # 手机端菜单水平内间距（默认 8px）
  mbl_horizontal_padding:
  # 手机端菜单纵向内间距（默认 10px）
  mbl_vertical_padding:
```

# 侧边栏
首先，启用侧边栏。
```yml 主题配置文件
sidebar:
  enable: true
```

侧边栏由`组件组`和`组件`组成。按照以下格式填写。
```yml 主题配置文件
sidebar:
  items:
    <page>, <device>, <mark>:
      <type>, <mark>: <value>
    sticky_items:
      <page>, <device>, <mark>:
        <type>, <mark>: <value>
```
具体可填写的数值，参考下表。
|参数名        |作用                          |
|----------------|-------------------------------|
|page          |页面限制           |
|device          |设备限制           |
|mark          |标记           |
|value          |参数           |
|type          |组件类型           |

## page、device
`page` 和 `device` 参数用于限制`组件组`能够在哪些页面和设备上显示。
需要留意的是，Apha 是通过屏幕尺寸来区分设备的。

|page 参数       |说明                          |
|----------------|-------------------------------|
|all          |在所有页面上显示           |
|index          |仅在首页显示           |
|page          |仅在非首页页面显示           |

<p></p>

|device 参数       |说明                          |
|----------------|-------------------------------|
|all          |在所有设备上显示           |
|pc          |仅 PC 端显示           |
|mbl          |仅手机端显示           |

## type
`type 参数`用于选择不同的组件，以下是可选的组件列表。
|参数        |说明                          |
|----------------|-------------------------------|
|title|特殊组件：组件组标题             |
|icon          |特殊组件：组件组标图标           |
|avatar|头像             |
|author_name          |作者名           |
|social_link          |社交链接           |
|act_statistics          |归档、归类、标签统计           |
|text          |文本           |
|toc          |目录           |
|newest_posts          |最新文章           |
|tags          |标签云           |
|categories          |归类           |
|search          |搜索           |
|button          |按钮           |
|num_of_articles          |文章数目           |
|total_word_count          |站点总字数           |
|total_visitors          |总访客数           |
|total_visits          |总访问量           |
|runtime          |运行时长           |
|last_update          |最后更新时间           |

### title、icon
`title` 和 `icon` 是两个特殊组件，没有 `mark 参数`。用于设定`组件组`的标题和图标，选填，每个组件组有且仅能有一个 `title` 和 `icon`。

以下是示例。
```yml 主题配置文件
sidebar:
  items:
    all, pc, new:
      icon: fas fa-calendar
      title: 最新文章
    all, pc, link:
      icon: fas fa-link
    all, pc, comment:
      title: 评论
    all, pc, me:
```
![示例](/imgs/doc3_0.png "左为未填写 title 和 icon，右均有填写")

### toc
这是一个目录组件，用于展示文章目录，同时还可以展示页面的目录。
建议的做法是目录作为 `sticky_items 组` 中第一个组的唯一个组件，如下。
```yml 主题配置文件
sidebar:
  items:
    all, all, others:
    sticky_items:
      all, all:
        toc:
      all, all, others:
```
`toc` 组件有 3 个可选参数，如下：
```yml 主题配置文件
toc:
  # 在文章中显示（默认 true）
  post: 
  # 在页面中显示（默认 false）
  page: 
  # 显示序号（默认 true）
  list_number: 
```
另外，不建议创建多个 `toc` 组件，只有第一个 `toc` 组件能够确保正常运行。

### newest_posts
该组件用于展示最新的文章。
该组件有 1 个可选参数，如下。
```yml 主题配置文件
newest_posts:
  # 限制数量（默认 6）
  limit: 
```

### categories
该组件用于展示归类。
该组件有 2 个可选参数，如下。
```yml 主题配置文件
categories:
  # 归类深度（默认 1）
  depth: 
  # 显示分类数量（默认 true）
  show_count:
```
### tags
该组件用于展示标签云。
该组件有个可选参数，如下。
```yml 主题配置文件
tags:
  # 限制数量（默认 30）
  limit: 
  # 多彩（默认 true）
  # 通过下方的”开始颜色“和”结束颜色“来设置变化范围，由 Hexo 随机选择颜色。
  colorful: 
  # 开始颜色（默认 #3EA919）
  start_color: 
  # 结束颜色（默认 #156FD6）
  end_color:
```

### avatar
该组件用于显示头像。
有 1 个可选参数，如下。
```yml 主题配置文件
# 方形头像
avatar, 0: 
# 圆形头像
avatar, 1: round
```

### author_name
用于显示作者名。
有 1 个可选参数，如下。
```yml 主题配置文件
author_name: <文本>
```

### act_statistics
用于同时显示归档、归类和标签的统计。
有 3 个可选参数，如下。
```yml 主题配置文件
act_statistics:
  # 归档页链接（默认 /archives/）
  archive:
  # 归类页链接（默认 /categories/）
  categorie:
  # 标签页链接（默认 /tags/）
  tag:
```

### text
一个文本组件，允许直接在其中编写 html。

```yml 主题配置文件
# 普通的文本
text: Hello World
# html
text, 0: <div style="color:var(--main-color);font-size:16px;">
  Hello world!
  允许多行，注意缩进。
  务必确保标签完整闭合！
  </div>
```

### search
创建一个用于搜索的按钮或输入框。
有 1 个必填参数，如下。
```yml 主题配置文件
# 搜索按钮
search: button
# 输入框
search, 0: input
```

### button
用于创建一个按钮。
有 1 个必填参数和 2 个可选参数，如下。
```yml 主题配置文件
button: <链接>, <文本>, <图标>
```
以下是示例。
```yml 主题配置文件
button: /
button, 0: /, home
button, 1: /, home, fa fa-home
button, 2: /, , fa fa-home
```

### 其余无参数组件
以下组件没有参数，直接使用即可。
|type        |说明                          |
|----------------|-------------------------------|
|num_of_articles          |文章数目           |
|total_word_count          |站点总字数           |
|total_visitors          |总访客数           |
|total_visits          |总访问量           |
|runtime          |运行时长           |
|last_update          |最后更新时间           |
|social_link          |社交链接           |

## sticky_items
`sticky_items` 是一个特殊的组件组，至多只能创建一个并且必须是`最后一个`组件组。
不能直接在这个组件组内创建组件，而需要创建普通的组件组，再在普通的组件组内创建组件。
{% blocktip "red" "fas fa-times" %}
这种写法不会报错，但会导致排版错误。因为 `sticky_items` 没有被放到最后。
```yml 主题配置文件
sidebar:
  items:
    sticky_items:
      all, all:
        title: Apha
    all, all:
      title: Apha
```
{% endblocktip %}
{% blocktip "red" "fas fa-times" %}
这种写法不会报错，但会导致排版错误。因为 `sticky_items` 存在多个。
```yml 主题配置文件
sidebar:
  items:
    all, all:
      title: Apha
    sticky_items:
      all, all:
        title: Apha
    sticky_items, 1:
      all, all:
        title: Apha
```
{% endblocktip %}
{% blocktip "green" "fas fa-check" %}
这种写法是正确的。
```yml 主题配置文件
sidebar:
  items:
    all, all:
      title: Apha
    sticky_items:
      all, all:
        title: Apha
```
{% endblocktip %}