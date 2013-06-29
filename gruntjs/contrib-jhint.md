使用jshint 插件
----------------

在 grunt.initConfig 添加 jshint 配置


```javascript

    grunt.initConfig({
      jshint: {
          all: [
              'Gruntfile.js',
              'js/dev/*.js',
              'js/*.js'
          ],
          options: {
            asi: true,
            curly: false,
            eqeqeq: true,
            eqnull: true,
            browser: true,
            globals: {
              jQuery: true
            },
          }
        }
    })

    grunt.loadNpmTasks('grunt-contrib-jshint');
    // 注册任务
    grunt.registerTask('default', ['jshit'])
```


安装jshint
-----------------

```sh

    npm install grunt-contrib-jshint --save-dev 

```


执行语法检查
------------------


```sh

    grunt jshint

```
