title: VPS上搭建简易Blog
date: 2015-01-09 18:00:30
tags:
    - vps
    - blog
---

# VPS

网上推荐的VPS主要有三款：[Linode](https://www.linode.com), [DigitalOcean](https://www.digitalocean.com), [Bandwagon](https://bandwagonhost.com)
我先开的DigitalOcean，大概一个月30元。后来看到Bandwagon太便宜了，一年只要60多，忍不住也开了。两个VPS都是最低配，5G硬盘，512RAM，带宽流量肯定用不完，用来搭一个简单的BLOG足够了。实测速度两者也几乎一样，之后使用过程中感觉Bandwagon还更稳定一些。

# 系统安装

Bandwagon使用默认的Centos 6 x86，DigitalOcean使用CentOS 6.5 x64

以下以Bandwagon为例：
修改root密码
{% asset_img 1.png  %}

# LNMP安装
[LNMP一键安装包](http://lnmp.org/install.html)

# Blog系统
我个人使用的是hexo静态博客系统，优点是简单方便，将生成的public文件夹下的内容全部上传到VPS的/home/wwwroot/default/目录下即可。
具体一些使用方法可参考：[使用hexo布置blog](/2015/01/08/hexo/)

# 远程连接
ubuntu下使用ssh命令和scp命令，ssh用于远程控制VPS，scp远程拷贝文件
```
$ ssh -p 12345 123.123.123.123  #12345是端口号
$ scp -r -P 12345 * username@123.123.123.123:/home/wwwroot/default/
```

windows下可使用putty，ftp等工具

# 域名绑定

域名解析里绑定VPS的IP
{% asset_img 2.png  %}

这时可能会出现用IP可以访问，但是用域名却出现403 forbidden，原因主要是nginx.conf没配置好
```
$ nginx -t  #显示nginx.conf路径
$ vi /usr/local/nginx/conf/nginx.conf
```

所有绑定的www开头和无www开头的域名都要在server_name后设置
{% asset_img 3.png  %}