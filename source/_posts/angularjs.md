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


# Building

https://docs.angularjs.org/misc/contribute

``grunt webserver`` start the web server