title: toString和valueOf的隐式转换
date: 2015-01-02 17:33:45
tags:
    - javascript
---


理论上，toString是转换为字符串的方法，valueOf是转换成数值的方法。

```
'aaa' + {toString: function(){return 'bbb';}}   //"aaabbb"
11 + {valueOf: function(){return 4;}}   //15
```

如果，一个对象既有toString也有valueOf，那么是否仍按上面的规则呢?

```
var a = {
    toString: function(){
        return '111';
    },
    valueOf: function(){
        return 100;
    }
}
a+1     //101
a+'b'   //"100b"
```

实际情况是这样的，无论要转换为字符串还是数值，首先调用valueOf方法，如果不存在，那么调用toString方法。~~如果valueOf方法返回不是基本类型，那么还会对返回结果再调用一次toString~~

那么，再看下例

```
var a = {
    toString: function(){
        return '111';
    },
    valueOf: function(){
        return {};
    }
};
var b = {};
1*a     //111
1+a     //"1111"
1+b     //"1[object Object]"
1*b     //NaN
```

如果valueOf方法返回不是基本类型，那么就使用toString的返回值并进行强制类型转换

```
var a = {
    toString: function(){
        return {};
    },
    valueOf: function(){
        return {};
    }
};
1+a     //Uncaught TypeError: Cannot convert object to primitive value(…)
1*a     //Uncaught TypeError: Cannot convert object to primitive value(…)
```

如果将valueOf和toString方法都返回对象，将导致无法隐式转换

结论：最好将valueOf和toString方法的返回结果统一，并且只使用其中一个方法，如toString