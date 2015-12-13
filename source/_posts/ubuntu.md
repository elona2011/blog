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

# java安装
先从Oracle官网下载JDK
装JDK解压至``/usr/lib/jvm``
配置环境变量命令
```
$sudo gedit ~/.bashrc
添加以下代码：
export JAVA_HOME=/usr/lib/jvm/jdk1.7.0_79   
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH

激活配置
source ~/.bashrc

测试
java -version
javac -version
```

# android环境安装
下载Android Studio
解压后进入android-studio/bin/
运行./studio.sh

报错:
```
Failed to get the adb version: Cannot run program "adb": error=2, 没有那个文件或目录
```
原因:由于是64bit的系统，而Android sdk只有32bit的程序，需要安装lib32
```
sudo apt-get install lib32z1
sudo apt-get install lib32stdc++6
```
此外, 编译报错时还要安装SDK Tools里的Android Support Repository

# jekyll安装

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

# 资料搜索方法
https://github.com/getlantern/lantern
https://github.com/hawx1993/accessing-Google