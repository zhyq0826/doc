## gruntjs practice

## install

先卸载全局的grunt

```shell

    npm uninstall -g grunt

```

安装命令工具

```shell

    npm install -g grunt-cli

```

然后安装grunt到用户目录

```shell

    npm install grunt

```

建立package.json 文件

```javascript

    {
      "name": "adesk",
      "version": "1.0.0",
      "homepage": "http://www.androidesk.com",
      "author": {
        "zhyq0826": "@三月沙 https://github.com/zhyq0826"
      },
      "description": "adesk app front end js",
      "lib": {
        "jquery": "http://jquery.com",
        "swipejs": "http://swipejs.com/",
        "nodejs": "http://nodejs.org/",
        "gruntks": "http://gruntjs.com/"
      },
      "repository": {
        "type": "git",
        "url": "https://github.com/zhyq0826/blackboard"
      },
      "devDependencies": {
        "grunt": "0.4.1",
        "grunt-contrib-jshint": "0.6.0",
        "grunt-contrib-uglify": "0.2.2",
        "grunt-contrib-concat": "0.3.0",
        "grunt-contrib-qunit": "0.2.2",
        "grunt-contrib-watch": "0.4.4"
      }
    }
```

**注意**:版本号必须是1.x.x格式


安装依赖库,在package.json 目录运行该命令

```shell

    npm install

```


建立Gruntfile.js 

```javascript
    
    module.exports = function(grunt) {
      grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),
        meta: {
          banner: '/*! <%= pkg.name %> - v<%= pkg.version %>' + '<%= grunt.template.today("yyyy-mm-dd") %>\n' + '<%= pkg.homepage %>\n' + '* Copyright (c) <%= grunt.template.today("yyyy") %> androidesk: <%= pkg.author.zhyq0826 %> */\n'
        },
        concat: {
          options: {
            separator: ';'
          },
          dist: {
            // the file to concatenate
            src: [
                '../lib/swipe.js',
                '../lib/jquery.lazyload.js',
                '../dev/global.js',
                '../dev/template.js',
                '../dev/util.js',
                '../dev/analysis.js',
                '../dev/base.js',
            ],
            // the location of the resulting js file
            dest: '../<%= pkg.name %>.js'
          }
        },
        uglify: {
          options: {
            // the banner is inserted at the top of the ouput
            banner: '/*! <%= pkg.name %> - v<%= pkg.version %>' + '<%= grunt.template.today("yyyy-mm-dd") %>\n' + '<%= pkg.homepage %>\n' + '* Copyright (c) <%= grunt.template.today("yyyy") %> androidesk: <%= pkg.author.zhyq0826 %> */\n'
          },
          dist: {
            files: {
              '../<%= pkg.name %>.min.js': ['<%= concat.dist.dest %>']
            }
          }
        },
        qunit: {},
        jshint: {}
      });
    
      grunt.loadNpmTasks('grunt-contrib-uglify');
      grunt.loadNpmTasks('grunt-contrib-jshint');
      grunt.loadNpmTasks('grunt-contrib-qunit');
      grunt.loadNpmTasks('grunt-contrib-watch');
      grunt.loadNpmTasks('grunt-contrib-concat');
    
      //grunt.registerTask('test', ['jshint', 'qunit']);
      //grunt.registerTask('default', ['jshint', 'qunit', 'concat', 'uglify']);
      grunt.registerTask('default', ['concat', 'uglify'])
    }

```


build 构建

```shell

    grunt

```

