title: javascript笔记
date: 2015-01-21 20:56:51
tags: javascript

---

# 数据类型

数据类型为：undefined, boolean, number, string, object，前4种为基本类型，第5种为引用类型
基本类型无法添加属性,如需添加可以在prototype上添加
```
var a = '111';
a.value = '222';
console.log(a.value); //undefine
console.log(a.length); //3
String.prototype.bb = '33';
a.bb; //'33'
```

typeof可返回6种类型：undefined, boolean, number, string, object, function

基本类型中的假值
false, 0, "", NaN, null, undefined, 除了这6个值，其它所有值均可隐式转换为true 

# 变量

若变量声明不在顶部,则会自动声明,但不赋值
```
var a = 1;
function b(){
         alert(a);
         var a = 2; //等价于在第一个alert前有一个var a;此处为a=2;
         alert(a);
}
b();
```

# 表达式

字符串比较中是按第一个不相同的字符的ascall码值来比较的
```
'2' > '10' //true
```

为什么++[[]][+[]]+[+[]] === '10'是true?
首先``+[] === 0``
原表达式可转换为``++[[]][0]+[0]``
``[[]][0]`` 表示返回内部数组 ([])
转换为``++[]+[0]``,可以这么理解,但不能这么写,因为``[]+1==1``,但``++[]``会报错
然后转换为1+[0]
最终为1+'0'='10'

# 对象

对象的赋值实际是保存该对象的地址
对象的属性的赋值分为两步，先是判断该对象是否有该属性，没有就先创建；然后赋值
例:
```
var a = {n:1}; //a获取对象{n:1}的地址
var b = a; // 将a的值赋给b，b也获取对象{n:1}的地址
a.x = a = {n:2}; //首先在对象上创建属性，得到对象{n:1, x:undefine}，此时a和b都指向它；然后a获取对象{n:2}的地址，a改变了值；对象{n:1, x:undefine}的x获取对象{n:2}的地址
alert(a.x);// --> undefined
alert(b.x);// --> {n:2}
```

## 对象的类型

```
function A(){}
var a = new A();
if(typeof a === 'object'){} //基本类型判断
if(a instanceof A){} //实例判断
if(a.constructor === A){} //构造器函数判断
```

# 函数

## 常用技巧

缓存函数
```
function getElements(name){
  if(!getElemnts.cache) getElements.cache = {};
  return getElements.cache[name] = getElements.cache[name] || document.getElementsByTagName(name);
}
```
DOM的缓存(地址缓存，数据都是实时最新的)
```
function a(){
    var cache = {};
    return function(dom){
        return cache[dom] ? cache[dom] : cache[dom] = document.getElementById(dom);
    }
}
var b= a();
console.log(b("test").innerHTML);
document.getElementById('test').innerHTML="you";
console.log(b("test").innerHTML);
```

函数判断
```
function isFunction(fn){
  return Object.prototype.toString.call(fn) === "[object Function]";
}
```

重载函数
```
function addMethod(object, name, fn){
  var old = object[name];
  object[name] = function(){
    if(fn.length === arguments.length)
      return fn.apply(this, arguments);
    else if(typeof old === 'function')
      return old.apply(this, arguments);
  }
}
```

私有变量
```
function Ninjia(){
  var feints = 0;
  this.getFeints = function(){
    return feints;
  }
  this.feint = function(){
    feints++;
  }
}
var ninja = new Ninjia();
ninja.feint();
```

## 基本概念
函数中没有return语句，则相当于return undefine;


## this
this是隐式传入参数，改变this的方法就是将函数作为对象的方法调用

立即执行函数中的this
```
var c = {d:function(){
  console.log(this);
  (function(){
    console.log(this);
  })();
}};
c.d();
-Object { d: c.d() } //第1个this
-window  //第2个this
```

隐式绑定
例1：

```javascript
var me = {
	a: 3,
	show:show
};
function show(){
	console.log(this.a);
}
me.show(); //this绑定到me上，输出3
```

例2：
如果将me.show赋值给一个变量，再调用：

```javascript
var show1 = me.show;
show1(); //undefine,和上例完全不同！！
```

例3：
同样，作为回调函数：

```javascript
setTimeout(me.show, 1000); //undefine,参数传递其实就是一种赋值，结果和例2一样
```

例4：
例3的解决方法：

```javascript
setTimeout(function(){me.show();}, 1000); //3,传递了一个匿名函数直接调用me.show()，结果和例1一样
```

## 参数赋值
如果函数内部对于参数整体赋值修改，那么都不会影响外部，无论参数是数组，对象。
但如果该参数有元素(数组)或属性(对象)，函数内直接对元素或属性赋值，那么将影响到函数外部。
实际上，该问题和对象的引用有关。当复制对象时，操作的是对象的引用。但为对象添加修改属性时，操作的是对象本身。

## 立即执行函数
(function b(){})();
b();    //抛出一个referenceError,b函数只能在函数表达式内部访问

对象的属性名都是字符串，如果不是，也会先转化成字符串，如下：
```
var myObject={};
myObjcet[true] = "foo";
myObject[3] = "bar";
myObject[myObject] = "baz";
myObject['true"]; //"foo"
myObject["3"]; //"bar"
myObject["[object Object]"]; //"baz"
```
还可以写成:
```
~function b(){}();
+function b(){}();
```

## get和set
var my={
get a(){return this._a_;},
set a(val){this._a_=val*2;}
};
my.a=2;
my.a; //4
 
所有的普通对象都可以通过对于Object.prototype的委托来访问hasOwnProperty()，但有的对象可能没连接到Object.prototype（通过Object.create(null)来创建），这时访问myObject.hasOwnProperty()会失败。但可以使用Object.prototype.hasOwnProperty.call(myObject, "a")

可枚举相当于“出现在对象属性的遍历中”，即for(var k in myObject){...}遍历可枚举属性
for...in可遍历对象的可枚举属性列表，包括[[prototype]]链
("b" in myObject); //查找[[Prototype]]链
myObject.hasOwnProperty("b"); //只查找对象直接包含的属性
Object.keys(myObject); //返回一个数组，包含所有可枚举属性，不查[[Prototype]]链
Object.getOwnPropertyName(myObject); //返回一个数组，包含所有属性，不查[[Prototype]]链

# Ajax
## XMLHttpRequest
```
var xhr = new XMLHttpRequest();
xhr.open('get', 'http://yanjie.me/');
xhr.onload = function() { /* do something */ }
xhr.setRequestHeader('Content-Type', 'application/json');
xhr.setRequestHeader('Content-Length', JSON.stringify(data).length);
xhr.send(JSON.stringify(data));
xhr.status
xhr.responseText
```

## CORS(Cross Origin Resourse-Sharing)
验证简单跨域请求与非简单跨域请求合法性的区别就在于，验证非简单跨域请求前，浏览器向服务器发送一个OPTIONS方法的预检请求来加以判断，如果预检失败，实际请求将被丢弃。而简单跨域请求浏览器会正常发送请求，再对返回头加以判断以检查请求的合法性。在检查失败时，浏览器将会阻止脚本对返回内容的访问。
简单跨域请求并不会包含下面的HTTP头。而预检请求将会发送以下HTTP头
Origin: 普通的HTTP请求也会带有，在CORS中专门作为Origin信息供后端比对
Access-Control-Request-Method: 接下来请求的方法，例如PUT, DELETE等等
Access-Control-Request-Headers: 自定义的头部，所有用setRequestHeader方法设置的头部都将会以逗号隔开的形式包含在这个头中
其他头，例如实际请求的头部，Cookie头等都将不被包含在预检请求中。
```
Access-Control-Allow-Origin: "*" //表示该网站支持跨域请求
```

https的页面请求http的ajax请求会报错

## JSONP

http://www.cnblogs.com/dowinning/archive/2012/04/19/json-jsonp-jquery.html

# ES6
## let

```
for(var i=1;i<5;i++){
 setTimeout(function timer(){
  console.log(i);
 },i*1000);
} //输出4个5
for(let i=1;i<5;i++){
 setTimeout(function timer(){
  console.log(i);
 },i*1000);
} //输出1，2，3，4
```

## class
与ES5一样，实例的属性除非显式定义在其本身（即定义在this对象上），否则都是定义在原型上（即定义在class上）
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '('+this.x+', '+this.y+')';
  }
}

## 不建议使用
arguments.callee指向当前函数(将被废弃)
使用内联命名函数

```
var a={
  b: function c(n){
    return n > 1 ? c(n-1) + "_@" : "@";
  }
};
```

arguments.callee.caller指向调用当前函数的函数

# 函数速查

## String
String(true) // "true" 转换为字符串

### indexOf
确定一个字符串在另一个字符串中的位置,0开始.如果返回-1,表示不匹配

match
search

### replace
replace方法的第二个参数是一个函数时，将匹配内容作为函数参数，替换为函数返回值。
它的第一个参数是捕捉到的内容，第二个参数是捕捉到的组匹配（有多少个组匹配，就有多少个对应的参数）
```
'/* <span id="test1">111</span><span id="test2">222</span> */'.replace(
  /(<span id=")(.*?)(">)(<\/span>)/g,
  function(match, $1, $2, $3, $4){
    return $1 + $2 + $3 + prices[$2] + $4;
  }
);
```

### split
返回按指定规则分割后的数组７
```
var e = "a,b,c".split(/,\s*/);
```

## Array
### join
join方法以参数作为分隔符，将所有数组成员组成一个字符串返回。如果不提供参数，默认用逗号分隔。

### splice
第一个参数是删除的起点，第二个参数是被删除的个数。之后的参数表示要被插入数组的新元素。返回值是被删除的元素[数组]

### concat
传入参数需转为数组
```
function a(){return [1].concat(arguments);}
undefined //return
a(2,3)
Array [ 1, Arguments ] //return

function a(){return [1].concat(Array.prototype.slice.call(arguments));}
undefined //return
a(2,3)
Array [ 1, 2, 3 ] //return
```

## document
### getElementsByTagName(name)
The special string "*" represents all elements.

### 选择器性能测试
```
console.time('jq');
for(var i =0;i<100000;i++)$('#main_panel #action_list_page #action_list li');
console.timeEnd('jq');
```
耗时：getElementsByTagName<querySelector<querySelectorAll<jq选择器

## Element

$(a).data()添加自定义属性在a的缓存中；读取时，先从缓存中读，再从data-*属性中读

$(a).attr()添加自定义属性在a上
a.setAttribute('aaa','111')设置属性在a.attributes下
a.getAttribute('aaa')
$(a).attr('aaa')

a.setAttribute('data-aaa-bbb','211')设置属性在a.dataset下
a.getAttribute('data-aaa-bbb')
a.dataset.aaaBbb
$(a).attr('data-aaa-bbb')

el.closest(selector)返回当前元素节点的最接近的非子元素（父元素或节点本身）
el.classList.add('aaa')
el.classList.remove('className');
el.classList.contains('className');
el.classList.toggle('className');

## window
### setTimeout
返回一个整数，表示定时器的编号，以后可以用来取消该定时器。

## console
打印时间间隔，能显示到微秒级，new Date()只显示到毫秒级
console.time('a')
console.timeEnd('a')

# 文章收集
JS模板
http://div.io/topic/758 