title: angularjs
date: 2016-02-09 09:29:03
tags:
---

# 代码规范
https://github.com/johnpapa/angular-styleguide

# 入门教程
http://www.revillweb.com/tutorials/angularjs-in-30-minutes-angularjs-tutorial/
https://github.com/colorfest/angularjs

# 原理
https://github.com/angular/angular.js/wiki/Understanding-Dependency-Injection

Providers are objects that provide (create) instances of services and expose configuration APIs that can be used to control the creation and runtime behavior of a service.

# $scope.$apply
[all Controller code should expect to be run within Angular, so it should have no need to call $apply or $digest. Conversely, code that is being trigger directly as a call back to some external event, from the DOM or 3rd party library, should expect that it is never called from within Angular, and so any Angular application code that it calls should first be wrapped in a call to $apply.](https://docs.angularjs.org/error/$rootScope/inprog?p0=$apply)

# Directive

## ng-app

## ng-controller

## ng-model

```
Search: <input ng-model="query">
```

## ng-repeat
ngRepeat使用时要注意传入的是数组还是对象，如果是对象，且使用数组的写法，会导致n的排序为对象key的字母顺序。此情况多发生在，错误地将数组转成了对象，且未发现。
如数组[1,2,3,4,5,6,7,8,9,10]排序正常，但对象{1:1,2:2,3:3,4:4,5:5,6:6,7:7,8:8,9:9,10:10}的排序将为{1:1,10:10,2:2,3:3,4:4,5:5,6:6,7:7,8:8,9:9}

```
<li ng-repeat="phone in phones | filter:query">
  {{phone.name}}
  <p>{{phone.snippet}}</p>
</li>
```

# Custom Directive

在自定义指令中传入回调函数，还可以传参
```
<custom-directive callback="callback(data)"></custom-directive>
```

recursion directive
http://stackoverflow.com/questions/14430655/recursion-in-angular-directives

# Service

$exceptionHandler 可以重写exception catch

# Building

https://docs.angularjs.org/misc/contribute

``grunt webserver`` start the web server
