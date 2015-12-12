title: Linux命令及Ubuntu
tags:
  - linux
  - backend
date: 2015-03-02 22:21:45
categories:
      - 后端
---

# 快捷键
``Ctrl+Alt+t`` 弹出终端
``Ctrl+t`` 新建标签页
``Ctrl+w`` 关闭当前标签页
``Ctrl+Tab`` 往右切换一个标签页

# 文件
``ln -s /media/nari/`` #在当前文件夹创建软链接到/media/nari/

``du -sh .`` 当前目录总大小(包括子目录)
``du -h -d 1 --all`` 当前目录下的所有目录和文件的大小
``du -sh .[^.]*`` 当前目录下的所有隐藏目录和文件的大小
``df -h`` 显示挂载的所有文件系统的用量

``rm -rf`` 删除目录和文件及子目录和子文件(小心操作)

``mount /dev/cdrom /mnt`` 挂载光驱到/mnt

# 关机
``shutdown -h 10`` 十分钟后关机 
``shutdown -h 23:30`` 下一个23：30关机 
``shutdown -h now`` 立即关机 
``reboot`` 重启

# 系统版本
``cat /etc/redhat-release`` Redhat/CentOS Linux release

# flash插件
chromium安装及flash插件安装, 需使用Pepper Flash Player, Adobe Flash Player无法使用
```
sudo apt-get update
sudo apt-get install chromium-browser
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```

# 安装jekyll

安装ruby
```
sudo apt-get install ruby
```

修改ruby源 
```
gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/ gem sources -l 
```

在ubuntu15.10下安装还需要安装下两步
``` 
sudo apt-get install ruby-dev 
sudo apt-get install zlib1g-dev 
```

然后就可以安装了 
```
sudo gem install github-pages sudo gem install jekyll
```
