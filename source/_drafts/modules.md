
# CommonJS(node.js)

CommonJs 是服务器端模块的规范，Node.js采用了这个规范。

CommonJS 加载模块是同步的，所以只有加载完成才能执行后面的操作。像Node.js主要用于服务器的编程，加载的模块文件一般都已经存在本地硬盘，所以加载起来比较快，不用考虑异步加载的方式，所以CommonJS规范比较适用。但如果是浏览器环境，要从服务器加载模块，这是就必须采用异步模式。所以就有了 AMD  CMD 解决方案。

## express
```
var express = require('express');
var app = express();
app.get('/', function (req, res) {
  var q = req.query.q;
  res.send('Hello World');
});
app.listen(3000, function () {
  console.log('app is listening at port 3000');
});
```

## utility
```
var utility = require('utility');
var md5Value = utility.md5(q);
```

# AMD(require.js)

# CMD(sea.js)
