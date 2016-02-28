title: gulp用法
tags:
  - javascript
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

(gulp-sequence)[https://github.com/teambition/gulp-sequence]
```
//先并行执行a, b, 再执行c, 再并行执行d, e, 再执行f
gulp.task('sequence-1', gulpSequence(['a', 'b'], 'c', ['d', 'e'], 'f'));
```

(del)[https://github.com/sindresorhus/del]

(gulp-less)[https://github.com/plus3network/gulp-less]
```
gulp.task('less', function() {
    return gulp.src(config.cssPaths)
        .pipe(less({
            paths: [path.join(__dirname, 'src/customize/res')]
        }))
        .pipe(concat('all.css'))
        .pipe(gulp.dest('src/customize/res/css'));
});
```

(gulp-handlebars)[https://github.com/lazd/gulp-handlebars]
```
gulp.task('handlebars', function() {
    return gulp.src(config.templatesSrc)
        .pipe(handlebars({
            handlebars: require('handlebars'),
            compilerOptions: {
                knownHelpers: {
                    image: true,
                    text: true,
                    ifCond: true,
                    times: true
                },
                knownHelpersOnly: true
            }
        }))
        .pipe(wrap('Handlebars.template(<%= contents %>)'))
        .pipe(handlebarsDeclare({
            namespace: 'templates'
        }))
        .pipe(concat('templates.js'))
        .pipe(header(fs.readFileSync('tool/handlebars/prepend.js', 'utf8')))
        .pipe(footer('\n' + fs.readFileSync('tool/handlebars/append.js', 'utf8')))
        .pipe(gulp.dest(config.templatesDest));
});
```

exec
```
gulp.task('svn.update', function(cb) {
    var cwd = process.cwd();
    var cmd_command = 'TortoiseProc.exe /command:update /path:' + cwd + ' /closeonend:1';
    exec(cmd_command, function(err, stdout, stderr) {
        console.log(stdout);
        console.log(stderr);
        cb(err);
    });
});
```