title: handlebars
<<<<<<< HEAD
date: 2015-11-07 22:13:23
=======
date: 2015-12-07 22:13:23
>>>>>>> bed7b8dc1855a68fd337e1e0733c839809d00117
tags:
---

# templates模板函数
templates是一个函数数组，里面的函数都是使用hbs文件预编译生成的，一个hbs文件代表一段HTML代码，该文件编译生成一个函数，返回值就是HTML模板
```
chanTpl = templates['widget.RecordManage.TaskTpl']();
```

# helper
条件判断helper, 根据handlebars轻逻辑的思想, 是不鼓励这么用
```
var ifConFuncMaps = {
        '==': function(v1, v2, options, context) {
            return (v1 == v2) ? options.fn(context) : options.inverse(context);
        },
        '===': function(v1, v2, options, context) {
            return (v1 === v2) ? options.fn(context) : options.inverse(context);
        },
        '!=': function(v1, v2, options, context) {
            return (v1 != v2) ? options.fn(context) : options.inverse(context);
        },
        '!==': function(v1, v2, options, context) {
            return (v1 !== v2) ? options.fn(context) : options.inverse(context);
        },
        '<': function(v1, v2, options, context) {
            return (v1 < v2) ? options.fn(context) : options.inverse(context);
        },
        '<=': function(v1, v2, options, context) {
            return (v1 <= v2) ? options.fn(context) : options.inverse(context);
        },
        '>': function(v1, v2, options, context) {
            return (v1 > v2) ? options.fn(context) : options.inverse(context);
        },
        '>=': function(v1, v2, options, context) {
            return (v1 >= v2) ? options.fn(context) : options.inverse(context);
        },
        '&&': function(v1, v2, options, context) {
            return (v1 && v2) ? options.fn(context) : options.inverse(context);
        },
        '||': function(v1, v2, options, context) {
            return (v1 || v2) ? options.fn(context) : options.inverse(context);
        },
        'default': function(v1, v2, options, context) {
            return options.inverse(context);
        }
    };
    Handlebars.registerHelper('ifCond', function(v1, operator, v2, options) {
        var fn = ifConFuncMaps[operator] || ifConFuncMaps['default'];
        return fn(v1, v2, options, this);
    });
```

```
{{#ifCond status '===' '2' }}
    <br/><span class="status ui-text-small">Status: Fail</span> 
{{else}}
    {{#ifCond status '===' '1' }}
        <div id="progress_bg">
                <div id="progress" style="width: {{progress}}%;"></div>
        </div>
    {{/ifCond}}
{{/ifCond}}
```

handlebars循环
```
Handlebars.registerHelper('times', function(n, block) {
    var accum = '';
    for(var i = 0; i < n; ++i) {
        accum += block.fn(i);
    }
    return accum;
});
```

```
{{#each actionList as |it k|}}
<li class="ui-button ui-text-medium">{{it.name}}</li>
{{/each}}
```