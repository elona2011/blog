date: 2015-08-30 21:53:12
title: nodejs笔记
tags: [node, js]
---

## nvm

install nvm:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```
nvm的安装后，运行node程序可能会导致如下错误
```
/usr/bin/env: node: 没有那个文件或目录
```

临时使用：
1 ``nvm ls``查看当前使用版本
2 如果没有绿色箭头指向某个版本，则``nvm use 0.12``
长久解决:
``$ nvm alias default 0.12``
from: [https://github.com/alsotang/node-lessons/tree/master/lesson0](https://github.com/alsotang/node-lessons/tree/master/lesson0)

## npm源

``npm config set registry http://registry.cnpmjs.org`` 国内源
``npm config set registry "http://registry.npmjs.org/"`` 官方源

如果卡顿，可尝试关闭https npm config set strict-ssl false

## cnpm

 1.安装cnpm工具 npm install -g cnpm --registry=http://r.cnpmjs.org 或npm install -g cnpm --registry=http://registry.npm.taobao.org 
 2.使用cnpm安装模块 cnpm install xxx 原文：http://segmentfault.com/a/1190000000471219

```
npm install microtime --registry=http://r.cnpmjs.org --disturl=http://dist.cnpmjs.org
```

grunt-cli会执行当前目录中package.json文件指定的grunt版本，来读取当前目录下的gruntfile的配置文件，然后按其中的配置项来执行自动化。 之所以这样是为了多个grunt版本并存，来支持新老项目。
