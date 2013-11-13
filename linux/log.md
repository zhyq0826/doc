## linux 日志

##### 密码正确，但无法登录，总是回到登录界面

一般是由于该用户的环境变量发生了变化导致登录出错，可以ctrl+alt+f1进入命令行，    
然后切到当前用户目录之下，查看.profile 文件看有没有问题


##### ubuntu 无法关机

ctrl+alt+f1 进入字符命令模式，输入 sudo aticonfig -acpi-services=off,然后重启
*注意*：推出字符模式ctrl+alt+f7
