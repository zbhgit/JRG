题目1： 如何全局安装一个 node 应用?

`npm install -g express`  
-个 是-global的意思，全局安装

题目2： package.json 有什么作用？

这是项目文件介绍，包括项目名称，版本信息，还有开发依赖等信息。

```
  {
     {
  "name": "test",  //名称
  "version": "0.0.1",  //版本
  "description": "This is my first node.js program.",  //描述
  "main": "index.js",  //入口
  "keywords": [  //关键字
                       "node.js",
                       "javascript"
  ],
  "scripts": {  //执行命令行
	  "start": "node index.js"
  },
  "author": "Mike",  //作者
  "license":"MIT",  //认证
  "dependencies": {  //生产环境依赖
	              "express": "latest"
  },
  "devDependencies": {  //开发环境依赖
		   "bower": "~1.2.8",
		   "grunt": "~0.4.1"
  }
}
```

题目3： npm install --save app 与 npm install --save-dev app有什么区别?

> --save 是模块自身依赖的其他模块。需要的依赖模块添加到package.json的dependdencies中

> --save-dev  是开发模块时用到的模块。这些添加package.json的 devDependencies中。



题目4： node_modules的查找路径是怎样的?

> 从当前文件目录开始查找node_modules目录；依次进入父目录，查找父目录下的node_modules目录，依次迭代，直到找到根目录下的node_modules目录。


题目5： npm3与 npm2相比有什么改进？yarn和 npm 相比有什么优势? (选做题目)

题目6： webpack是什么？和其他同类型工具比有什么优势？

webpack是一款模块加载器兼打包工具，他能把各种资源JS/CSS/图片等都作为模块来使用和处理。

* webpack是以CommonJS的形式来书写脚本，但对AMD/CMD的支持很全面，方便旧项目进行代码迁移

* webpack本身只能处理原生JS模块，但是loader转换去可以将各种类型的资源转换成JS模块。这样任何资源都可以成为webpack可以处理的模块。

* 可以将代码拆分成多个区块，每个区块包含一个或多个模块，他们可以按需异步加载，极大减少了页面初次加载时间。

* 有一个只能解析器，几乎可以处理任何第三方库，无论他们的模块形式是CommonJS，AMD还是JS文件。

* 还有一个丰富的插件系统。大多数内容功能都是基于这个插件系统运行的。还可以开发和使用开元的webpack插件，来满足格式是各样的需求。

* 使用异步I/O和多级缓存提高运行效率，使得它能够快速增量编译


题目7：npm script是什么？如何使用？

package.json 文件有一个script字段，可以用于指定脚本命令，供npm直接调用。npm内置了两个简写的命令： npm test 和npm start 其他命令要写成npm run XXX的形式

题目8： 使用 webpack 替换 入门-任务15中模块化使用的 requriejs

题目9：gulp是什么？使用 gulp 实现图片压缩、CSS 压缩合并、JS 压缩合并

```
//安装插件
npm install gulp-imagemin --save-dev //图片压缩
npm install gulp-cssnano --save-dev //css压缩
npm install uglify --save-dev //js压缩
npm install gulp-jshint --save-dev //js规范检查
npm install gulp-concat --save-dev //文件合并
npm install gulp-rename --save-dev //重命名

//gulpfile.js
//引入插件
var gulp = require('gulp'),
    cssnano = require('gulp-cssnano'),
    concat = require('gulp-concat'),
    jshint = require('gulp-jshint'),
    uglify = require('gulp-uglify'),
    imagemin = require('gulp-imagemin'),
    rename = require('gulp-rename'),
 
  //css合并压缩
  gulp.task('build:css', function() {
      gulp.src('./src/css/*.css')
        .pipe(concat('merge.css'))
        .pipe(rename({
            suffix: '.min'
        }))
        .pipe(cssnano())
        .pipe(gulp.dest('dist/css/'));
  })

  //js合并压缩
   gulp.task('build:js', function() {
      gulp.src('src/js/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'))
        .pipe(concat('merge.js'))
        .pipe(rename({
          suffix: '.min'
        }))
        .pipe(uglify())
        .pipe(gulp.dest('dist/js/'));
  })

  //图片压缩
  gulp.task('build:image', function() {
      gulp.src('src/imgs/*')
        .pipe(imagemin())
        .pipe(gulp.dest('dist/imgs/'));
  })

gulp.task('build', ['build:css', 'build:js', 'build:image']);

//命令行
gulp build
```
