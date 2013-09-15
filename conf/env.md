####以下全部使用sudo apt-get install 来安装

```sh

    git
    vim
    ctags
    python-pip
    redis-server
    memcached
    ssh
    nginx
    g++ 
```

#### install mongodb

```sh

    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
    
    echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list

    sudo apt-get update

    sudo apt-get install mongodb-10gen

```

#### install python lib 以下全部使用  sudo pip install


```sh

    tornado
    python-memcached
    redis
    jinja2
    pymongo


```


#### install google chrome

```sh
    
    sudo apt-get install libxss1
    sudo dpkg -i google-chrome.dep

```


#### install nodejs

必须把nodejs放在用户目录进行编译


```sh
    
    sudo make install
```


```sh


    sudo npm install grunt -g
    sudo npm install grunt-cli -g

```