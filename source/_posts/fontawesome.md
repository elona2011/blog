title: Font Awesome
date: 2015-12-19 14:41:23
tags:
    - css
    - image
---

如何像文字一样使用图标？可以给图标设置大小、颜色、甚至风格么，就像文字设置字号、颜色、字体一样简单么？
答案就是Font Awesome

# 官网
http://www.bootcss.com/p/font-awesome/
http://fontawesome.io

# 原理

在使用了Font Awesome的网页上审查图标元素，看不到任何image引用，原因就是它使用了字体库

打开Font Awesome的源码
``@font-face`` 定义外部引用字体
``.fa`` 定义图标的基础样式
``.fa-lg .fa-2x .fa-4x ...`` 定义图标大小样式
{% asset_img 2.png %}

实际的图标就是在content属性通过转义的字符串引用
```
.fa-lock:before {
  content: "\f023";
}
```
{% asset_img  1.png %}

# 使用
使用就非常简单了，直接引用相应的图标class，大小class，效果class即可
```
<span><i class="fa fa-link fa-2x"></i> 链接</span>
```

# 深入阅读
http://www.verydemo.com/demo_c447_i8251.html
http://www.jb51.net/css/70033.html