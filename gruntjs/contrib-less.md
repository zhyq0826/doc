 使用less 插件
 ----------------

 在 grunt.initConfig 添加 less 配置

```javascript

     grunt.initConfig({
        less: {
          production: {
            options: {
              paths: ["css/less"],
              yuicompress: true
            },
            files: {
              "css/base.css": "css/less/base.less"
            }
          }
        }
    });

    grunt.loadNpmTasks('grunt-contrib-less');
    // 注册任务
     grunt.registerTask('default', ['less'])
```

安装less
-----------------

```sh

    npm install grunt-contrib-less --save-dev 

```
