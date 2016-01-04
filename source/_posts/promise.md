title: promise笔记
date: 2015-12-22 22:48:36
tags:
    - javascript
    - ES6
---

# new Promise()
```
function getURL(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest();
        req.open('GET', URL, true);
        req.onload = function () {
            if (req.status === 200) {
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            }
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send();
    });
}

var URL = "http://httpbin.org/get";
getURL(URL).then(function onFulfilled(value){
    console.log(value);
}).catch(function onRejected(error){
    console.error(error);
});
```
``resolve(req.responseText)`` 在response的内容中加入了参数。
``reject(new Error(req.statusText))`` 创建一个Error对象后再将具体的值传进去。

```
Promise.resolve(11);
等价于
new Promise(function(resolve){resolve(11);});
```
同理Promise.reject(value);

# .catch(error)
使用.catch来将resolve和reject处理分开来写是比较推荐的做法，这样catch就可以捕获到resolve中的错误
```
function throwError(value) {
    throw new Error(value);
}
// <1> onRejected不会被调用
function badMain(onRejected) {
    return Promise.resolve(42).then(throwError, onRejected);
}
// <2> 有异常发生时onRejected会被调用
function goodMain(onRejected) {
    return Promise.resolve(42).then(throwError).catch(onRejected);
}
// 运行示例
badMain(function(){
    console.log("BAD");
});
goodMain(function(){
    console.log("GOOD");
});
```

# .all
接收一个 promise对象的数组作为参数，当这个数组里的所有promise对象全部变为resolve或reject状态的时候，它才会去调用 .then 方法。
```
function getURL(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest();
        req.open('GET', URL, true);
        req.onload = function () {
            if (req.status === 200) {
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            }
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send();
    });
}
var request = {
        comment: function getComment() {
            return getURL('http://azu.github.io/promises-book/json/comment.json').then(JSON.parse);
        },
        people: function getPeople() {
            return getURL('http://azu.github.io/promises-book/json/people.json').then(JSON.parse);
        }
    };
function main() {
    return Promise.all([request.comment(), request.people()]);
}
// 运行示例
main().then(function (value) {
    console.log(value);
}).catch(function(error){
    console.log(error);
});
```

# .race
只要有一个promise对象进入 FulFilled 或者 Rejected 状态的话，就会继续进行后面的处理

全文：http://liubin.github.io/promises-book/