# linux 命令

##### 删除-r 文件

```sh

  rm ./-r

```
##### 解压 压缩


```sh

  解压：tar xvfz xxx.tar.gz.
  压缩：tar -czf xxx.tar.gz xxxx

```

##### scp 

```sh

  scp -P port xxx.txt  user@192.168.0.3:~/


```


##### 更改目录权限到某个用户

```sh

  sudo chown -R zhyq.zhyq src/
  
```


##### wc 统计字符信息

```sh

  wc 

```

#### install software

```sh

sudo dpkg -i xxxx.deb

```


##### 切到用户目录

```
  
  cd 
 
```


##### telnet 退出

ctrl+], 然后输入q


##### ntpdate 同步服务器时间


```
    sudo apt-get install ntpdate

    sudo ntpdate pool.ntp.org

```


##### du -sh .

统计当前目录大小



##### 查找指定字符在什么文件 什么行





##### 查找指定字符在什么文件 什么行

cat *.py | grep -rn conding
