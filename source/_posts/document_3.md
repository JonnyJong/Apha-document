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

其中，`pc_nav_items` 中设置的组件将显示在 PC 端“顶部”的`导航栏`中；`mbl_nav_items` 中设置的组件将显示在手机端“顶部”的`导航栏`中；`side_nav_items` 中设置的组件将显示在`侧边导航栏`中。

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
{% blocktip "red" "fas fa-times" %}
这种写法将会报错，因为第 3 行和第 4 行键值名重复了；第 5 行和第 6 行的键值名也重复了。
```yml 主题配置文件
navbar:
  items:
    all, text: "hello"
    all, text: "hello"
    all, search, 0: "icon"
    all, search, 0: "input"
```
{% endblocktip %}
{% blocktip "green" "fas fa-check" %}
这种写法是正确的。
```yml 主题配置文件
navbar:
  items:
    all, text: "hello"
    all, text， 1: "hello"
    all, search, 0: "icon"
    all, search, 1: "input"
```
{% endblocktip %}

