---
title: Apha 文档：开始（零）
date: 2022-02-13
updated: 2022-02-15
sticky: 100
---
{% blocktip "blue" "fas fa-info" %}
当前文档版本为 `v0.0.3 build 3.100`
请留意所使用的 Apha 版本是否匹配。如需请查阅旧版文档。
{% endblocktip %}
{% blocktip "blue" "fas fa-info" %}
所有尖括号`<>`及其内容均需要替换为所需的参数或字符串。例：
```bash
# 文档提供的
hexo init <folder>
# 使用
hexo init myBolgFolderName
```
{% endblocktip %}
# 环境准备
## Hexo
根据 Hexo 官方文档安装和准备好 Hexo。
https://hexo.io/zh-cn/docs/setup

```bash
hexo init <folder>
```

此外，可能还会需要`hexo-deployer-git`。
```bash
npm i hexo-deployer-git --save
```

## 渲染插件
Apha 还需要安装`hexo-renderer-pug`和`hexo-renderer-stylus`才能够正常运行。
```bash
npm i hexo-renderer-pug --save
npm i hexo-renderer-stylus --save
```

## 可选插件
如需，还需要安装`hexo-wordcount`用于统计字数。
```bash
npm i hexo-wordcount --save
```

# 安装 Apha
提供了以下三种方式安装，按需选择。
{% blocktip "blue" "fas fa-info" %}
当前 Apha 处于 aplha 阶段，因此建议使用` Github（dev 渠道）`。
{% endblocktip %}
{% tabs %}
,,npm（当前为 alpha 阶段，后续将保持为正式版）,,
```bash
npm i hexo-theme-apha --save
```
,,Github（main 渠道，与 npm 同步）,,
```bash
git clone -b main https://github.com/JonnyJong/hexo-theme-apha.git themes/apha
```
,,Github（dev 渠道，最新但可能有 bug）,,
```bash
git clone -b dev https://github.com/JonnyJong/hexo-theme-apha.git themes/apha
```
{% endtabs %}

然后在`根目录`的`_config.yml`中修改：
```yml /_config.yml
theme: apha
```

然后运行以下指令检查是否正常。若出现修改后刷新浏览器未发生变化，也请尝试运行以下指令。
```bash
hexo clean
hexo s
```

# 配置 Apha
不建议通过修改`主题根目录`中的`_config.yml`来配置 Apha。且怎么做也不便于后续升级。
将`主题根目录`中的`_config.yml`复制到`根目录`并重命名为`_config.apha.yml`。

然后你可以将配置填写到`_config.apha.yml`中，`_config.apha.yml`会与`主题根目录`中的`_config.yml`自动合并，`_config.apha.yml`的优先级高于`主题根目录`中的`_config.yml`。

# 升级 Apha
根据安装主题的方式，分别选择以下方式更新。
{% tabs %}
,,npm,,
```bash
npm update hexo-theme-apha --save
```
,,Github（main 渠道）,,
```bash
cd ./themes/apha
git pull
```
,,Github（dev 渠道）,,
```bash
cd ./themes/apha
git pull
```
{% endtabs %}