process.argv 命令行输入值，数组
process.argv[0]和process.argv[1]固定为node和该文件，
参数从process.argv[2]开始

# 读取文件
计算文件有多少行（默认最后一行无换行符'\n')
```
var fs = require('fs')

console.log(fs.readFileSync(process.argv[2], 'utf8').split('\n').length - 1)
//console.log(fs.readFileSync(process.argv[2]).toString().split('\n').length - 1)
```
