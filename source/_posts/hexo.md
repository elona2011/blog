title: 使用hexo布置blog
date: 2014-11-08 17:53:31
tags: 
    - hexo
categories:
      - blog
---


# 命令行

``npm install hexo-cli -g`` 安装
``hexo new [post/draft/page] <title>`` 生成[发布/草稿/页面]文档
``hexo s`` 启动服务预览，并监视文件自动更新
``hexo publish <title>`` 草稿转为公开文章
``hexo d`` === ``hexo deploy`` 自动发布
``hexo d -g`` === ``hexo g -d`` 生成并发布

# tags
``tags: [js, jq]`` 文章头部的tags写法

# 图片引用
1 将_config.yml文件中的post_asset_folder设为true，此后用hexo new创建的文件都会有一个同名文件夹
```
post_asset_folder: true   //_config.yml
```
2 将被引图片放在同名文件夹中，通过以下语法引用
```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}

{% asset_img example.jpg This is an example image %}
```


# deploy

可以使用HTTPS和SSH两种方式。SSH可以免去deploy时输入密码
使用HTTPS deploy方法后（ https://hexo.io/docs/deployment.html ），windows下可能会报错：

```
bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error
    at ChildProcess.<anonymous> (E:\blog\blog\node_modules\hexo-deployer-git\node_modules\hexo-util\lib\spawn.js:42:17)
    at emitTwo (events.js:87:13)
    at ChildProcess.emit (events.js:172:7)
    at maybeClose (internal/child_process.js:818:16)
    at Process.ChildProcess._handle.onexit (internal/child_process.js:211:5)
```

解决方法：
1.设置SSH KEY
2._config.yml文件的repo修改为SSH URL
```
deploy:
  type: git
  repo: git@github.com:elona2011/elona2011.github.io.git
  branch: master
```

参考：
[https://help.github.com/articles/generating-ssh-keys/](https://help.github.com/articles/generating-ssh-keys/)
[https://help.github.com/articles/using-ssh-over-the-https-port/](https://help.github.com/articles/using-ssh-over-the-https-port/)
[http://www.yczmm.com/hexo-deploy%E6%8A%A5%E9%94%99%E8%A7%A3%E5%86%B3.html](http://www.yczmm.com/hexo-deploy%E6%8A%A5%E9%94%99%E8%A7%A3%E5%86%B3.html)
[http://eesly.github.io/2014/10/26/%E5%88%A9%E7%94%A8ssh%E7%9C%81%E5%8E%BB%E5%9C%A8hexo-deploy%E8%BE%93%E5%85%A5%E5%AF%86%E7%A0%81/](http://eesly.github.io/2014/10/26/%E5%88%A9%E7%94%A8ssh%E7%9C%81%E5%8E%BB%E5%9C%A8hexo-deploy%E8%BE%93%E5%85%A5%E5%AF%86%E7%A0%81/)

# Next主题

``layout/_partials/header.swig`` 头部模板, 可以修改结构和样式
_config.yml 可设置菜单的FontAwesome图标

``source/css/_variables/base.styl`` 基础样式
``$font-size-base           = 20px`` 基础字体大小
