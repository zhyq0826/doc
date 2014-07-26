### 在linux下面配置java 环境

1.mkdir /usr/java

2.cd /usr/java

解压jdk包到该目录

3.配置 /etc/profile 文件 添加下面的信息

```

export JAVA_HOME=/usr/java/jdk1.7.0_60

export JAVA_BIN=/usr/java/jdk1.7.0_60/bin

export PATH=$PATH:$JAVA_HOME/bin

export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

export JAVA_HOME JAVA_BIN PATH CLASSPATH

```

4. 使 /etc/profile 生效

```
. /etc/profile

```
