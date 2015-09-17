

1.安装 proxychains 
  
  apt-get install proxychains

2.安装 shadowsocks

  pip install shadowsocks

3.本地创建一个配置文件 shadowsocks.json

```

  {
    "server":"xxx.xxx.xxx.xxx",
    "server_port":443,
    "local_port":1081,
    "password":"xxxxxxx",
    "timeout":600,
    "method":"aes-256-cfb",
    "local_address":"127.0.0.1",
    "workers": 4
  }

```

4.启动本地代理(如果需要后台启动则在最后加上 -d start)，将本地代理启在127.0.0.1:1081上

sslocal -c shadowsocks.json

5.配置本地proxychains，路径为 ~/.proxychains/proxychains.conf

```
  trict_chain
  proxy_dns 
  remote_dns_subnet 224
  tcp_read_time_out 15000
  tcp_connect_time_out 8000
  localnet 127.0.0.0/255.0.0.0
  quiet_mode
  [ProxyList]
  socks5  127.0.0.1 1081
```

6.测试翻墙

proxychains w3m twitter.com
