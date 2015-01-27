## python 日常小技巧

#### python 取得linuxshell命令的输出结果

```

    import subprocess

    r = subprocess.Popen(['wc', '/var/log/adesk.sts'], stdout=subprocess.PIPE)
    std_out = r.communicate()
    print std_out

```


## 注册python 包

1. python setup.py sdist
2. python setup.py register
3. python setup.py sdist upload
