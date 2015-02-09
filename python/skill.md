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

## instal weasyprint

sudo apt-get install libxml2-dev libxslt1-dev

sudo apt-get install python-dev python-pip python-lxml libcairo2 libpango1.0-0 libgdk-pixbuf2.0-0 libffi-dev shared-mime-info

## install pyquery

apt-get install libxml2-dev libxslt1-dev python-dev

apt-get install python-lxml

pip install pyquery

