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


实践
-----------------

1. 运行grunt watch 报 Fatal error: watch ENOSPC 错误

    这是因为内核的监听文件的参数偏小，需要调整

``` 

    sudo sysctl -A | grep watch
```
    
查看内核参数，并找到 fs.inotify.max_user_watches参数

```

    fs.inotify.max_user_watches = 8192
```


修改该参数为一更大的值


 ```
    sudo sysctl -w fs.inotify.max_user_watches=524288
 ```


为了在下次启动系统的时候，该参数还能保持是一个大值，可以将该参数写进内核文件


```

    sudo vi /etc/sysctl.conf 
```

在其末尾添加 fs.inotify.max_user_watches=524288
    
    
    






