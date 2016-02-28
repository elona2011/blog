date: 2016-01-03 23:17:12
title: Angular2学习笔记(2.0.0-alpha.40)
tags:
---

angular2由组件组成，每个组件都有自己的类、模板和样式。angular2通过不断地构造组件，搭建组件，复用组件来完成项目。
所有项目总是会有一个组件树，所有的组件都在组件树上，父组件包含着子组件。根组件由bootstrap启动。

下面是一个典型的组件文件host.ts：
```
import { Component, View } from 'angular2/angular2';
import { RouteConfig, RouterLink, RouterOutlet } from 'angular2/router';
import { Search } from '/app/recommended/recommendedNavigation/test/search';
import { Artist } from '/app/recommended/recommendedNavigation/test/artist';

@Component({
	selector: 'host'
})

@View({
	directives: [RouterLink, RouterOutlet],
	template: `
		<header>
			<a [router-link]="['./search']">Search</a>
		</header>
		<main>
			<h1>{{title}}</h1>
			<router-outlet></router-outlet>
		</main>`,
	styleUrls: ['host.css']
})

@RouteConfig([
	{ path: '/', redirectTo: '/search' },
	{ path: '/search', as: 'search', component: Search },
	{ path: '/artist/:id', as: 'artist', component: Artist }
])

export class Host {
	title: string;
	constructor() {
		this.title = ' title';
	}
}
```

1	Typescript and ES6
angular2采用typescript语法和ES6 ，比较常用的有：

1.1	箭头函数
chrome的调试窗口中箭头函数中的this会显示为指向Window，该显示是错误的，实际指向class

1.2	let
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

1.3	class
```
export class Hello {//定义类和构造函数
    name: string = 'World';
    constructor() {
        setTimeout(() => {
          this.name = 'NEW World'
        }, 2000);
    }
}
```
Constructor构造函数，初始化数据

参考：
http://www.typescriptlang.org/Handbook
http://es6.ruanyifeng.com/

2	import,export
import引入依赖的模块及自定义组件
例1：``import {ComponentMetadata as Component, ViewMetadata as View, bootstrap, CORE_DIRECTIVES } from 'angular2/angular2';``
例2：``import {Zippy} from 'zippy';``

export输出组件和函数
例1：``export class Search {}``
例2：``export function status(response) {...}``

2.1	依赖关系
FORM_DIRECTIVES:ng-model
ROUTER_DIRECTIVES:<router-outlet>
CORE_DIRECTIVES:NgIf, NgFor, Pipe, OnInit		包含所有CORE里的指令
例1：
```
import {Component, View, CORE_DIRECTIVES, NgStyle} from 'angular2/angular2';
@View({
	directives: [CORE_DIRECTIVES, NgStyle]
})
```
例2：
```
import {Component, View, EventEmitter} from 'angular2/angular2';
import {FORM_DIRECTIVES} from 'angular2/forms';
import { RouterOutlet } from 'angular2/router';
import { RouterLink } from 'angular2/router';
import { ROUTER_DIRECTIVES, RouteConfig } from 'angular2/router';
import { ROUTER_BINDINGS, LocationStrategy, HashLocationStrategy } from 'angular2/router';
```

3	@Component组件
3.1	selector
组件名称。
例：``selector: 'zippy',``
3.2	properties
申明组件的外部属性,其它组件可以通过这个属性传入参数。
例1：``properties:['myTitle1',’myTitle2’]``
例2：``<zippy [my-title1]="title2"></zippy>`` 绑定title2变量
例3：``<zippy [my-title2] = "’title2’"></zippy>`` 绑定title2字符串
例4：``['tabTitle: tab-title']``申明变量tabTitle,将tab-title绑定到组件内的tabTitle变量上。内部绑定的优先级高于外部绑定，例如例4的绑定高于例2的绑定。
3.3	events
申明事件。
例：``events: ['open', 'close'],``

3.4 host
内部事件。
例1：
```
host: {
    '(mouseenter)': 'focusElement("77")'
  }
```
例2：内部绑定和外部绑定的相互切换。一个属性同时在template和组件class中绑定，只要有其中一个值改变，属性值就会刷新。
```
import {View, Component, bootstrap, Directive, Host, Optional} from 'angular2/angular2'

@Component({
  selector: 'bank-account',
  properties: ['bankName:bank-name', 'id: account-id'],
  host: {
    '(mouseout)': 'focusElement("77")'
  }
})
@View({
  template: `
    Bank Name: {{bankName}}
    Account Id: {{id}}
  `
})
class BankAccount {
  bankName: string;
  id: string;
  
  constructor(){
    this.bankName = "222";
  }
  focusElement(isFocus) {
    this.bankName = isFocus;
  }
  
  // this property is not bound, and won't be automatically updated by Angular
  normalizedBankName: string;
}
@Component({selector: 'app'})
@View({
  template: `
    <bank-account [bank-name]="RBC1" account-id="4747" (click)="onclick()"></bank-account>
  `,
  directives: [BankAccount]
})
class App {
  RBC1: string;
  constructor(){
    this.RBC1 = "2221";
  }
  onclick(){
    this.RBC1 = this.RBC1+1;
  }
}
bootstrap(App);
```

3.5 bindings
绑定依赖，先要import该依赖。绑定可供子模块查询。
例：``bindings: [IptvService, AuthenticateService]``

3.6 viewBindings
``viewBindings:[bind(VideoService).toClass(SpecificVideoService)]``  绑定的对象只能供本模块使用，不会影响到子模块

4 @View视图
4.1 directives
template中用到的angular指令和自定义指令，camel驼峰写法。
例：``directives: [EzCard],``

4.2 template
该视图的模板，html代码。directives要用小写中划线写法。
例：``template: ‘< ez-card [title1]="'deeeeeeee'"></ ez-card >’,``

HTML元素属性的几种写法：
``title="Details"``：title属性为字符串Details
``[title]="'Details'"``： title属性为字符串Details
``[title]="Details"``： title属性为变量Details
``bind-title=”’Details’”``： title属性为字符串Details

 ``<input #searchvalue (keyup)="searchArtist($event, searchvalue.value)"/>`` #searchvalue会双向绑定到input对象上，searchvalue.value可实时更新input输入值

4.3 templateUrl
模板地址，引入外部HTML文件。例：``templateUrl: 'zippy.html'``

4.4 styles
``styles: ['.tabs1 {background-color: green;}','{...}'],`` 声明的样式只在本组件中可用，默认，取决于encapsulation

4.5 styleUrls
``styleUrls: ['zippy.css'],`` 声明外部样式文件
此外还可以直接写在template中，多用于关联动态样式，如生成动态获取的背景图片

下面有导致hexo出错的BUG

4.6 encapsulation
封装设置。
ViewEncapsulation.None 无样式封装，样式位于<head>中，将全局可用。
ViewEncapsulation.Emulated 样式模拟，样式位于<head>中，仅当前组件可用，默认。
ViewEncapsulation.Native 当前组件可用，样式位于组件中，仅当前组件可用。

5 @Directive
https://github.com/angular/angular/blob/master/modules/angular2/docs/core/02_directives.md

6 常用指令
6.1 #
定义一个当前组件的局部变量，绑定当前位置的HTML元素，变量名只能小写
例1：``<input #searchvalue (keyup)="searchArtist(searchvalue.value)"/>``
例2：``<input class="form-control" type="text" placeholder="Your new friend" #friend (keyup) ="update(friend.value)">``

6.2 \\{\\{\\}\\}

动态变量或表达式
```
例1：``{{i%6}}``
例2：``<div>{{visible?'&blacktriangledown;':'&blacktriangleright;'}}</div>``
```
6.3 ``[]``
[参数]用于父组件向子组件传递参数，(事件)用于子组件向父组件传递事件。
例：``<todo-cmp [model]="todo" (complete)="onCompletingTodo(todo)"></todo-cmp>`` 其中model是子组件中定义的参数，todo是父组件中的变量，如果todo改变，model也会自动改变；complete是子组件中定义的事件，onCompletingTodo是父组件中的方法，complete事件将触发onCompletingTodo方法。

6.4 ng-for
例：``<div *ng-for="#content of contentList; #i= index">``
contentList为将遍历的数组，#content为遍历数组的元素，#i为数组指针。在当前div及其子元素可用``{{content}}``和``{{i}}``进行引用
6.5 ng-if
当*ng-if之后的表达式为true，则显示该HTML元素；反之则删除。显示删除过程会触发Lifecycle
例：
```
<div>
  <btv-player-menu *ng-if="isShowBtvPlayerMenu"></btv-player-menu>
  <btv-player-minidetail-page *ng-if="isShowBtvPlayerMinidetailPage"></btv-player-minidetail-page>
  <btv-player-reminder *ng-if="isShowBtvPlayerReminder"></btv-player-reminder>
</div>
```

6.6 ng-switch

6.7 ng-model

6.8 ng-style
例1：``<div [ng-style]="{'background-image':'url('+picture+')'}"></div>`` 背景图绑定picture变量，picture为图片地址
例2：``<div [ng-style]="{'text-align': alignExp}"></div>``
例3：``<div [ng-style]="styleExp"></div>``  可以是变量

6.9 ng-class
根据表达式的结果添加或移除CSS属性
例：``<div class="button" [ng-class]="{active: isOn, disabled: isDisabled}">``

6.10  ng-content
``<ng-content></ng-content>``表明其它组件或内容插入当前组件的位置。
例：``<zippy><p>111</p></zippy>``，其中``<p>111</p>``将插入zippy组件的template中的ng-content位置。

6.11  router-outlet
router的输出位置。

6.12  router-link
router-link表示跳转名称为search的地址，而不是跳转到/search的url下，见@RouteConfig。
有三种写法：
例1：``[router-link]="['./search']"`` search位于当前组件路径下
例2：``[router-link]="['../search']"``  search位于当前组件的父路径下
例3：``[router-link]="['/search']"``  绝对路径，从根路径开始
还可以传递参数：
例4：``[router-link] =”['/team', {teamId: 1}, 'user', {userId: 2}]”``


6.13  Pipe
1.import
```
import {Pipe} from 'angular2/angular2';
```

2.根据Pipe设定变量类型
```
public starttime: number = 0;
public endtime: number = 0;
this.starttime = parseInt(this.playbilllist.playbilllist[0].startTimeMilli);
this.endtime = parseInt(this.playbilllist.playbilllist[0].endTimeMilli);
```

3.使用Pipe设定时间
```
<div>{{starttime | date:'HHmm'}} - {{endtime | date:'HHmm'}}</div>
```
参考：
http://www.shmck.com/angular-2-pipes/
https://github.com/auth0/angular2-pipes

7 bootstrap
启动Main程序，[]中的绑定将全局可用
例：bootstrap(App, []);
8 inject
1.template中，注入的类为父子关系
```
<pet-list >
<pet-input></pet-input>
</pet-list>
```

2.import
```
import {PetList} from 'byinjection/PetList';
import { Inject, forwardRef} from 'angular2/angular2'; 
```

3.class注入，调用注入class的方法
```
export class PetInput {
  petList: PetList;

  constructor(@Inject(forwardRef(()=>PetList)) petList:PetList) { //petList为单例，指向dom树中的<pet-list>
    this.petList = petList;
  }

  doSomeThing(){
  this.petList.addItem(...); //调用petList的方法，可以传参
}
}
```

参考：
https://github.com/SekibOmazic/angular2-playground
http://blog.thoughtram.io/angular/2015/09/03/forward-references-in-angular-2.html

9 事件
9.1 系统事件
click事件
```
<div (click)="toggle()">
```
(click)监听click事件
toggle()事件触发函数
```
<div [hidden]="!visible">
```
[hidden] 中括号将HTML元素或组件的属性绑定到组件模型的某个表达式，当表达式的值变化时，对应的DOM对象将自动得到更新。
visible为对应class中定义的变量
keyup事件
例：``<input class="form-control" type="text" placeholder="Your new friend" #friend (keyup) ="update(friend.value)">``
键盘事件
1.document方法：
将下面代码加入class的constructor中
```
document.onkeydown = function(event) {
  switch (event.keyCode) {
    case 38:
      alert('clear');
      break;
  }
}
```

2.window方法：
将下面代码加入class的constructor中

```
window.addEventListener("keydown",()=>{
//1、显示miniepg
if (window.event && window.event.which === 73) {
this.showFlag = true;
}
}, true);
```

3.Angular2方法：
1.import
```
import {KeyEventsPlugin} from 'angular2/src/core/render/dom/events/key_events';
```

2.template中修改需要加入键盘事件的HTML元素，使用时该元素要先获得焦点
```
<div (keyup) ="onKeyDown($event)" tabindex="0">
```

3.class中加入以下方法，取得的lastKey为字符串
```
onKeyDown(event): void {
  this.lastKey = KeyEventsPlugin.getEventFullKey(event);
  event.preventDefault();
}
```

9.2 自定义事件
1.引入依赖
```
import {Component, View, EventEmitter} from 'angular2/angular2';
```

2.@Component声明
```
@Component({
    selector: 'zippy',
    events: ['open', 'close']
})
```

3.class类里定义事件变量
```
export class Zippy {
constructor() {
  this.open = new EventEmitter();
  this.close = new EventEmitter();}}
```

4.触发方法
toggle()方法执行，将触发事件：
```
toggle() {
      (this.visible)?this.open.next({src:’111’}):this.close.next();
    }
{src:’111’}为事件传参，在下面的$event会收到这个参数
```

5.使用该组件事件
```
<zippy (open)="sayOpen($event)" (close)="sayClose()"></zippy>
$event为事件传入参数
```
(open)可写为on-open，(close)可写为on-close

事件从组件内部发送到组件上，从而可以调用其它组件的方法：
```
<gadget-input (store)="gadget.onAddItem($event)"></gadget-input>
<gadget-list #gadget></gadget-list>
```

9.3 Observer事件
1.引用依赖
```
import {ObservableComponent} from 'base/core/ObservableComponent';
import {Event} from 'base/core/Event';
```

2.定义一个类
重写listNotificationInterests，返回一个数组包括所有事件名
用Event.getInstance().on方法设置所有事件的回调函数
```
class MyEvent extends ObservableComponent{
  constructor(){
    super();
    super.onInit();
    Event.getInstance().on("aaa", () => { console.log("I'm aaa") });
    Event.getInstance().on("bbb", () => { console.log("I'm bbb") });
  }

  listNotificationInterests() {
    return ["aaa", "bbb"];
  }
}
```

3.生成一个实例
```
constructor(iptvService: IptvService) {
    this.MyEvent = new MyEvent();
}
```

4.调用函数发事件
```
emitTest(){
    Event.getInstance().emit("bbb");
    Event.getInstance().emit("aaa");
}
```

9.4 Lifecycle
Lifecycle可以看作是组件自带的系统事件，在组件运行的关键时间点可添加处理函数，alpha.37改为如下写法请注意。
例：
1.import
```
import {OnInit, OnDestroy} from 'angular2/angular2';
```

2.重写相关Lifecycle方法
```
export class About implements OnInit, OnDestroy {
  onInit(){
    ...
  }

  onDestroy(){
    ...
  }
}
```

10  Router
10.1  router策略
``bind(LocationStrategy).toClass(HashLocationStrategy)`` 使用hash url定位策略
``bind(LocationStrategy).toClass(PathLocationStrategy)`` 需在index.html的<head>中加入<base href="/">

10.2  @RouteConfig
```
@RouteConfig([
  { path: '/', redirectTo: '/search' },
  { path: '/search', as: 'search', component: Search },
  { path: '/artist/:id', as: 'artist', component: Artist }
])
```
path: '/'为默认路径。
redirectTo：跳转到其它路径
as：路径的别名，用于[router-link]中引用
component：引用的组件类名

10.3  router设置
```
1.import { ROUTER_BINDINGS, LocationStrategy, HashLocationStrategy, PathLocationStrategy } from 'angular2/router';
import {bind} from 'angular2/angular2';
import { ROUTER_DIRECTIVES, RouteConfig, RouterLink } from 'angular2/router';
bootstrap(App, [ROUTER-BINDINGS, bind(LocationStrategy).toClass(HashLocationStrategy)]);

2.@RouteConfig([
    {path:'/', component:Start, as: 'start'}
])
3.<router-outlet></router-outlet>
directives: [ROUTER_DIRECTIVES, RouterLink]

4.<a [router-link]="['./user']">link to user component</a>
```

10.4  router跳转
1.import
```
import {Router} from 'angular2/router';
```

2.constructor注入
```
constructor(..., public router: Router) {
    ...
  }
```

3. url跳转方法
```
this.router.navigateByUrl('/home/livetv');
```

10.5  父子路由
1、  针对父—子路由：
父路由配置（在父ts文件下）：
  （1）、导入路由所需组件：
```
import { Router, RouteConfig, ROUTER_DIRECTIVES, ROUTER_BINDINGS } from 'angular2/router';
```
  （2）、配置路由：
```
@RouteConfig([
  { path: '/', redirectTo: '/login/userlogin' },   // redirectTo默认页面
  { path: '/login/...', component: Login, as: 'login' },  // component为导入的组件
  { path: '/mytvNavigation/...', component: MyTVNavigation, as: 'mytvNavigation' }
])
```
子路由配置（子ts文件中）：
  （1）、同上；
  （2）、配置路由：
```
@RouteConfig([
  { path: '/mytvNavigation', redirectTo: '/history'},
  { path: '/history', component: History, as: 'history'},
  { path: '/favorite', component: Favorite, as: 'favorite' },
{ path: '/profile/...', component: Profile, as: 'profile'}
])
```

其中path最好写上父路由路径，如果不写，在页面跳转时要加上父路径的path。
如果子路由下还存在子路由（如profile），以此类推……
注：凡是配置路由的ts文件，其``@View{}``中必须配置路由出口``<router-outlet></router-outlet>``，否则即使url地址变化，页面内容还是显示不出或者跳转不了！！！！
路由出口需要的组件：ROUTER_DIRECTIVES / RouterOutlet

11  Service服务
service是单例，数据共享给所有使用者
11.1  自定义Service
使用服务的4步，包括定义、引入、绑定、使用
1.定义Service
在angular2中，服务就是一个类。例：自定义一个简单的服务：
```
export class DataService {
  items:Array<any>;

  constructor() {
    this.items = [
      { name: 'Christoph Burgdorf' },
      { name: 'Pascal Precht' },
      { name: 'thoughtram' }
    ];
  }

  getItems() {
    return this.items;
  }
};
```
2.引入Service
```
import {DataService} from 'dataService';
```

3.绑定Service
有两种方法：
1.bootstrap绑定:
```
bootstrap(Hello, [DataService]);
```

2.Component中使用bindings，见@Component

4.使用Service
```
  constructor(dataService : DataService) {
    this.title = dataService.items[0].name;
    }
```
11.2  Service依赖
服务中需要引入依赖，以HTTP为例：
1.bootstrap文件
import {HTTP_BINDINGS} from 'angular2/http';
…
bootstrap(Hello , [HTTP_BINDINGS] );
2.服务文件
import {Injectable} from 'angular2/core';
import {Http} from 'angular2/http';
@Injectable()
export class DataService {
  constructor(http:Http) {...}
};
本文件另一种写法：
import {Http} from 'angular2/http';
import {Inject} from 'angular2/angular2';
export class DataService {
  constructor(@Inject(Http)  http:Http ) {...}
};
原文：http://blog.thoughtram.io/angular/2015/09/17/resolve-service-dependencies-in-angular-2.html

12  node_modules
systemjs - 通用模块加载器，支持AMD、CommonJS、ES6等各种格式的JS模块加载
es6-module-loader - ES6模块加载器，systemjs会自动加载这个模块
traceur - ES6转码器，将ES6代码转换为当前浏览器支持的ES5代码。systemjs会自动加载 这个模块。
13  实例
13.1  三种通信实例
本实例演示组件通信的三种方法：事件、服务、注入。提供源码。
三种方法的理解：事件
地址：https://github.com/SekibOmazic/angular2-playground
演示方法：
1下载源代码，点击Download Zip下载
 
2解压下载的ZIP文件
3命令行进入解压好的目录，npm i回车
 
4gulp play
 
5实际显示页面，三种通信方法

14  报错
Uncaught SyntaxError: Unexpected token <
可能原因：ts文件未能成功编译成js文件，实际的错误提示是找不到js文件。
解决：templateUrl路径不对，或是错误使用``引号，应使用’’引号

EXCEPTION: Invalid argument XXXX for XXX 'function () {}' in [null]
可能原因：参数类型不符。
解决：重点检查传入参数的类型。

EXCEPTION: Cannot resolve all parameters for ClassName (Router, ?). Make sure they all have valid type or annotations. in [null]
可能原因：找不到class
解决：@Inject(forwardRef(()=>ClassName)) classname: ClassName
参考：http://blog.thoughtram.io/angular/2015/09/03/forward-references-in-angular-2.html

EXCEPTION: LifeCycle.tick is called recursively
可能原因：页面删除时focus状态未清除
解决：将focus设置到非动态focus的元素上

15  版本改变
https://github.com/angular/angular/blob/master/CHANGELOG.md
16  参考资料
官方文档：
https://angular.io/docs/js/latest/
https://github.com/angular/angular
https://github.com/timjacobi/angular2-education