title: css layout
tags:
  - css
date: 2015-09-15 23:11:25
categories:
    - css
---

居中
/* Internet Explorer 10 */
display:-ms-flexbox;
-ms-flex-pack:center;
-ms-flex-align:center;

/* Firefox */
display:-moz-box;
-moz-box-pack:center;
-moz-box-align:center;

/* Safari, Opera, and Chrome */
display:-webkit-box;
-webkit-box-pack:center;
-webkit-box-align:center;

/* W3C */
display:box;
box-pack:center;
box-align:center;

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

