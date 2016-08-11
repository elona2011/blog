title: ubuntu下玩dota2
date: 2016-01-10 00:19:01
tags:
    - ubuntu
---

1122334455非常爽，原以为这么流行的游戏肯定不会原生支持Linux，结果居然支持，效果还很好，很流畅。下面说一下安装和设置的方法：
终端下运行：
```
$ wget http://media.steampowered.com/client/installer/steam.deb
$ sudo apt-get install gdebi-core
$ sudo gdebi steam.deb      #安装steam
$ sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386     #安装依赖包
```

安装完成后桌面会有steam图标，国服的账号就可以登陆，随后下载DOTA2。steam中还有很多别的游戏，很多都支持三平台（windows, Mac, Linux），有很多经典，自己研究吧。

下载好是这样的，英文版本，在游戏设置中调成全屏显示就可以游戏啦！
{% asset_img 004.png  %}

# 鼠标设置
ubuntu默认的鼠标移动速度对我来说有点快，会出现游戏中，特别是激战中找不到鼠标指针的情况。
DOTA2游戏设置无法调整鼠标移动速度，需要在系统设置里改。ubuntu15.10系统似乎没有鼠标移动速度的设置，在软件中心搜索鼠标，安装”键盘和鼠标“这个工具，可以调整鼠标移动速度。
{% asset_img 003.png  %}

# 国服设置
在Dota2游戏属性里添加``-perfectworld``
{% asset_img 005.png  %}
