---
title: Apha 文档：配置主题（三）
date: 2022-02-15
updated: 2022-02-15
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

#### site、img、text、act_statistics、hr、flexbox、search
以下是各个类型参数的写法。
```yml 主题配置文件
navbar:
  items:
    site: <图片链接 选填：链接 / favicon 即 info 中填写的 favicon 路径 / avatar 即 info 中填写的 avatar 路径>, <站点名 默认为 Hexo 配置文件中的 title 允许替换为其他合法的字符串，当为 none 时没有字符串>, <链接 默认为 Hexo 配置文件中的 url，当为 none 时没有链接>
    img: <图片链接>, <链接 选填>
    text: <文本>, <链接 选填>
    act_statistics:
      archive: <归档页面的链接 选填 默认为“/archives/”>
      categorie: <分类页面的链接 选填 默认为“/categories/”>
      tag: <标签页面的链接 选填 默认为“/tags/”>
    hr:
    flexbox:
    search: <类型 选填：icon 按钮 / input 输入框>
```
以下是示例的写法。
```yml 主题配置文件
navbar:
  items:
    site: 
    img: /favicon.png
    text: ヾ(≧▽≦*)o
    act_statistics:
      categorie: /categories/
      tag: /tags/
    hr:
    flexbox:
    search: icon
```

#### menu
menu 类型是唯一一个需要填写 `head value 参数` 的类型。
以下是参数的写法。
```yml 主题配置文件
navbar:
  items:
    # 普通的菜单项
    menu, <名称 选填>, <图标 选填>, <链接 选填>:
    # 有子菜单的菜单项
    menu, <名称 选填>, <图标 选填>, <链接 选填>:
      <名称 选填>: <链接 选填>, <图标 选填>
      hr:
```
以下是示例的写法。
```yml 主题配置文件
navbar:
  items:
    # 普通的菜单项
    menu, 主页, fas fa-home, /:
    # 有子菜单的菜单项
    menu, 文章, fa fa-graduation-cap:
      标签: /tags/, fa fa-tags
      归类: /categories/, fa fa-archive
      归档: /archives/, fa fa-folder-open
```

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