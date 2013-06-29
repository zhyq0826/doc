 使用watch 插件
 ----------------

 在 grunt.initConfig 添加 less 配置

```javascript

     grunt.initConfig({
       watch: {
        css: {
          files: 'css/less/*.less',
          tasks: ['less'],
          options: {
            event: ['changed']
          }
        },
        scripts: {
          files: 'js/dev/*.js',
          tasks: ['concat', 'jshint','uglify'],
          options: {
            event: ['changed']
          }
        }
      }
    });

    grunt.loadNpmTasks('grunt-contrib-watch');
    // 注册任务
     grunt.registerTask('default', ['jshit'])
```

安装watch
-----------------

```sh

    npm install grunt-contrib-watch --save-dev 

```

启动watch
-----------------

```sh

    grunt watch
```