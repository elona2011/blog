title: gulp用法
tags:
  - js
  - gulp
date: 2015-09-11 20:43:10
categories:
      - 自动化
---


gulp.task(name, fn) - 定义任务，第一个参数是任务名，第二个参数是任务内容。
gulp.task(name [, deps, fn])

gulp.src(path) - 选择文件，传入参数是文件路径。
gulp.dest(path) - 输出文件
gulp.pipe() - 管道，你可以暂时将 pipe 理解为将操作加入执行队列
https://nodejs.org/api/stream.html#stream_readable_pipe_destination_options

```
npm init
npm install gulp-uglify --save-dev
```

# 插件

gulp-uglify 压缩js文件
gulp-minify-css 压缩css文件


chapter4.md gulp.watch('images/*.*)', ['images'])有一点错误

gulp-sass
```
var gulp = require('gulp')
var gutil = require('gulp-util')

gulp.task('default', function () {
    gutil.log('message')
    gutil.log(gutil.colors.red('error'))
    gutil.log(gutil.colors.green('message:') + "some")
})
```