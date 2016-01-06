title: sublime笔记
date: 2015-02-23 22:57:22
tags: [sublime]
categories:
      - 开发环境
---


使用环境：ubuntu14.04

常用快捷键：
ctrl+tab　切换标签页
ctrl+w 关闭当前标签

打开关闭VIM模式：
For Windows edition, Preferences -> Settings-User -> 注释vintage这一行，保存即可
For Linux edition, add one property in the file 'Preferences.sublime-settings': ``"ignored_packages":[]``
like:
```
{
	"ignored_packages":[]
}
```

## VIM快捷键
<kbd>w</kbd> //向后移动一个word
<kbd>b</kbd> //向前移动一个word
<kbd>G</kbd> //光标移动到最后1行
<kbd>35G</kbd> //光标移动到第35行

<kbd>A</kbd> //当前行结尾处插入文字
<kbd>I</kbd> //当前行首（非空格）处插入文字

<kbd>yy</kbd> //复制光标所在那一行
<kbd>p</kbd> //在当前行粘贴
<kbd>D</kbd> //从当前位置删除到行尾

## 常用插件
HTMLPrettify

## 自定义系统设置
菜单Preferences->Setting - User打开Preferences.sublime-settings，修改或添加内容。
1 启动时打开上次最后关闭的文件：
```
{
  "hot_exit": true,
  "remember_open_files": true
}
```

## 自定义语法设置
菜单Preferences->Setting - More->Syntax Specific - User打开JavaScript.sublime-settings，修改或添加内容。
1 设置TAB缩进长度
```
{
    "tab_size": 4,
    "translate_tabs_to_spaces": true
}
```

## 自定义快捷键
1 菜单Preferences->Browse Packages 打开 User 文件夹并创建文件close_tabs.py和copy_path_to_clipboard.py
内容见[https://github.com/mjhea0/sublime-setup-for-python/tree/master/dotfiles](https://github.com/mjhea0/sublime-setup-for-python/tree/master/dotfiles)

2 菜单Preferences->Key Bindings - User 打开Default (Linux).sublime-keymap，内容如下
```
[
  // Copy file name
  {
    "keys": ["ctrl+shift+c"],
    "command": "copy_path_to_clipboard"
  },
  // Close all other tabs
  {
    "keys": ["ctrl+alt+w"],
    "command": "close_tabs"
  }
]
```

## Linux下无法输入中文
参见：https://github.com/YoungZHU/sublime-imfix
sublime安装目录/opt/sublime_text/
创建一个shell script快速启动
```
$ vi sublime.sh
```
```
#! /bin/bash
cd /opt/sublime_text/
LD_PRELOAD=./libsublime-imfix.so ./sublime_text
```
```
$ chmod +x ./sublime.sh
```

## 安装Package Control
Ubuntu下安装完Sublime，并没有带Package Control，安装方法如下：
1.点击Preferences > Browse Packages菜单
2.进入打开的目录的上层目录，然后再进入Installed Packages/目录
3.下载[Package Control.sublime-package](https://sublime.wbond.net/Package%20Control.sublime-package)并复制到Installed Packages/目录
4.重启Sublime Text。
原文：http://www.itkubo.com/201401370.html