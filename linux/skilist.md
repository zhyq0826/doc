#### 检查不是由你运行的程序

```
ps aux | grep -v `whoami`
ps aux--sort=-%cpu | grep -m 11 -v `whoami`

```


#### 在多个文件中替换掉相同的文本


```

#1
perl -i -pe 's/Windows/Linux/;' test*

#替换当前目录以及下层目录里所有文件中的Windows为Linux
find . -name '*.txt' -print | xargs perl -pi -e's/Windows/Linux/ig' *.txt

#只作用于普通文件上
find -type f -name '*.txt' -print0 | xargs --null perl -pi -e 's/Windows/Linux/'

```

#### 时钟保持准时

```
ntpdate ntp.blueyonder.co.uk

```


#### 找到最大的文件

```
ls -lSrh

#某个类型的最大文件
ls -lSrh *.mp*

#搜寻最大的目录
du -kx | egrep -v "\./.+/" | sort -n

```

#### 端口转发

ssh -NL 27017:localhost:27017 username@host
