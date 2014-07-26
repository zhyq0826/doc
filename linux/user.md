### petta server config

#### 更新镜像源

```
yum update
yum upgrade

```


#### 建立用户 petta

```
useradd -d /home/petta -s /bin/bash -m petta
passwd petta

```


#### 在 root 下面 添加 sudo


```

chmod 777 /etc/sudoers
echo "petta  ALL=(ALL) ALL">>/etc/sudoers
chmod 440 /etc/sudoers

```

#### 安装基础软件

pass
