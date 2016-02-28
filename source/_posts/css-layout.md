title: css layout
tags:
  - css
date: 2015-09-15 23:11:25
categories:
    - css
---


内外div居中
.btv_icon_text_outside{
	height: 120px;
	width: 150px;
	float: left;
}

.btv_icon_text_inside{
	left:30%;
	top: 20%;
	height: 90px;
	width: 90px;
	float: left;
	position: relative;
}

底部居中
.btvinfobar{
	height: 34%;
    width: 100%;
    top: 66%;
    position: absolute;
}

内外DIV
.btvinfobar_outside{
	height: 34%;
    width: 100%;
    top: 66%;
    position: absolute;
}

.btvinfobar_inside{
    top: 30%;
    width: 100%;
    position: absolute;
    left: 20%;
}

border
border-style: solid;
border-width: 3px;
border-color: #313638;
border-radius: 15px; //圆角

font字体大小及居中
font: -webkit-control;
font-size: x-large;
text-align: center;
line-height: 200%;

文字单行省略
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;

overflow: hidden; //隐藏超出范围
box-shadow: 0px 0px 30px 6px #1a2123; //阴影
background-color: rgba(26, 33, 34, 0.8);
background-image: url("/assets/images/04LiveTV/arrow_down.png"); //url从./或../或/开始
background-size: 20px 12px; //背景的拉伸
background-repeat: no-repeat;

<<<<<<< HEAD
渐隐效果
-webkit-mask-image: -webkit-gradient(linear, 640 0, 770 0, from(#000000), to(rgba(0, 0, 0, 0)));

=======
>>>>>>> bed7b8dc1855a68fd337e1e0733c839809d00117

css文件里可以引用其它css文件:
@import url(my.css);

请详细观看盒子模型的立体图片，从第一层到第五层依次为：border、content+padding、background-image、background-color、margin。