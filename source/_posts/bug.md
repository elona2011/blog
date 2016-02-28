title: bug收集
date: 2015-11-04 22:21:17
tags:
  - bug
categories:
      - bug
---

# hexo
```
{{}}
```
如果不加代码高亮,将引起如下错误
Template render error: unexpected token: }}
    at Error.exports.TemplateError (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/<font color=red>nunjucks</font>/src/lib.js:51:19)
    at Object.extend.fail (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:64:15)
    at Object.extend.parsePrimary (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:947:18)
    at Object.extend.parseUnary (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:882:25)
    at Object.extend.parsePow (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:856:25)
    at Object.extend.parseMod (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:844:25)
    at Object.extend.parseFloorDiv (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:832:25)
    at Object.extend.parseDiv (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:820:25)
    at Object.extend.parseMul (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:808:25)
    at Object.extend.parseSub (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:796:25)
    at Object.extend.parseAdd (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:784:25)
    at Object.extend.parseCompare (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:751:25)
    at Object.extend.parseIn (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:720:23)
    at Object.extend.parseNot (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:716:21)
    at Object.extend.parseAnd (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:698:25)
    at Object.extend.parseOr (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:686:25)
    at Object.extend.parseInlineIf (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:668:25)
    at Object.extend.parseExpression (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:663:25)
    at Object.extend.parseNodes (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1158:30)
    at Object.extend.parseAsRoot (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1177:42)
    at Object.module.exports.parse (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1199:18)
    at Object.module.exports.compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/compiler.js:1118:48)
    at Obj.extend._compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:444:35)
    at Obj.extend.compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:433:18)
    at null.<anonymous> (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:378:22)
    at Object.exports.withPrettyErrors (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/lib.js:24:16)
    at Obj.extend.render (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:374:20)
    at Obj.extend.renderString (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:261:21)
    at /media/nari/工作/blog/blog/node_modules/hexo/lib/extend/tag.js:56:9
    at tryCatcher (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/util.js:26:23)
    at Promise._resolveFromResolver (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:480:31)
    at new Promise (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:70:37)
    at Tag.render (/media/nari/工作/blog/blog/node_modules/hexo/lib/extend/tag.js:55:10)
    at Object.tagFilter [as onRenderEnd] (/media/nari/工作/blog/blog/node_modules/hexo/lib/hexo/post.js:253:16)
    at /media/nari/工作/blog/blog/node_modules/hexo/lib/hexo/render.js:55:19
    at tryCatcher (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/util.js:26:23)
    at Promise._settlePromiseFromHandler (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:507:31)
    at Promise._settlePromiseAt (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:581:18)
    at Promise._settlePromises (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:697:14)
    at Async._drainQueue (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:123:16)
    at Async._drainQueues (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:133:10)
    at Immediate.Async.drainQueues [as _onImmediate] (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:15:14)
    at processImmediate [as _immediateCallback] (timers.js:367:17)

```
<div>{{visible?'&blacktriangledown;':'&blacktriangleright;'}}</div>
```
如果不加代码高亮,将引起如下错误
Template render error: expected variable end
    at Error.exports.TemplateError (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/lib.js:51:19)
    at Object.extend.fail (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:64:15)
    at Object.extend.advanceAfterVariableEnd (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:133:18)
    at Object.extend.parseNodes (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1159:22)
    at Object.extend.parseAsRoot (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1177:42)
    at Object.module.exports.parse (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/parser.js:1199:18)
    at Object.module.exports.compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/compiler.js:1118:48)
    at Obj.extend._compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:444:35)
    at Obj.extend.compile (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:433:18)
    at null.<anonymous> (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:378:22)
    at Object.exports.withPrettyErrors (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/lib.js:24:16)
    at Obj.extend.render (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:374:20)
    at Obj.extend.renderString (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/nunjucks/src/environment.js:261:21)
    at /media/nari/工作/blog/blog/node_modules/hexo/lib/extend/tag.js:56:9
    at tryCatcher (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/util.js:26:23)
    at Promise._resolveFromResolver (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:480:31)
    at new Promise (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:70:37)
    at Tag.render (/media/nari/工作/blog/blog/node_modules/hexo/lib/extend/tag.js:55:10)
    at Object.tagFilter [as onRenderEnd] (/media/nari/工作/blog/blog/node_modules/hexo/lib/hexo/post.js:253:16)
    at /media/nari/工作/blog/blog/node_modules/hexo/lib/hexo/render.js:55:19
    at tryCatcher (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/util.js:26:23)
    at Promise._settlePromiseFromHandler (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:507:31)
    at Promise._settlePromiseAt (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:581:18)
    at Promise._settlePromises (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/promise.js:697:14)
    at Async._drainQueue (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:123:16)
    at Async._drainQueues (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:133:10)
    at Immediate.Async.drainQueues [as _onImmediate] (/media/nari/工作/blog/blog/node_modules/hexo/node_modules/bluebird/js/main/async.js:15:14)
    at processImmediate [as _immediateCallback] (timers.js:367:17)
