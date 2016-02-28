title: CSS & DOM 笔记
tags: css
date: 2015-05-03 19:22:57
categories:
    - css
---

# selectors
http://www.w3.org/TR/selectors/#selectors

.style.cssText 元素的style属性值,直接.style是一个对象

色值三位#abc 转为6位#aabbcc 三位色值在CSS中可使用

# inline-block
inline-block元素间，换行或有空格，会显示出一个空格的间距，实际页面就是显示了一个空格
将非inline-block元素设置css(display: inline-block;)，也会产生该效果。
该问题常出现在DIV元素设置为inline-block
两种解决方法:
方法1. 将DIV元素写成一行,中间不要换行
方法2. 或者在父元素上设置font-size:0

# animation
```
#RecmWidget_img1{
        left: 0px;
        animation-delay: 1s;
        animation-duration: 4.5s;
        animation-iteration-count: infinite;
        animation-name: slideImage1;
    }

@keyframes slideImage1 {
  0% { left: 0; opacity:1;z-index:0; }
  11% { left: -272px;opacity:1;z-index:0; }
  12% { left: -272px; opacity:0; z-index:-1; }
  13% { left: 272px; opacity:0; z-index:-1; }
  14% { left: 272px; opacity:1; z-index:0; }
  33% {left: 272px; opacity:1; z-index:0;}
  44% {left: 272px; opacity:1; z-index:0;}
  66% {left: 272px; opacity:1; z-index:0;}
  77% { left: 0px; opacity:1; z-index:0; }
  100% { left: 0px; opacity:1; z-index:0; }
}
```

# css权重
1.多个选择器可能会选择同一个元素，有3个规则，从上到下重要性降低： 
    !important的用户样式 
    !important的作者样式 
    作者样式 
    用户样式 
    浏览器定义的样式 

2.CSS规范为不同类型的选择器定义了特殊性权重，特殊性权重越高，样式会被优先应用。 
权重设定如下： 
html选择器，权重为1； 
类选择器，权重为10； 
id选择器，权重为100； 
这里还有一种情况：在html标签中直接使用style属性，这里的style属性的权重为1000； 
即如下情况： 

```
#x34y {color:red} 
<p id=x34y style="color:green">  优先选择style=""设定的样式。 
```

例子： 

```
h1{color:blue}  权重为1 
p  em{color:yellow}  权重为2 
.warning{color:red}  权重为10 
p.note em.dark{color:grag}  权重为22 
#main{color:black}  权重为100     这里还有一种情况： 
```
权重一样时如何处理？ 

3.CSS样式的层叠原则——谁离我近，谁说了算。 
当权重一样时，会采用“层叠原则” 后定义的会被应用。 
```
p{color:yellow} 
p{color:red} 
```
作用到这里   <p>我的什么颜色呢？</p> 
结果会是red的。 
