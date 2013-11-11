# cssh 


1. install libx11-protocol-perl

2. install tk


*error*:Can't locate Tk.pm

1）sudo apt-get install libx11-dev

2）sudo cpan -i Tk　##会自动地从CPAN上下载安装Tk.pm

3. ./configure
4. make
5  make install

## config .csshrc

clusters = blackbord

blackbord = username@ip1:port  username@ip2:port2

