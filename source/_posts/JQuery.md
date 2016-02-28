title: JQuery
date: 2015-03-17 22:45:10
tags: 
    - jquery
    - javascript
---

JQuery

## 选择器

$("p~")之后同级全部
$("p+")之后最近的一个
$("div > label")子元素，不包括孙元素
$("div label")div的所有后代label

$("li:last")最后一个li
$("li:first-child")第组中的第一个
$("li:eq(2)")第3个li
$("li:eq(-3)")倒数第3个li
$("li:contains('jQuery')")根据内容选择
$("li:has('label')")根据元素选择
$("input:hidden")获取全部不可见的元素
$("li[title='蔬菜']")属性选择

$("#frmTest :input")
$(":text")
$(":radio")
$("#frmTest :checkbox")

$('div[title]') 选择拥有title属性的div

.text和.html的区别

对jQuery对象取数组元素[0],[1],...取到的是DOM对象，可以使用DOM对象的原生属性和方法：
className属性：读取和设置class属性
classList属性：类似className属性，返回的是类数组
.classList.add():增加一个class
.classList.remove():移除一个class

``$(function(){ });`` 当文档载入完毕就执行
``$(document).ready(function(){ })`` 同上
<<<<<<< HEAD


=======
>>>>>>> bed7b8dc1855a68fd337e1e0733c839809d00117
