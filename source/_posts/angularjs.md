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
```
<li ng-repeat="phone in phones | filter:query">
  {{phone.name}}
  <p>{{phone.snippet}}</p>
</li>
```

# Service

$exceptionHandler 可以重写exception catch

# Building

https://docs.angularjs.org/misc/contribute

``grunt webserver`` start the web server
