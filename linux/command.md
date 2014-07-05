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
>disk usage -> du 
>du -cs 统计目录总大小

统计当前目录大小



##### 查找指定字符在什么文件 什么行

```
grep some dir|filename --color -n

```

##### 查找指定字符在什么文件 什么行

cat *.py | grep -rn coding



##### 查看内存

* top
* top -p        #pid 的内存等


##### lsof

* lsof -i:8300  #端口pid
* lsof -p pid   #pid 文件位置


#####  uname －a   （Linux查看版本当前操作系统内核信息）


##### cat /proc/version （Linux查看当前操作系统版本信息）


##### cat /etc/issue  或cat /etc/redhat-release

##### cat /proc/cpuinfo （Linux查看cpu相关信息，包括型号、主频、内核信息等）

##### getconf LONG_BIT  （Linux查看版本说明当前CPU运行在32bit模式下， 但不代表CPU不支持64bit）

##### lsb_release -a
