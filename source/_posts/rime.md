title: 中州韵输入法Rime
date: 2015-12-19 00:01:34
tags:
    - ubuntu
---

官方网站：http://rime.im/
网上评价颇高，实际使用确实不错。特别是高度可定制的[输入方案](https://github.com/rime/home/wiki/RimeWithSchemata)，可以定制独一无二的输入法。

# Rime五笔86输入法安装
1 ubuntu软件中心直接搜索安装
2 将五笔86的方案文件复制到 Rime 用户文件夹中
```
$sudo cp /usr/share/rime-data/wubi86.schema.yaml ~/.config/fcitx/rime
```
3 打开 Rime 用户文件夹中的 default.yaml 文件
``~/.config/fcitx/rime/default.yaml``
在 schema_list 尾部添加一行 “- schema: wubi86″，保存退出
{% asset_img rime_default_yaml.png default.yaml %}
4 重新部署启动一下rime. 就可以在方案菜单（按 F4 或 Ctrl+`）中选择五笔86了

另一篇介绍Rime: http://www.barretlee.com/blog/2015/11/20/new-input-methed-rime/