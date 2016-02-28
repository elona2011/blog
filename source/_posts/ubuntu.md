title: Linux命令及Ubuntu
tags:
  - ubuntu
date: 2015-03-02 22:21:45

---

# 快捷键
``Ctrl+Alt+t`` 弹出终端
``Ctrl+t`` 新建标签页
``Ctrl+w`` 关闭当前标签页
``Ctrl+Tab`` 往右切换一个标签页

## launcher自定义sh
```
sudo -i gedit /usr/share/applications/name.desktop

[Desktop Entry]
Type=Application
Terminal=true
Name=unmount-mount
Icon=/path/to/icon/icon.svg
Exec=/path/to/file/mount-unmount.sh
```
保存后将新创建的图标拖到launcher上


# 文件
``ln -s /media/nari/`` #在当前文件夹创建软链接到/media/nari/

``du -sh .`` 当前目录总大小(包括子目录)
``du -h -d 1 --all`` 当前目录下的所有目录和文件的大小
``du -sh .[^.]*`` 当前目录下的所有隐藏目录和文件的大小
``df -h`` 显示挂载的所有文件系统的用量

``rm -rf`` 删除目录和文件及子目录和子文件(小心操作)

``mount /dev/cdrom /mnt`` 挂载光驱到/mnt
``sudo mount /dev/sdb1 /media/work`` 挂载sdb1分区
``umount /dev/sdb1`` 卸载分区，已挂载的分区在/etc/mtab文件中

开机自动挂载分区
```
$ sudo fdisk -l  #查看分区
...
设备       启动      Start     末尾     扇区   Size Id 类型
/dev/sdb1  *            63  629153594  629153532   300G  7 HPFS/NTFS/exFAT
/dev/sdb2        629153656 1953523711 1324370056 631.5G  f W95 扩展 (LBA)
/dev/sdb5        629153658 1564775696  935622039 446.1G  7 HPFS/NTFS/exFAT
/dev/sdb6       1564776448 1936959487  372183040 177.5G 83 Linux
/dev/sdb7       1936961536 1953523711   16562176   7.9G 82 Linux 交换 / Solaris
...

$ sudo gedit /etc/fstab
... #在文件尾部添加，可以man fstab查看参数定义
/dev/sdb1 /media/work ntfs defaults 0 0    
```

## 文件的颜色
蓝色表示目录；绿色表示可执行文件；红色表示压缩文件；浅蓝色表示链接文件；白色表示其他文件；黄色是设备文件

# 网络
## iftop
查看实时网络流量 interface top
``sudo apt-get install iftop`` 安装iftop 

# 关机
``sudo shutdown -h 10`` 十分钟后关机
``sudo shutdown -h 23:30`` 下一个23：30关机 
``shutdown -h now`` 立即关机 不要sudo
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